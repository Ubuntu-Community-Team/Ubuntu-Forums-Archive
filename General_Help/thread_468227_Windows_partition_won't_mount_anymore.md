---
title: "Windows partition won't mount anymore"
date: 2007-06-08
forum: General Help
---

### Post by maharbA on 2007-06-08
A few weeks ago I set up a Dell Inspiron 8600 to dual-boot with XP. All was working well until a a few days ago: with the latest update, the Windows partition no longer mounts automatically (I think the last update had a kernel update because I had to reboot, and there were two new options in my Grub list with slightly newer kernel versions).

The Windows partition was sda1, which I had changed in fstab to mount as WinDrive. That entry in fstab is still there, but the partition still won't mount. Gparted still lists the partition, so I know it's still there, but it calls it hda1 (I can't remember what it was before). Also, when I opened Gparted, the drive mounted, but just as "disk" (incidentally, the custom icon I had assigned the drive is still applied -- just not the name) and it still won't mount automatically.

Any light that can be shed on this mystery will be GREATLY appreciated.

---

### Post by merlinus on 2007-06-08
If you post fstab, perhaps someone can help.

Also

sudo fdisk -l

and 

blkid

-merlin

---

### Post by eapache on 2007-06-08
The older kernel had a bug that caused ide drives to be recognized as sata (sd* instead of hd*). The new kernel fixed this. In fstab, replace sd** with hd**. If it lists a big long string of hex instead, replace that with hd**. Remember to back up fstab first.

---

### Post by maharbA on 2007-06-08
BINGO!
Thankyousomuch , eapache
you're a genius.

---

