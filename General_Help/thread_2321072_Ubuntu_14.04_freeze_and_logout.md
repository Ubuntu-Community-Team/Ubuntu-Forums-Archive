---
title: "Ubuntu 14.04 freeze and logout"
date: 2016-04-20
forum: General Help
---

### Post by nenadcvetkovic on 2016-04-20
[COLOR=#111111][FONT=Ubuntu]I've upgraded kernel two days ago following [these instructions]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack").[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have Dell Inspiron 15 3542,[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]uname -a is: Linux Maschina 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Google Chrome Version 50.0.2661.75 (64-bit).
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I was watching video on youtube, switched several times from small video to fullscreen and back, then first Chrome froze and then everything except mouse. Then x restarted and login screen appeared.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is from kern.log
[/FONT][/COLOR]
```
Apr 19 22:20:24 Maschina kernel: [35302.370965] compiz[3859]: segfault at 8 ip 00007f75c8fd950d sp 00007ffe0a13f078 error 4 in libcompiz_core.so.0.9.11.3[7f75c8f75000+ae000]

Apr 19 22:20:48 Maschina kernel: [35326.340722] wallch[3957]: segfault at 7f2f9de49c08 ip 00007f2fad7aa1cd sp 00007ffca86da9b8 error 4 in libQt5Core.so.5.2.1[7f2fad50f000+49a000]

Apr 19 22:20:49 Maschina kernel: [35327.448464] chrome[26687]: segfault at 968 ip 00007fc10b035d0d sp 00007fff98864f50 error 4 in libX11.so.6.3.0[7fc10b00e000+130000]
```

[COLOR=#111111][FONT=Ubuntu]and this is syslog

[/FONT][/COLOR]Apr 19 22:20:24 Maschina kernel: [35302.370965] compiz[3859]: segfault at 8 ip 00007f75c8fd950d sp 00007ffe0a13f078 error 4 in libcompiz_core.so.0.9.11.3[7f75c8f75000+ae000]

```
Apr 19 22:20:48 Maschina gnome-session[3777]: WARNING: Application 'compiz.desktop' killed by signal 11

Apr 19 22:20:48 Maschina gnome-session[3777]: WARNING: App 'compiz.desktop' respawning too quickly

Apr 19 22:20:48 Maschina gnome-session[3777]: CRITICAL: We failed, but the fail whale is dead. Sorry....

Apr 19 22:20:48 Maschina kernel: [35326.340722] wallch[3957]: segfault at 7f2f9de49c08 ip 00007f2fad7aa1cd sp 00007ffca86da9b8 error 4 in libQt5Core.so.5.2.1[7f2fad50f000+49a000]
```

[COLOR=#111111][FONT=Ubuntu]Should I send some bug report? The system didn't offer me to send error report.[/FONT][/COLOR]

---

### Post by mörgæs on 2016-04-21
Thanks for considering this but there is not much interest in 14.04. 
However, if you find a similar bug in 16.04 a report is welcome.

---

### Post by nenadcvetkovic on 2016-04-21
Yeah, in two years, when I plan to update to 16.04

---

