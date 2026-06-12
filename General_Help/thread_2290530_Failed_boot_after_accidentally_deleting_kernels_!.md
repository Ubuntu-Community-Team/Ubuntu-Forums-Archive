---
title: "Failed boot after accidentally deleting kernels !"
date: 2015-08-11
forum: General Help
---

### Post by tarek-taha-6 on 2015-08-11
I am facing the same problem and I can't seem to solve it by following your instructions. I also used bootrepair that generated the following report: [http://paste.ubuntu.com/12055484/](http://paste.ubuntu.com/12055484/) can someone please have a look and let me know how can I fix it ?

---

### Post by tarek-taha-6 on 2015-08-13
Hi, 

  I accidentally deleted kernels while trying to clear more space in the boot partition (i couldn't update new kernels due to lack of space). Now I am unable to boot my Ubuntu Linux (14.04). I tried the boot-repair after booting from a live-usb, but it keeps on failing at the end, and when I reboot, the systems give me the following error :

 ```
 ALERT! /dev/mapper/ubuntu-root does not exist ! Dropin in to shell !
```

This is the log of boot-repair: [http://paste.ubuntu.com/12055484/](http://paste.ubuntu.com/12055484/) 

Please I want to get the sever up and running as soon as possible, any help  ?

---

### Post by montag dp on 2015-08-13
I don't know if this is what you want to hear, but I would probably just reinstall in that case.  First, back up your files to be safe.  Then, when reinstalling, choose "Something else" or whatever the option is called to set up the partitions yourself.  If you have your files mounted to /home on a separate partition from root, you can choose to format the root partition but not /home.  That way you'll just have to reinstall your software and not copy your files back over.  If you don't have your /home on a separate partition, this might be a good opportunity to do that.  It's very useful to have it set up that way if you need to reinstall.

PS: This probably isn't the right forum, since this is a support request, so you might request the mods to move the thread so that it will get more views.

---

### Post by coffeecat on 2015-08-13
*Thread moved to **General Help**.*

And added the post that was posted to another old thread.

---

### Post by oldfred on 2015-08-14
You have UEFI hardware, but tried to install in BIOS boot mode.
With UEFI you have to have an ESP - efi system partition which is FAT32 (vfat) with the boot flag.
With BIOS boot on a gpt partitioned drive you must have a 1 or 2MB unformatted partition with the bios_grub flag.
I often suggest both, so you can install either way.

Boot-Repair can convert a BIOS install to UEFI or vice-versa if you have correct partitions ESP or bios_grub for grub to correctly install. Use advanced mode and choose full uninstall/reinstall. Make sure you have /boot & LVM mounted, but Boot-Repair should do that.

---

