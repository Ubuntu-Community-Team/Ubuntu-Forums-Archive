---
title: "grub error 17 help"
date: 2007-09-06
forum: General Help
---

### Post by obsines311 on 2007-09-06
Good day.

I have an "error 17 cannot mount partition" when trying to load ubuntu from grub and an error when I try to load windows xp(I forgot the error message but it's something like cannot recognize partition or filesystem).

I have an IDE hard drive which has xp and fedora core 1 installed. I recently added a brand new SATA hard drive and installed ubuntu, but before installing, I changed the BIOS settings so that the SATA drive would have boot priority since the IDE drive has boot priority. Then during the ubuntu installation, I changed the boot loader install from "hd0" to "hd1"(please correct me because I'm not sure about this). Then after rebooting from the installation, the boot loader shows up and the error occurs after I try to load an OS.

Does anyone know how to get around this? Need help. Thanks.

---

### Post by confused57 on 2007-09-06
> **obsines311 said:**
> Good day.

I have an "error 17 cannot mount partition" when trying to load ubuntu from grub and an error when I try to load windows xp(I forgot the error message but it's something like cannot recognize partition or filesystem).

I have an IDE hard drive which has xp and fedora core 1 installed. I recently added a brand new SATA hard drive and installed ubuntu, but before installing, I changed the BIOS settings so that the SATA drive would have boot priority since the IDE drive has boot priority. Then during the ubuntu installation, I changed the boot loader install from "hd0" to "hd1"(please correct me because I'm not sure about this). Then after rebooting from the installation, the boot loader shows up and the error occurs after I try to load an OS.

Does anyone know how to get around this? Need help. Thanks.

You can reinstall Fedora's grub to your IDE mbr, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
make sure to have your IDE drive set to boot before your SATA drive in bios

If you don't mind setting your bios to boot first to your SATA drive, you could reinstall Ubuntu's grub to the SATA drive's mbr.  This would actually be the easiest way to get all your OS to boot, without having to add an entry to your Fedora grub to boot Ubuntu  if you choose the first option.

---

### Post by obsines311 on 2007-09-07
Thanks for replying.

Actually, my fedora boot loader on hd0, which is my IDE, works fine. The ubuntu boot loader on hd1, SATA, will start but can't mount my partitions. Well, I could just edit the fedora boot loader so I could boot ubuntu, but I want to boot from the SATA, is there any way to get around this. I'll try your suggestion and reinstall my ubuntu boot loader when I get home.

---

### Post by confused57 on 2007-09-07
> **obsines311 said:**
> Thanks for replying.

Actually, my fedora boot loader on hd0, which is my IDE, works fine. The ubuntu boot loader on hd1, SATA, will start but can't mount my partitions. Well, I could just edit the fedora boot loader so I could boot ubuntu, but I want to boot from the SATA, is there any way to get around this. I'll try your suggestion and reinstall my ubuntu boot loader when I get home.

If you're getting a grub boot menu when you boot first to your Ubuntu drive, try highlighting your Ubuntu entry, press "e" to edit, then highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot...this change is temporary, but it can be made permanent in your menu.lst.

In order to boot Windows from your Ubuntu grub menu, you'll need mapping lines:
```
title   Windows XP
rootnoverify  (hd1,0)
makeactive
map  (hd0) (hd1)
map  (hd0) (hd0)
chainloader +1
```

---

### Post by obsines311 on 2007-09-07
It worked! Thanks.

I haven't tried the windows part yet but I could boot my ubuntu and fedora by changing the hd(n) part. I'll try windows next.

Anyway, after trying what you said, I was wondering what happened? I installed the boot loader on hd1 which has ubuntu. So why does ubuntu load when I changed the boot settings to hd0?

---

### Post by confused57 on 2007-09-07
> **obsines311 said:**
> It worked! Thanks.

I haven't tried the windows part yet but I could boot my ubuntu and fedora by changing the hd(n) part. I'll try windows next.

Anyway, after trying what you said, I was wondering what happened? I installed the boot loader on hd1 which has ubuntu. So why does ubuntu load when I changed the boot settings to hd0?

I thought it might work...what happened is that when you set your SATA drive to boot first in bios, grub recognizes your SATA drive as (hd0).  When you selected to install grub's IPL to (hd1), I would think that it was installed to your IDE drive's mbr(which would be recognized as hd1).  So when you boot first to your SATA drive, your drives are recognized as:
(hd0)  SATA drive with Ubuntu
(hd1)  IDE drive with Windows & Fedora

When you boot first to your IDE drive, it's recognized as (hd0) and the SATA drive as (hd1)...confused yet?

If Windows is on the first partition, the entry I gave you should boot Windows.  In order to boot Fedora, you'll need to change the root from (hd0,y) to (hd1,y)...you may already have a correct Window's entry and Fedora's root (hd0,y) in your Ubuntu /boot/grub/menu.lst.

I believe it would have been better to have installed grub's IPL to (hd0) when you installed Ubuntu...(hd0) "should" have been your SATA drive's mbr.

Here's an excellent guide that explains grub:]
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by obsines311 on 2007-09-07
The guide you linked to is very helpful, I guess grub has some issues when using IDE and SATA together.

Thank you very much for helping.:smile:

---

