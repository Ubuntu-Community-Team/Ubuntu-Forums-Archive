---
title: "grub error 17"
date: 2008-01-16
forum: General Help
---

### Post by dydo on 2008-01-16
I have dual boot settings and they worked fine. Windows XP and Ubuntu dual booted fine. I used windows xp to delete 2 logical partitions that I made but had nothing on it. They were under an extended partition. Now when I boot grub, I get error 17 and can't boot into any OS.

---

### Post by c0met on 2008-01-16
Before getting into the code and stuff, it might be easiest if you downloaded a bootable ISO for the program called SuperGrub. Burn this to a CD and then boot your system from this CD. It will give you options for...

    * making your win(dows) drive bootable
    * making your linux drive bootable
    * setting your system up for a dual boot

If you have Windows on one drive and Linux on the other, then you simply need to choose the dual boot option and it will setup the Grub menu for you so that you can select which operating system to boot into.

This is a great little program to have on hand. It's got me out of a few tight spots. You can download the ISO from...

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

===========================

**[COLOR="Red"]IF SUPERGRUB DOESN'T WORK[/COLOR]**, then boot up from the Ubuntu Live CD and go the the URL

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")

About 1/3 of the way down the web-page is a heading "Reinstall GRUB to the MBR". Follow the instructions from there onwards and you will be able to restore you system.

---

### Post by dydo on 2008-01-16
Thank you it worked, now I can use Ubuntu and XP again.

---

### Post by c0met on 2008-01-16
Excellent! I have had GRUB error 17 a few times. SuperGRUB doesn't always work but most of the time is does. It's a handy little program to keep with your bag of tricks.

---

