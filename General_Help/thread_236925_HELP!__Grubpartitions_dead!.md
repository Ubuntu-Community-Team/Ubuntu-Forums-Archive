---
title: "HELP!  Grub/partitions dead!"
date: 2006-08-15
forum: General Help
---

### Post by termite on 2006-08-15
I resized an ntfs partition using a partition magic boot cd and rebooted.  When GRUB started, I got an error 17.  I got a GRUB cd, attempted to fix things using ```
root (hd0,5)
setup (hd0)
```

this allowed to get as far as the GRUB menu.  When I select any of the options, it dies with ```
Error 17: Cannot mount selected partition
```

I tried editing the boot commands manually.  Originally, I had: ```
root (hd0,6)
kernel /boot/vmlinuz-2.6.17.5 root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.17.5
savedefault
boot
```

I changed the first line to ```
root (hd0,5)
```
as (hd0,6) is my swap, not my root.  Did the same for the second line (also tried leaving it as is, no diff).

Now the system dies on the 'Mounting root filesystem' part.  I get: ```
Mounting /dev/hda7 on /root failed: No such device
```
etc, and it drops to BusyBox

If I do ```
fstype /dev/hda7
``` it gives ```
FSTYPE=unknown
```
ditto for /dev/hda5.

However, ```
fstype /dev/hda6
``` gives ```
FSTYPE=ext3
```
ditto for /dev/hda8

I can mount /dev/hda6 and /dev/hda8 and can see that those are my old partitions.

So somewhere along the line, hda5 (my old root partition) became hda6 and hda7 (my old home partition) became hda8.  But as far as GRUB can tell, the change hasn't taken place.  I know the latter part since when I drop to the GRUB command line and type ```
root (hd0, +tab
``` it gives me partitions 5 and 7 as ext2fs, partition type 0x83.

Any ideas?  I would really like my system to work...

---

### Post by termite on 2006-08-15
ok, so I managed to boot by changing the root option on the second line to hda6 as well as the first line to the same.

I had to change fstab to mount /dev/hda8 rather than hda9 on /home, and to comment out the rest of fstab.  Working on it.

However, at boot, if I drop to the GRUB commandline, it still gives me (hd0,5) as my ext3.

I can patch this by fixing fstab, but would really like to do this at the partition level.

Help welcome.

---

### Post by skale on 2006-08-15
If you can boot, I don't see what the problem is. However, the issue is probably either in fstab or menu.lst. You've played with both, just make sure all the partitions are right.

---

