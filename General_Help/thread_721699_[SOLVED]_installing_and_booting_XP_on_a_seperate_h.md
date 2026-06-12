---
title: "[SOLVED] installing and booting XP on a seperate hard drive?"
date: 2008-03-11
forum: General Help
---

### Post by AvengingAngel718 on 2008-03-11
I recently picked up a copy of the PC version of elder scrolls 4 oblivion. I havent had any luck installing it with cedega, so i'm planning on installing xp (bleah) on a seperate hard drive that i got from the computer science department at my university for free (cant beat free!). I was hoping someone could help me out with this, because i'd like to not mess anything up like i did when i tried repartitioning my drive to install xp (reinstalled twice and wasted about 2 weeks :( )

My main drive which uses ubuntu is SATA but the one i plan on using for windows is IDE, so i need to know if i need to set the jumpers to slave, master, or cable select. Right now they're set to master, and with the hard drive hooked up, my computer wouldnt even boot lol

Also, is there any chance of messing up grub if i install it on a seperate drive? Also, how would i go about adding XP to grub after installing?

---

### Post by Rocket2DMn on 2008-03-11
The jumpers on the drive depend on how you plug it into your IDE port - it won't share a cable with your SATA drive since it's a different style cable.  Cable select is probably best, otherwise you would probably want master (unless you plug it into slave on a CD drive IDE cable or something).

Windows will overwrite the bootloader when you install it, but you can get GRUB back, see here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by AvengingAngel718 on 2008-03-11
i figured it would mess grub up.....stupid windows.

anyway, i'll try it out tonight and post here if anything goes wrong

wish me luck

---

