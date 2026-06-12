---
title: "Custom bootable USB"
date: 2016-03-03
forum: General Help
---

### Post by thanatos2 on 2016-03-03
What I want to do is make a [x]ubuntu bootable USB with my choice of software on it configured any way I like it. Trying to just save it all into a presistent file caused problems with running out of space.

The purpose is to have a USB stick for plugging into user machines that can run a variety of cleanup utilities to reset forgotten passwords with chntpw, remove viruses with Comodo and have some pretty background pictures and other UI customization.

Is there a way to repackage an existing installed copy of Xubuntu back into a bootable USB stick?

---

### Post by sudodus on 2016-03-03
It is hard to repackage an existing installed copy of Xubuntu back into a bootable USB stick. I think you have two fair choices.

1. Get a bigger USB drive (USB3 pendrive, or SSD in an enclosure) and keep your installed system there

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

2. Start from the beginning with a persistent live system with a casper-rw ***partition*** instead of a casper-rw file. You can do it with ***mkusb***. Also in this case you might need a bigger USB drive if you want a lot of program packages installed.

See this recent thread

[Create an persistent bootable linux with windows storage access](http://ubuntuforums.org/showthread.php?t=2315930)

---

### Post by thanatos2 on 2016-03-03
Hard as in more steps, or hard as in impossible? I may have to admit defeat and just do it all in casper-rw but I am curious.

---

### Post by sudodus on 2016-03-03
Hard, not impossible.

- Is it an installed system in an internal drive?
- How much space does it occupy?
- Have you installed any proprietary drivers?

- There are some tweaks to reduce wear, which is important when you run an installed system in a USB pendrive:

- the mount option noauto in /etc/fstab
- no journaling in the root file system

You should also avoid using swap (except maybe  for very unusual occations)

-o-

You can create partitions in the pendrive and copy the whole root file system with

```
sudo rsync -Hav source/ target
```

and install the grub bootloader into the pendrive's head

and match the UUID's of /etc/fstab to those of the partitions in the pendrive

and match the UUID's of /boot/grub/grub.cfg to those of the root partition in the pendrive.

I think I have remembered all the steps :-)

---

### Post by Bucky Ball on 2016-03-03
Also, a point worth making, is that are all the machines you are going to be using this stick on booting in either UEFI or BIOS? If they might be booting in one or the other but that is an unknown, that is another thing you are going to need to consider. Will your USB boot in both UEFI mode and BIOS? If not, you are going to need to tweak with the BIOS of each machine, possibly, to get it to boot. Might not be as simple as shoving the stick in and switching the machine on an voila. :|

---

### Post by Bucky Ball on 2016-03-03
Also, a point worth making, is that are all the machines you are going to be using this stick on booting in either UEFI or BIOS? If they might be booting in one or the other but that is an unknown, that is another thing you are going to need to consider. Will your USB boot in both UEFI mode and BIOS? If not, you are going to need to tweak with the BIOS of each machine, possibly, to get it to boot. Might not be as simple as shoving the stick in and switching the machine on an voila. :|

---

### Post by sudodus on 2016-03-04
> **Bucky Ball said:**
> Also, a point worth making, is that are all the machines you are going to be using this stick on booting in either UEFI or BIOS? If they might be booting in one or the other but that is an unknown, that is another thing you are going to need to consider. Will your USB boot in both UEFI mode and BIOS? If not, you are going to need to tweak with the BIOS of each machine, possibly, to get it to boot. Might not be as simple as shoving the stick in and switching the machine on an voila. :|

+1

There are persistent live drives, that boot in UEFI as well as BIOS mode, for example those made with [mkusb](https://help.ubuntu.com/community/mkusb).

---

