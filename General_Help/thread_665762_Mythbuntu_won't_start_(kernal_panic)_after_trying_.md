---
title: "Mythbuntu won't start (kernal panic) after trying to change wireless settings"
date: 2008-01-12
forum: General Help
---

### Post by GLMontyWV on 2008-01-12
Was attempting to upgrade my wireless network, couldn't get WPA to work so thought I would try WEP.  Desktop froze while making changes in the network manager and now it won't complete startup.  Below are two of the screens when froze.

[IMG]http://www.tacticalgearreview.com/images/badk1.jpg[/IMG]

[IMG]http://www.tacticalgearreview.com/images/badk2.jpg[/IMG]

Looks like the line before the "Kernel Panic" has to do with the WEP so I'm pretty sure that's where my problem is but how do I get back into Mythbunto so I can start figuring out how to fix the problem?

Thanks!

Monty

---

### Post by erpo on 2008-01-13
Try booting in rescue mode. This may require you to hit escape during the grub timer countdown during startup. If you can't get into rescue mode, try booting from a live CD. Once your system has started up, undo your WEP changes and reboot normally.

---

### Post by Ber P on 2008-01-18
Boot in rescue mode. Edit /etc/network/interfaces. Put # in front of every line except the two first lines (something like "auto lo" and "iface lo inet loopback"), save and reboot.

On my machine I went into "kernel panic" even in secure mode, so I used serveral attemps before I was able to finish editing the interfaces-file in time before "kernel panic".

Still needs to figure out how to enable WPA :(

---

