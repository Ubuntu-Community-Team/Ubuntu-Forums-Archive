---
title: "Failure to Suspend (Blinking Sleep Light)"
date: 2015-06-18
forum: General Help
---

### Post by RadiantPhoenix on 2015-06-18
What I did:

[list]
[*] Reinstalled Xubuntu 14.04 from the ISO, used it for a while, installing some stuff, and updating
[*] Used "suspend" from the "action buttons" widget
[/list]

What I expected:

[list]
[*] Computer to suspend, and be able to resume afterwards, so I don't need to shut down everything every time.
[/list]

What I got:

[list]
[*] Computer half-suspends and can't wake up, so I have to use the power button to power it off and on
[/list]

Symptoms:

[list]
[*] Black screen
[*] Blinking sleep light
[/list]

Note: I think it worked properly via lid-closure back when I didn't have /etc/systemd.logind.conf saying "HandleLidSwitch=ignore", which I did because that stopped a black screen after resume, which had to be fixed by:

[list]
[*] Super+T (terminal)
[*] ALT+TAB (bring terminal to front. Why wasn't it there already?)
[*] "xrandr --auto" (somethingsomething reconfigure the display)
[/list]


Computer: Thinkpad W500

```
uname -srvmpio
Linux 3.19.0-21-generic #21~14.04.1-Ubuntu SMP Sun Jun 14 18:45:42 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

