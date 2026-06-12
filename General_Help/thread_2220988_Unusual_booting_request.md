---
title: "Unusual booting request"
date: 2014-04-30
forum: General Help
---

### Post by Milambar on 2014-04-30
OK, this is probably going to confuse some people, but I will try and explain my situation.

I have a 4 year old laptop with a failing hard disk. I cannot afford to replace the hard disk yet. The failure symptom is unusual, nothing is able to boot from the hard disk directly.

However once booted by other means, the disk is readable, writeable and mountable. It has Ubuntu 14.04 installed on it, it just can't boot.

It can however boot from a "live CD" without issue.

My request, is a command or sequence of commands so that I can boot the laptop with the CD, then mount the hard disk, then change the "operation" of the OS from the CD to the hard disk, because naturally hard disk access is much faster than a CD.

So

Boot from CD
mount /dev/sda1
somemagichere that makes the OS run off the hard disk instead of the cd.

It will only be a temporary solution for a month maybe two until I can afford to replace the hard drive unit, and I'm not worried about data loss should the hard drive suddenly fail totally so don't worry about that.

Many thanks

---

### Post by dragonfly41 on 2014-04-30
Have you tried running boot-repair?

---

### Post by zemega on 2014-04-30
Are you saying the hard disk MBR is damaged? Quite tricky. And the solution you're asking is impossible I think. When you boot from live CD that means its the Ubuntu inside the CD, not the laptop.

There is an option that I can describe. Install Ubuntu (any, even minimal install is okay) into a USB drive (I hope you have spare around), install, not creating a live usb. Once there is a Ubuntu inside the pendrive, you can set you BIOS to boot into the pendrive. So automatically you will from now boot into the USB drive. After that you can update and modify the grub inside the USB Drive Ubuntu and make it boot into the laptop Ubuntu. It should be way better than live CD, as long as it is a good USB drive. The actual speed of the USB Drive will determine the speed of Ubuntu. I think its better to use Xubuntu in this case. Also, 4 years old laptop, I hope it comes with USB 2.0 or 3.0, give up on this method if its only USB 1.0.

---

### Post by dragonfly41 on 2014-04-30
Since I'm right now trying to swap out a damaged disk from an old Sony VAIO tower for a family member I can suggest one or two options ..

If you do have damaged MBR or partition read here ..

[http://www.geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/](http://www.geekyprojects.com/storage/how-to-repair-a-damaged-partition-table-or-mbr/)

But since you can get into your Ubuntu (albeit in a roundabout way) perhaps this article might help to bootup another iso from a partition in your internal hard drive ..

[http://www.dangibbs.co.uk/journal/how-to-boot-live-cd-iso-with-grub2-ubuntu](http://www.dangibbs.co.uk/journal/how-to-boot-live-cd-iso-with-grub2-ubuntu)

(I just found this today by coincidence since I'm trying to make my replacement drive bootable before I install it back into the old tower).

---

### Post by Bashing-om on 2014-04-30
Milambar; Hi ! 

Are you certain the hard drive is failing ? Have you run the hardware disk diagnostics ? If it is but the MBR files that have become corrupted, these may be replaced.

To directly respond to your query, however, see how a full 'change root' from the liveDVD into the install works for you:
When completed you will be running from the installed harddrive system.

## copy and paste these commands below :
## Change /dev/sdxY to actual partition value eg. /dev/sda5 - Where 'root' was installed to.
##This assumes a standard install and that there are no separate partitions.
```

sudo mount /dev/sdxY /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
##May not be needed in later releases, try without these next 3 commands -> If networking is needed: Open a new terminal and ->
sudo cp /mnt/etc/hosts /mnt/etc/hosts.old
sudo cp /etc/hosts /mnt/etc/hosts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt/ /bin/bash

To shut down the system you MUST back out of the chroot, else file system corruption **will result** !
# =============
# Remove CHROOT
# =============

## copy and paste these commands below.
exit ##returns you to the liveDVD environment. 
to restore the old hosts file if networking were enabled ->
cp /etc/hosts.old /etc/hosts
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

*side note: /etc/resolv.conf is nowadays managed by resolvconf, it'll automatically be generated when using NetworkManager and can safely be removed using rm /etc/resolv.conf


[INDENT]my little bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kurja on 2014-04-30
Sounds like an mbr issue (although you didn't give much detail on exactly with what symptoms boot fails), not necessarily caused by the disk being at the end of it's life.

When booted from live cd, check for the hard disk's smart data for any warnings. Then, try running fsck, this alone might repair your issue.

---

### Post by Milambar on 2014-05-01
> **Bashing-om said:**
> Milambar; Hi ! 

Are you certain the hard drive is failing ? Have you run the hardware disk diagnostics ? If it is but the MBR files that have become corrupted, these may be replaced.

To directly respond to your query, however, see how a full 'change root' from the liveDVD into the install works for you:
When completed you will be running from the installed harddrive system.

## copy and paste these commands below :
## Change /dev/sdxY to actual partition value eg. /dev/sda5 - Where 'root' was installed to.
##This assumes a standard install and that there are no separate partitions.
```

sudo mount /dev/sdxY /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
##May not be needed in later releases, try without these next 3 commands -> If networking is needed: Open a new terminal and ->
sudo cp /mnt/etc/hosts /mnt/etc/hosts.old
sudo cp /etc/hosts /mnt/etc/hosts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

sudo chroot /mnt/ /bin/bash

To shut down the system you MUST back out of the chroot, else file system corruption **will result** !
# =============
# Remove CHROOT
# =============

## copy and paste these commands below.
exit ##returns you to the liveDVD environment. 
to restore the old hosts file if networking were enabled ->
cp /etc/hosts.old /etc/hosts
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

*side note: /etc/resolv.conf is nowadays managed by resolvconf, it'll automatically be generated when using NetworkManager and can safely be removed using rm /etc/resolv.conf


[INDENT]my little bit
[INDENT][INDENT][INDENT]to try and help
[/INDENT][/INDENT][/INDENT][/INDENT]

Thank you much. Exactly what I was looking for.

Theres no point in trying to fix the disk, not when its SMART data gives a reallocated sector count of 15. Meaning the physical disk is dying. Its a Seagate model with a reallocated sector count threshold of 36 (the lower the number, the worse condition the drive is in), so its going to fail totally, probably within weeks.

---

