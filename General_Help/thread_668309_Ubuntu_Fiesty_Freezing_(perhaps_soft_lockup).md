---
title: "Ubuntu Fiesty Freezing (perhaps soft lockup)"
date: 2008-01-15
forum: General Help
---

### Post by redr on 2008-01-15
I am using ubuntu fiesty.

Events happend as follows

I logged on my machine and realised that its damn slow.
It took more than a minute to open shell and give the output of 'top'.
and Xorg was using CPU in the range of 49% to 98%. and it was not momentary usage.
Ctrl+Alt+F1 was also damn slow. I had some other work so I locked the screen. I came after couple of hrs. Now output of top shown most of the CPU time being used by processes watchdog/0, kblocked/0, ksoftirq/0, events/0 (each process' usage in the range of 20% to 90 % or so.)
( I was using gnome. Are kblocked/0, ksoftirq/0 these KDE processes?)
I couldnt do anything more. It was taking a few seconds to display keys being typed. So, finally I gave up and reboot.
Now it appears to be working fine.
I checked /var/log/messages but couldnt make out anything. There was this line in the log file
[softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Is this the problem thing?

What can be the problem?
Thanks in advance.

---

