---
title: "alternate install of gutsy and heron freeze at boot -Try the &quot;8139too&quot; driver instead"
date: 2007-12-03
forum: General Help
---

### Post by cannonfodder on 2007-12-03
I have been using Linux (Ubuntu, Zenwalk, Wolvix, Elive) for almost a year now. I'm no Linux guru but thanks to Google and forum posts (and a lot of trial and error) I usually manage to solve most problems I experience.

This time around, my luck has run out. Nothing on Google or in the forums I've consulted has helped. The next logical step was to admit that this was beyond me and to finally post on the Ubuntu forums.

Here is my problem. 

In an effort to setup a minimal Ubuntu-based OpenBox system, I downloaded and burned ubuntu-7.10-alternate-i386.iso.

I was able to do a 'command line install' without any problems but upon rebooting, the OS froze almost right away and hung at the following:
[FONT="Courier New"][B]
This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

Try the "8139too" driver instead[/B][/FONT]

I checked the ISO's integrity and it passed so I re-installed but the problem remained. I have the same issue with a Hardy Heron alternate install.

I am using an HP Pavilion a1218n with a Pentium 4 (2.93GHz), 512MBs of ram, onboard NIC. The computer is a tad under 2 years old. I have NEVER had problems installing Ubuntu (5.10, 6.10, 7.10) via the desktop live CD on this machine. As a matter of fact, I have only had trouble installing the odd distro  or running the odd live CD. That is, my hardware generally works well with Linux.

Despite my searching online, I found little in the way of troubleshooting suggestions. Adding 'acpi=off' to the menu.lst kernel line did not help.

If I understand correctly, the problem is with the NIC driver. Why would this problem surface with an alternate install and not the desktop CDs? How do I go about fixing this?

Please help. Thanx in advance.

---

