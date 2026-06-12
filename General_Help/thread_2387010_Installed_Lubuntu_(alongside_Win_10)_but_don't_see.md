---
title: "Installed Lubuntu (alongside Win 10) but don't see a prompt to choose OS upon reboot"
date: 2018-03-13
forum: General Help
---

### Post by AshleyQuick on 2018-03-13
Complete newbie here so please keep that in mind (I want to learn the OS).

So I made the installation on a USB stick using Rufus and installed from the live (try now or whatever it's called) desktop. The install seemed to work fine but when I reboot, I don't see any option to choose Lubuntu. Help?

---

### Post by hrsetrdr on 2018-03-13
During installation there should have been a dialogue asking if and/or where you would like [Grub]("https://en.wikipedia.org/wiki/GNU_GRUB")(the Grand Unified Bootloader)  installed.  Did this happen?

Edit:  There may be a more *appropriate* way to fix this,  but there is a grub repair disc called[ Super Grub 2]("https://www.supergrubdisk.org/super-grub2-disk/") that can help you boot to your Ubuntu install.   Once you do boot into Ubuntu you can edit your grub.cfg file.

---

### Post by yancek on 2018-03-13
A likely possibility is that you installed Lubuntu using Legacy/MBT while windows is UEFI.  To get that information, boot your Lubuntu usb and go to the site below and use the 2nd option to download boot repair.  After doing that, run boot repair per instructions and select the option to Create BootInfo Summary and do not try to make any repairs.  You should get a link to the output of boot repair which you can post here and get help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by AshleyQuick on 2018-03-13
I had to change the boot order in my bios. I now get the prompt.

---

