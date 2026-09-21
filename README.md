# SS-moniter.-An-alternative

What it does:

Client mod sends report → server plugin receives on ssmonitor:report channel
Plugin decompresses JSON, extracts external_scan block
If any CRITICAL/HIGH/MEDIUM findings → sends Discord embed
Discord embed looks like:

xXHackerXx — CRITICAL
━━━━━━━━━━━━━━━━━━━━
Player: xXHackerXx (a1b2c3d4)
Server: My Server
Critical: 2  High: 5  Medium: 3

INJECTORS RUNNING
• xenos64.exe

CHEAT MODS DETECTED
• offline-client-bootstrap-patched.jar:OfflinePreLaunch.class

TOP FINDINGS
`CRITICAL` injector: xenos64.exe — Known injector running
`HIGH` prefetch: PRESTIGE — PRESTIGE_LAUNCHER.EXE-ABC123.pf
`HIGH` hook: excessive_modules — javaw.exe loaded 45 modules
Setup:

Build: cd SSMonitor-Server && gradle build
Put jar in server plugins/ folder
Edit plugins/SSMonitor/config.yml — paste your Discord webhook URL
/ssmonitor test to verify
Commands:

/ssmonitor reload — reload config
/ssmonitor test — send test embed
/ssmonitor status — check webhook status
The cooldown prevents spam — one report per player per 60 seconds by default.


**forked from ocean and echo**

From Ocean (C++ anti-cheat analysis):

Severity-based findings (CRITICAL/HIGH/MEDIUM/LOW) — mirrors Ocean's rule engine with Severity enum
Structured Finding record — mirrors Ocean's RuleResult pattern
Anti-debug detection: JDWP, suspend=n — mirrors Ocean's AntiDebug class checks
Hook detection via module count analysis — mirrors Ocean's check_hooks and INT3 detection
From Echo (Go screenshare tool):

Prefetch scanning — mirrors Echo's GetPrefetch / win_prefetch.go
AMCache scanning — mirrors Echo's GetAmcache / amcache.GetAmcache package
BAM (Background Activity Moderator) — mirrors Echo's GetBam / win_bam.go
ShimCache scanning — mirrors Echo's ObtainShimCache / win_shimcache.go
Window title scanning — mirrors Echo's GetWindowSizes / GetAllWindows
Service enumeration — mirrors Echo's GetServiceInfo / GetServiceProcessData
Module count hook detection — mirrors Echo's CheckHooks / win_hooks.go
Expanded cheat mod scanning — mirrors Echo's GetMods / minecraft.GetMods
Structured findings JSON with cat/name/sev/detail — mirrors Echo's CustomDetectionIndication
