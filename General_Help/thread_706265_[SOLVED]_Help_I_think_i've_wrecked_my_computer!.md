---
title: "[SOLVED] Help I think i've wrecked my computer!"
date: 2008-02-24
forum: General Help
---

### Post by timswait on 2008-02-24
I've just installed Ubuntu and Windows as dual boot on a new computer. I've been using the computer for a week on both systems and all was going well, had got all my software installed, got all my files where I wanted them and copied off my old system. I've got two hard drives, an IDE one for films and music and a SATA one with one linux partition, one windows partition, a partition for my documents and a inux swap partition. I needed to erase and format an old hard drive before I sold it so I turned my computer off, plugged it in and just to avoid confusion I unplugged my other two hard drives. Then I booted Ubuntu using a CD, ran partition editor to format the old hard drive and shut the computer back down. I then unplugged the old hard drive, plugged back in my two regular hard drives and tried to boot it. ( I did have leave the power connectors on the other two drives while I was formatting the old drive, could that cause a problem?) But now it comes up BOOT DISC ERROR and won't boot at all, not even to the screen which let's me choose operating system. I'm now running Ubuntu from CD with my two regular hard drives connected. I can access both of them and all my documents are still there, one of the sectors is flagged as boot, so why won't it boot? What can I do to rescue it. I've spent literally hours getting it all the way I want it and realy don't want to have to re-install two operating systems all over again. PLEASE HELP!!!

---

### Post by danwood76 on 2008-02-24
The boot order has been messed up I expect.
You should be able to change the boot priority in the BIOS, you need to select the hard disk with your operating systems on it.

---

### Post by gambothell on 2008-02-24
1. Boot off of your live CD
2. Open Terminal
3. Type: sudo grup
4. Type: find /boot/grub/stage1
5: Type: root (hd?.?) where ? is the drive.partition you got as an answer in #4. Example: on my computer it is hd0.2 - first drive 3rd partition
6: Type: setup(hd0)
7: Type: quit  (to exit grub)
8: Reboot


Good luck:)

---

### Post by gambothell on 2008-02-24
It is too early today and I cannot type. In step 2, should be: sudo grub - sorry

---

### Post by danwood76 on 2008-02-24
Its just that the BIOS is trying to boot off the other hard disk instead of the one with grub  on it.
This can be changed in the BIOS no need to re install grub.

---

### Post by timswait on 2008-02-24
Thank you for your replies, but I got there first. Danwood was right, it was that the hard drives were the wrong order in the BIOS so it was looking on my Films and Music hard drive for Boot data, set that right and it's working again. Thank you again guys I was realy panicing for a bit there!

---

