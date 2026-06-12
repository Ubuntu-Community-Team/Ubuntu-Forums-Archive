---
title: "error: invalid arch-independent ELF magic."
date: 2013-09-15
forum: General Help
---

### Post by AmbiguousOutlier on 2013-09-15
Hello, 

I recently was presented with the above error then with the grub rescue> prompt. I followed these [steps]("http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/") to restore grub. Grub now works, however when I select Ubuntu I get the same error twice and then a "Press any key to continue..." then I return to the Grub menu, same this happens if I try to boot in recovery mode. 

```
Loading Linux 3.5.0-22-generic...
error: invalid arch-independent ELF magic.
Loading initial ramdisk...
error: invalid arch-independent ELF magic.

Press any key to continue...
```

I did get an [output]("http://paste.ubuntu.com/6110065/") from boot-repair;

Any thoughts?

---

### Post by oldfred on 2013-09-15
I thought that error was usually incompatible versions of grub. Or an older boot loader but new install type issue. If you can boot, I am not sure.
They have sped up booting so much that external mounts like your network entries in fstab often are loaded before network or USB are fully loaded and sometimes those give errors. Work around is often a script at end of boot to mount rather than fstab.

---

### Post by AmbiguousOutlier on 2013-09-16
I hope it's not an fstab issue as I this is how I mount my server in all my machines.

However, I managed to re-install Grub2 and now every time I boot I get the Grub prompt NOT a rescue prompt. 

```
set root=(hd0,msdos1)
linux /vmlinuz ro root=/dev/sda1
initrd /initrd.img
boot
```

I run this code and everything is working as it should. Next step is to boot without interaction and then to try and figure out how I broke it. 

Any ideas?

---

### Post by oldfred on 2013-09-16
When you say you reinstalled grub, did you just reinstall the boot loader to the MBR, or a full reinstall of all of grub. I not all of grub I would do that. Boot-Repair can help you chroot into your system and do a full reinstall. You do need Internet working as it has to download new grub and you cannot boot after it deletes old grub.

---

