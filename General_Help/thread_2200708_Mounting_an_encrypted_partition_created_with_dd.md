---
title: "Mounting an encrypted partition created with dd"
date: 2014-01-20
forum: General Help
---

### Post by caitifty on 2014-01-20
Hi all

In preparation for an upgrade on an ultrabook, I created a full disk image from my HDD to an external drive by doing:

sudo dd if=/dev/sda of=/path-to-external-device/oldhd.img

In the past, following a new install I'd just mount the image using

sudo mount -o loop,ro,offset=1048576 /path-to-external-device/oldhd.img /media/temp

and copy everything I wanted across.

The problem this time is on the last install I enabled full disk encryption. So the above mount only mounts the boot sector, not any of the encrypted LVM volumes.

I've googled around and most of what I could find on using cryptsetup to mount a LUKS encrypted partition assumes you're trying to mount an actual partition, not an LVM in an .img, and everything I've tried has failed, usually with the error that the device is not a LUKS device.

sudo fdisk -lu /path-to-external-device/oldhd.img gives:

Device Boot Start End Blocks Id System
/path-to-external-device/oldhd.img1 * 2048 499711 248832 83 Linux
/path-to-external-device/oldhd.img2 501758 250068991 124783617 5 Extended
/path-to-external-device/oldhd.img5 501760 250068991 124783616 83 Linux

Any suggestions on how to mount oldhd.img5 (which is the LVM volume containing everything except /boot) would be much appreciated.

I should add that I'm just making sure I can mount the image *before* blowing away the original hdd, so this question isn't about recovering my files, just about preparing for a reinstall.

Many thanks in advance.

Pete

---

