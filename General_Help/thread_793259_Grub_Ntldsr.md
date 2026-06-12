---
title: "Grub Ntldsr"
date: 2008-05-13
forum: General Help
---

### Post by pogij on 2008-05-13
Hi

On my computer I have doual boot system (Windows XP and Kubuntu 8.04). When GRUB starts I can run Kubuntu normally, but when I want to start Windows XP I get: NTLDR is missing Press Ctrl+Alt+Del to restart.
The only way to start windows is, to change hdd priority in bios to windows hdd (Windows and Kubuntu are on different hdd), so NTLDR is fine.
I have also checked menu.lst in /boot/grub and everything also looks ok.

What else can be wrong?

---

### Post by pogij on 2008-05-14
Nothing?!

This is my menu.lst:

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=8a752a15-49bd-4704-bc2d-70dbdb8c137a ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=8a752a15-49bd-4704-bc2d-70dbdb8c137a ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Pro
root    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader     +1

Is here anything wrong (although it is more or less the same as it was when i had mandriva installed)?




if I replace:
root    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)

with:
root    (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)

computer just restarts.

---

### Post by meierfra. on 2008-05-14
post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

---

### Post by pogij on 2008-05-14
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a1b4b57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2918     3903795   82  Linux swap / Solaris
/dev/sda3            2919       14593    93779437+  83  Linux

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa529fdaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375       24791   147934552+   f  W95 Ext'd (LBA)
/dev/sdb5            6375       24791   147934521    7  HPFS/NTFS

---

### Post by meierfra. on 2008-05-14
Try

title Microsoft Windows XP Pro
root[COLOR="Red"]noverify [/COLOR](hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by pogij on 2008-05-14
I have already tried this and it didn't work.

---

### Post by meierfra. on 2008-05-15
I really don't see what the problem could be.  Your might try "fixboot" if you have a Windows CD ( but I don't think it will make a difference since you are able to boot  into   XP by booting from the XP drive)

Supergrub is another option. But again I don't really see  what good it would do, but one never knows.

You might also try using a different boot loader: Lilo or  WinGrub or add ubuntu  to boot.ini.  Let me know if you need help trying those out.

---

### Post by pogij on 2008-05-15
I have finally solved the problem!

The problem was:
I have 3 hdds and I can set their priority in bios. Before I had:
1. Linux hdd
2. additional hdd
3. Windows hdd

so when grub called hd1 it apparently expected to find window in additional hdd. My attempt to boot windows on hd2 has failed because I misnamed ntdetect.com file trying to fix this problem by replacing ntldsr and ntdetect.com (I had ntdetect.com.com).

Thanks for the help.

---

### Post by meierfra. on 2008-05-15
> I have 3 hdds 


????????  Your "fdisk -l" only lists 2.

---

