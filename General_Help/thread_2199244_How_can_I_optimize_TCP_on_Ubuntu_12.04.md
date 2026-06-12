---
title: "How can I optimize TCP on Ubuntu 12.04?"
date: 2014-01-12
forum: General Help
---

### Post by deaton25 on 2014-01-12
[COLOR=#000000] I work off of Chrome on Ubuntu. The TCP Optimizer people claim that my Rwin values are way to low[/COLOR]
[COLOR=#000000]I know that TCP Optimizer is designed for Windows. But there is a Wine based version available.[/COLOR]
[COLOR=#000000]Is this worth checking out? Failing that, what codes should I punch in at the console to crank up my Rwin?[/COLOR]
[COLOR=#000000]I'm told that Linux now auto-adjusts these things. But if that's the case, then why are my Rwin scores so low?![/COLOR]
[COLOR=#000000]These are my results:[/COLOR]
[COLOR=#000000]« SpeedGuide.net TCP Analyzer Results » [/COLOR]
[COLOR=#000000]Tested on: 2014.01.08 05:41 [/COLOR]
[COLOR=#000000]IP address: 24.235.xxx.xx [/COLOR]
[COLOR=#000000]Client OS/browser: Linux (Chrome 31.0.1650.63) [/COLOR]

[COLOR=#000000]TCP options string: 020405b40402080a0010ab980000000001030307 [/COLOR]
[COLOR=#000000]MSS: 1460 [/COLOR]
[COLOR=#000000]MTU: 1500 [/COLOR]
[COLOR=#000000]TCP Window: 14720 (NOT multiple of MSS) [/COLOR]
[COLOR=#000000]RWIN Scaling: 7 bits (2^7=128) [/COLOR]
[COLOR=#000000]Unscaled RWIN : 115 [/COLOR]
[COLOR=#000000]Recommended RWINs: 64240, 128480, 256960, 513920, 1027840 [/COLOR]
[COLOR=#000000]BDP limit (200ms): 589kbps (74KBytes/s)[/COLOR]
[COLOR=#000000]BDP limit (500ms): 236kbps (29KBytes/s) [/COLOR]
[COLOR=#000000]MTU Discovery: ON [/COLOR]
[COLOR=#000000]TTL: 49 [/COLOR]
[COLOR=#000000]Timestamps: ON [/COLOR]
[COLOR=#000000]SACKs: ON [/COLOR]
[COLOR=#000000]IP ToS: 00000000 (0)
[/COLOR]
[COLOR=#000000]Can you help ?[/COLOR]

---

### Post by sandyd on 2014-01-13
Ubuntu doesnt have RWin, but see [http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346) for equivilent

---

