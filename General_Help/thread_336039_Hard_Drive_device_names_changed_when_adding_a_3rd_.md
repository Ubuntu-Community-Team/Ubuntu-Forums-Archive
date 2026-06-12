---
title: "Hard Drive device names changed when adding a 3rd drive"
date: 2007-01-11
forum: General Help
---

### Post by badoug on 2007-01-11
I have a Breezy box which I use as  a MythTV box. I recently rearranged data on a different computer to free up a hard drive to add to my myth Volume.

The initial setup in my Myth box is as follows:
hard drive #1 (SATA drive #1) -> sda
                       sda1 -> /
                       sda2 -> swap
                       sda3/4 -> part of LVM
hard drive #2  (SATA drive #2) -> sdb
                       sdb1/2 -> part of LVM



Now the new drive #3... (still has all the old partitions on it from the old machine, including some legacy ntfs partitions, etc from a dual-boot system... the result is that the drive will show up with 7 partitions)

I plug in hard drive #3 into SATA port #3:
When I boot, the post screen identifies the 3 hdds, drive #3 shows up as SATA drive #3.
Then the boot sequence proceeds....

> Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
FATAL: Module unknown not found.
mount: Mounting /dev/sda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

Then it drops me into a BusyBox shell
I do:
ls -1 /dev/sd*
> /dev/sdc2
/dev/sdc1
/dev/sdc
/dev/sdb4
/dev/sdb3
/dev/sdb2
/dev/sdb1
/dev/sdb
/dev/sda7
/dev/sda6
/dev/sda5
/dev/sda4
/dev/sda3
/dev/sda2
/dev/sda1
/dev/sda

so it looks like the mapping it ended up with was
drive3->sda
drive1->sdb
drive2->sdc

If I remove drive3, it returns to:
drive1->sda
drive2->sdb
and boots normally.


I have tried a few different combinations of different orders of connecting the 3 drives but haven't exhaustively tested all 24 possible combinations, no luck finding the magic combination yet.

Does anyone have any idea why this is happening, or know a way to override how the device names get assigned??

thanks...
-doug

---

### Post by chrisccoulson on 2007-01-11
It might be easiest to modify your fstab to reflect the newly assigned device node names. To do this, you should be able to boot in recovery mode by temporarily modifying the kernel boot parameters in Grub. To do this, highlight the recovery mode option in Grub, press [E] and highlight the line which begins 'kernel /boot/vmlinuz....'. Press [E] again to edit this line. There should be an option which looks like

```
root=/dev/sda1
```

Change this to

```
root=/dev/sdb1
```

Press [ENTER] and then [B] to boot. This should allow you to boot in to recovery mode. From here, you can modify your /etc/fstab and /boot/grub/menu.lst to reflect the newly assigned device node names. Then you should be up and running again.

---

