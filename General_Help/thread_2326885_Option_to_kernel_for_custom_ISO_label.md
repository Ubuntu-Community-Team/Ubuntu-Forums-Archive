---
title: "Option to kernel for custom ISO label?"
date: 2016-06-05
forum: General Help
---

### Post by Andy_Crowd on 2016-06-05
Hi!  I am making a custom USB with many Linux on it, and Ubuntu asks for Label of disk, it can't find it. I am making bootable USB with Archiso and many Linux distros on it for showing different types of Linux as an alternative to Windows and Mac.  I am testing to start it with those options but it fails:   ```
    kernel /casper/vmlinuz  initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper   ignore_uuid -- 
```

---

### Post by yancek on 2016-06-05
You will need to post more details on what you have done.  The entry you have posted is to boot a single instance of some Ubuntu installation using syslinux/isolinux.  If you simply want a number of systems on a flash drive you could install Grub2 to the MBR of the drive and then put the various Ubuntu or other system's iso files on the flash drive and boot the iso file directly.  This works with almost all Ubuntu derivatives as well as a number of other Linux distributions and there are a number of sites with detailed instructions on how to do this.

I've done similar flash drives and never been asked for a label so not sure what that's about.

---

### Post by oldfred on 2016-06-06
While it mentions hard drive this applies to just about any drive.
Issues usually are getting drive & path correct.
Boot drive is always hd0 in BIOS/grub, only if ISO on another drive would you need different drive.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by Andy_Crowd on 2016-06-11
Thank you! It was also missed the folder "/.disk" in source.

---

