---
title: "Grub no longer boots XP"
date: 2008-03-31
forum: General Help
---

### Post by John Costella on 2008-03-31
Hi folks,

I'm having trouble getting grub to boot into XP. I select it from the grub menu and the machine just reboots back into the grub menu.

I may have broken it my going into XP and renaming the C volume. It used to have a space in the volume name, which was causing me headaches, so I booted into XP and changed it something saner. Ubuntu remounted the renamed volume no problems, and with some encouragement it mounted it with the new name in /media too.

I thought all was well until later today I tried to reboot into XP to do some banking (the ANZ bank site crashes Firefox no matter what I do), and I discovered it was dead.

The Windows volume is still there and mounted under ubuntu; I just can't boot it.

I tried digesting the grub documentation but I'm lost in the details.

Can anyone offer any advice?

Many thanks
John Costella

---

### Post by housam on 2008-03-31
[[COLOR="Red"]_recover grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub")

or use the [[COLOR="Red"]_super grub _[/COLOR]]("http://supergrub.forjamari.linex.org/")tool

---

### Post by John Costella on 2008-03-31
Thanks housam,

I was looking at those options but I was hesitant because grub seemed to be working fine, as did ubuntu and even the partition. It was only XP itself that was upset.

Before reinstalling grub I took one last snoop around the root directory of the Windows volume (from within ubuntu). When I turned on hidden files I found a trash can, and inside I was amazed to find NTDETECT.COM. I'd never come across this file before, but it sounded like one of the boot files for Windows. 

So I put it in the root directory, and, lo and behold, Windows is back.

I don't know how on earth I managed to delete this file -- I assume I did something stupid at some point -- but I'm glad to have it all back.

Thanks again for your help,
John

---

