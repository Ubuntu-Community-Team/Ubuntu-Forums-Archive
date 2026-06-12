---
title: "Gutsy random freezes completely: SMP bug???"
date: 2007-11-01
forum: General Help
---

### Post by Felipaus on 2007-11-01
I'm running xubuntu on an old MSI dual Pentium III mb. Everything OK with Feisty 7.04.
After the Gutsy 7.10 upgrade (compeleted in a clean simple way) the machine totally freezes (no mouse, no keyboard, no apparent network activity: only haer reset works) at totally random times. At first I supposed a problem related to graphic driver (ATI open one: I'm not a gamer and I've got an old 64Mb ATI radeon 9000). 
Until I tested other kernels: random freezes with 2.6.22.14 generic and with 2.6.22.14 server too: both with smp dual pentium support needed for my old dual slot1 mb.
But with 2.6.22 i386 **NO MORE FREEZES!!**! :):):) but only one CPU recognized (linux-i386 isn't SMP aware) :(
So I think Gutsy kernel 2.6.22 generic SMP support needs fixes since Feisty generic one was OK

---

### Post by haldean on 2007-11-01
I have the same problem - random freezing at normal load levels, and only a hard reset turns the thing off. I only have one CPU though, and I *am* using the 2.6.22.14-i386 kernel, not the generic one. If anyone knows any fixes for this, I'd be really grateful!

---

### Post by squideekie on 2008-02-04
I can confirm that the generic and server kernel for 2.6.22-14 both have smp issues/bugs. My freezes aren't random, mostly when playing video/audio files or browsing flash sites. I added noapci nosmp to my grub menu.lst. It also works with i386 kernel so it's definitely an smp issue.

Let me know if you have an update.

---

