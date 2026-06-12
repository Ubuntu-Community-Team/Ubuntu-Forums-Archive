---
title: "How do I install XP on second Hard Drive?"
date: 2008-06-18
forum: General Help
---

### Post by redonwhite on 2008-06-18
Hello,

I just got my second hard drive in the mail today.  My Goal is to have XP on my new (Hard drive 2) for games, and to keep Ubuntu on my original Hard drive (Hard drive 1).


I connected Hard Drive 2 up to the motherboard and power supply.  From there I've just been guessing how to install windows with trial and error.  So far nothing is working.  Ive tried booting from the CD but it instantly goes to Ubuntu.  And i cant seem to find any way into my BIOs.  

Thanks for any help you can give me.

EDIT:  Would it be as simple as unplugging my ubuntu Hard drive and Installing XP on the new drive and then plugging back in the Ubuntu Drive?  Would it give me the option of witch Hard Drive i wanted to use if i did this?

---

### Post by cnekmp on 2008-06-18
The first way to install Windows XP on second drive is to change Boot Priority of devices in BIOS (you should try harder to find it). But after installation of Windows it'll write down his MBR, and will not see you Ubuntu. So, you'll need to boot up from Ubuntu CD and repair GRUB (it's not so hard as it seems)

The second way is to unplug your hard drive where is Ubuntu installed and install Windows on other drive. After that you'll need add some commands to GRUB loader from Ubuntu, that it recognized Windows OS from the boot menu.

---

### Post by Rocket2DMn on 2008-06-18
I would leave both drives plugged in and boot from the Windows CD by changing your BIOS order so that the CD boots above the hard drive (see post 2).  Then have XP install to the second hard drive - you can tell the difference by looking at size, file system, and number of partitions already on the drives.

And yes, Windows will take over the MBR so you need to restore GRUB to it.  See - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Also, the Super Grub Disk can be used for that - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Then you will have you dual boot.

---

### Post by forestpixie on 2008-06-18
Once you've installed it you will need to reinstall grub - this page should help, it also gives info on supergrub which is good as well

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by redonwhite on 2008-06-20
> **forestpixie said:**
> Once you've installed it you will need to reinstall grub - this page should help, it also gives info on supergrub which is good as well

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I got windows installed on the second hard drive.  Now for that link.  Which one should i use you think?  I read through everything but it all kind of confused me a little.  Thanks for your help.

---

### Post by Rocket2DMn on 2008-06-21
Sorry for the delayed response.  You will want to either use the Ubuntu LiveCD or the Super Grub Disk (you don't need to read much of that, you can just get the disk and run it).
You do not need to preserve the windows bootloader.

---

