---
title: "Cloning with rsync"
date: 2017-05-10
forum: General Help
---

### Post by vcrpcant on 2017-05-10
I'm trying to clone my system using rsync and following bits and pieces of instructions I've found on the internet.

But, I need a litle help to finish this. 

So far, I've done this about 20 times, but I can't boot from my new disk.
I've made multiple atempts.
I've even used an installation DVD using the repair option.
And also dd'ed the MBR.
All ended up with the cursor blinking before the grub menu appears.

So, this is my original set up, in which I have 3 partitions:
sda1 - boot, ext2
sda2 - luks - swap
sda3 - luks - root, ext4

In my new hard drive, I've made only 2 partitions (didn't made swap)
sdb1 - boot, ext2
sdb2 - luks - root, ext4

then, I've mounted sdb1 and /dev/mapper/sdb2_crypt and copied them using rsync like this:
rsync -aAXv /boot/* /media/computer/NEW-BOOT
rsync -aAXv --exclude-from=/ignore_list /* /media/computer/NEW-ROOT

afterwards, using blkid to find the new UUID, I've updated UUID in crypttab, fstab and /boot/grub/grub.cfg in the new hard drive.
umounted 

then, set bios_grub flag on boot partition of new hard drive:
parted /dev/sdb
set 1 bios_grub on
p [print partition table to check bios_grub flag is on]

cryptsetup luksOpen /dev/sdb2 sdb2_crypt
mkdir /mnt/temp

mount /dev/mapper/sdb2_crypt /mnt/temp
mount /dev/sdb1 /mnt/temp/boot

mount --bind /dev /mnt/temp/dev
mount --bind /dev/pts /mnt/temp/dev/pts
mount --bind /proc /mnt/temp/proc
mount --bind /sys /mnt/temp/sys

chroot /mnt/temp

update-initramfs -u -k all

grub-install /dev/sdb
update-grub

exit [exit chroot]
umount /mnt/temp/dev/pts
umount /mnt/temp/dev
umount /mnt/temp/proc
umount /mnt/temp/sys
umount /mnt/temp/boot
umount /mnt/temp

Then, I've shutdown, removed the original hard drive and tried booting with the new hard drive, but no luck.

Does anybody know how to successfully solve this?

---

### Post by leunam12 on 2017-05-10
I think the right tool is dd instead of rsync. But it is easier and faster to use clonezilla.

---

### Post by #&amp;thj^% on 2017-05-10
> **leunam12 said:**
> I think _**the right tool is dd instead of rsync**_. But it is easier and faster to use clonezilla.

+100 I Love dd bit for bit...Clonezilla has a easier interface to understand.

---

### Post by vcrpcant on 2017-05-10
I agree clonezilla (that uses dd) is an easy way to do it. It's what I've been using.
But, it has some disadvantadges, like the need to have a same size or bigger hard drive and being slower (sometimes, hours).

Using rsync, I can do this in less than 5 minutes. That's right, 5 minutes.

So, that would be really sweet to make this work.

---

### Post by oldfred on 2017-05-10
Do not know about LVM & encryption.

But a boot partition with LVM is not the same as a bios_grub partition.
The bios_grub partition is required if booting in BIOS boot mode from a gpt partitioned drive.
Most gpt partitioned drives are UEFI and then have to have the ESP - efi system partition (FAT32).

The bios_grub is 1 or 2 MB unformatted with bios_grub flag. When you install grub to gpt protective MBR, the core.img that with MBR partitioning that is normally in the sectors after the MBR goes into the bios_grub partition.
Grub does not use boot flag, that is Windows type boot loaders, syslinux & lilo that do use boot flag. But a few BIOS do need a boot flag just to start boot process, so we normally suggest to have one on a primary partition if BIOS booting. If UEFI, the boot flag is only on the ESP/efi.

You probably have to reinstall grub to get all the bits & pieces in correct place.
And without swap, your fstab may not let you boot. It used to be that you got a warning message but system booted. But newer systems (systemd?) just seem to fail if any entry in fstab is missing.

---

### Post by #&amp;thj^% on 2017-05-10
> **vcrpcant said:**
> 
Using rsync, I can do this in less than 5 minutes. That's right, 5 minutes.

So, that would be really sweet to make this work.
That dose perk my interest's in rsync largely.:)
But where I fall short, at least in helping here is:
```
sdb2_crypt /
```
I just don't do it is all choice/preference.
But I do have an interest in this thread now...and best of luck.:D
Edit: ninj'ed by oldfred...and right on time.;)

---

### Post by vcrpcant on 2017-05-10
I've finally made it happen!

Thank you oldfred!
Your reply made me think and find the error: 
I used GTP while partitioning the new disk because I use GPT to large 3TB data disks.
But I've should have used MS-DOS because that is my original disk partition table.

So, my new disk partition table will also be MS-DOS.

I've done this using LUKS encryption, but it's almost the same without it.
Only boot partition in not encrypted.

So, this time I did it this way:

in my original set up I have 3 partitions:
sda1 - boot, ext2
sda2 - luks - swap
sda3 - luks - root, ext4

in my new hard drive, this time I've made also 3 partitions:
sdb1 - boot, ext4, 200MB
sdb2 - luks - swap ext4, 8GB
sdb3 - luks - root ext4, 20 GB

using parted:
parted /dev/sdx (obviously, replace sdx with sda, sdb, etc)
(parted) mklabel msdos
q [quit]

then, I made the 3 partitions using fdisk and set the bootable flag "on" on the boot partition
I used fdisk, but obviously parted could also be used to make the partitions

afterwards, format boot partition:
mkfs.ext4 /dev/sdx1
this time I've used ext4 in the new boot partition, although the original boot partition is ext2

format swap partition:
cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdx2
cryptsetup luksOpen /dev/sdx2 SWAP_crypt
mkswap /dev/mapper/SWAP_crypt

format root partition:
cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 /dev/sdx3
cryptsetup luksOpen /dev/sdx3 ROOT_crypt
mkfs.ext4 /dev/mapper/ROOT_crypt

make temporary mount folder, mounting the new root partition and copying preserving permissions, ACL's, etc:
mkdir /mnt/temp
mount /dev/mapper/ROOT_crypt /mnt/temp
rsync -aAX --exclude-from=/ignore_list /* /mnt/temp

note:
my goal here is not to save data directories, but only to make a clone or replica of my operative system
because data directories are easily saved with simpler backups plans
so, I've excluded all my data folders using the rsync ignore list
in the ignore list, I've excluded the CONTENTS of the /boot folder because the boot partition is only mounted a step later
I've also excluded the CONTENTS of the other directories populated at boot like /dev, /proc, /sys, etc
but, the folders themselves are still copied, just not their contents
credits and more info:
[https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)
I've just replaced --exclude={"..."} with a file ignore list because I like it more using a file

mount the new boot partition and copy the original /boot contents to it:
mount /dev/sdx1 /mnt/temp/boot
rsync -aAXv /boot/* /mnt/temp/boot

now, let's find the UUID of the 3 partitions created in the new disk using the blkid command:
blkid

in the new disk, make a backup of the crypttab and fstab:
cp /mnt/temp/etc/crypttab /mnt/temp/etc/crypttab_bk
cp /mnt/temp/etc/fstab /mnt/temp/etc/fstab_bk

and them change their UUID's with mousepad or any other text editor:
mousepad /mnt/temp/etc/crypttab /mnt/temp/etc/fstab

now, let's move on to chrooting:
mount --bind /dev /mnt/temp/dev
mount --bind /dev/pts /mnt/temp/dev/pts
mount --bind /proc /mnt/temp/proc
mount --bind /sys /mnt/temp/sys

chroot /mnt/temp
update-initramfs -u -k all [I'm not sure this step is required, but I've done it anyway]
grub-install /dev/sdx
update-grub
exit [exit chroot]

umount /mnt/temp/dev/pts
umount /mnt/temp/dev
umount /mnt/temp/proc
umount /mnt/temp/sys
umount /mnt/temp/boot
umount /mnt/temp

and finally I booted into my new hard drive successfully!

now, I'm able to make a normal working replica of my system in another hard drive, 
even if it's an old one with only a few GB's since the system folders are usually around 5GB

and the best part is all this can be achieved under 5 minutes or less,
when done right at the first time at the terminal

another option is to burn the backup of the system folders to a dual-layer DVD
but this time do INCLUDE the folder /boot
and use that backup when needed to recreate the backed up system

better still, using this approach and hard links to make daily differential backups, 
it's easily possible to recreate the operative system of a particular past day

enjoy!

---

### Post by #&amp;thj^% on 2017-05-10
Cool.... Good Work!
And Thanks for sharing with details.:)

---

