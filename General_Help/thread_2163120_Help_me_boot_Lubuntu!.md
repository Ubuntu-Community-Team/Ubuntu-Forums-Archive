---
title: "Help me boot Lubuntu!"
date: 2013-07-17
forum: General Help
---

### Post by King Dude on 2013-07-17
I've been up all night trying to install Lubuntu on this old, crappy computer that cannot boot from USB. What I need to do is create a GRUB bootloader that I can simply plug into the darn thing, and then be able to boot Lubuntu through my USB flashdrive. Before anyone asks, I HAVE NO CDs, NO DVDs, -NOTHING! Just a 1GB flashdrive, a floppy, and two PCs with Windows.

Please give me specific directions.

Thanks.

---

### Post by Elfy on 2013-07-17
*Thread moved to **General Help**.*

---

### Post by sudodus on 2013-07-17
1. To give specific directions, it helps if you give us specific data of your computer: at least CPU and RAM size. I assume, that you need a 32-bit version, maybe non-pae. So try with Lubuntu 12.04. You can get better suggestions when we know about the CPU and RAM (and it help if you specify the graphics chip/card too).

2. Have you checked in your BIOS menus, how to change the boot order, and what options there might be to boot from USB? Sometimes the USB drive can be recognized as a hard disk drive (and should be given priority in the list of hard disk drives: You need to boot with the USB drive connected)

3. If it won't boot from USB and you have no CD/DVD, you might put Plop onto a floppy disk, and boot from the floppy. Plop can install USB drivers, so that some (but not all) old PCs will continue and boot from USB. See this link

[http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

4. See this link for ways to make good boot USB drives (also from Windows)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

5. If still no go, remove the hard disk drive from the Lubuntu candidate PC, connect it to one of the Windows PCs and boot from the USB install drive and install Lubuntu into that (temporarily connected) drive. Remember to install the bootloader into head of that drive (and not into the Windows drive). If you install no proprietary drivers, the installation will be portable, that is, it will work in most computers (*edit*: including your old PC).

---

### Post by King Dude on 2013-07-17
I'll try putting Plop on a floppy and see how that works out. Thanks.

---

