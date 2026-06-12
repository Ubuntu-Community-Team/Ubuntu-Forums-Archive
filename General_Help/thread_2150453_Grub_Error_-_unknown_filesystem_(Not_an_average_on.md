---
title: "Grub Error - unknown filesystem (Not an average one!)"
date: 2013-06-01
forum: General Help
---

### Post by FizzerUK on 2013-06-01
Hello

Booting my experimental project / study server this morning to a grub error

unknow filesystem...

Now fixed these before but this one has me going into unknown territory as a bit of a newbie.


[LIST]
[*]Booted into livecd.
[*]fdisk -l  /dev/sdh      *Disk to see if the disk is there (/boot is on a removable sd card)*
[/LIST]
[INDENT=2]Disk /dev/sdh: 2013 MB, 2013265920 bytes
49 heads, 51 sectors/track, 1573 cylinders, total 3932160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0217934c
[/INDENT]

[LIST]
[*]mkdir /mnt/tmp-boot
[*]mount /dev/sdh1 /mnt/tmp-boot
[/LIST]
[INDENT=2]NTFS signature is missing. [/INDENT]
[INDENT=2]Failed to mount '/dev/sdh1': Invalid argument[/INDENT]
[INDENT=2]The device '/dev/sdh1' doesn't seem to have a valid NTFS.[/INDENT]
[INDENT=2]Maybe the wrong device is used? Or the whole disk instead of a[/INDENT]
[INDENT=2]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/INDENT]

What is the above error about???  it's always been and ext3 partition.



[LIST]
[*]fsck.ext3 /dev/sdh1
[/LIST]
[INDENT=2]e2fsck 1.42 (29-Nov-2011)[/INDENT]
[INDENT=2]fsck.ext3: Superblock invalid, trying backup blocks...[/INDENT]
[INDENT=2]Superblock has an invalid journal (inode 8).[/INDENT]
[INDENT=2]Clear<y>? no[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]fsck.ext3: Illegal inode number while checking ext3 journal for /dev/sdh1[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]/dev/sdh1: ********** WARNING: Filesystem still has errors **********[/INDENT]


Do I fix ????


[LIST]
[*]dumpe2fs /dev/sdh1
[/LIST]
[INDENT=2]dumpe2fs 1.42 (29-Nov-2011)[/INDENT]
[INDENT=2]dumpe2fs: Bad magic number in super-block while trying to open /dev/sdh1[/INDENT]
[INDENT=2]Couldn't find valid filesystem superblock.[/INDENT]

Also blkid does not show a uuid for the partition ?????

I am confused as to how it's happened.

I suppose I could just create a new boot partition, but as I am still learning I do not know how to create the a good working initrd and I would rather fix it.
To add to complication of a new /boot my system rootfs is on a purely software raid 5 (3 disks using mdadm to manage) this is encrypted in luks format. Already have dropbear configured so I can decrypt over ssh during boot.

Advice guide pointers would be great, the normal grub recreate ones I find don't take into account rootfs on md device encrypted.

Help a wanna be linux system admin (linux+ done - studying LPI and RHCSA now!)

Complete disk anatomy from boot-repair

[http://paste.ubuntu.com/5722359/](http://paste.ubuntu.com/5722359/)

md5, md10, md15 are luks encrypted md devices nothing to do with system, just data partitions.

sda1, sdb1 and sdc1 are encrypted swap.
md127 is the rootfs encrypted md device which contains partions sda2, sdb2 and sdc2
sdh1 WAS the /boot partion on ext3 fs.

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]FizzerUK; Hi !

I do not have any direct help for you in this situation, But maybe a pointer ; This says
[/COLOR]> [COLOR=#000000]Disk /dev/sdh: 2013 MB, 2013265920 bytes[/COLOR]
[COLOR=#000000]49 heads, 51 sectors/track, 1573 cylinders, total 3932160 sectors[/COLOR][COLOR=#000000]
you have a serious problem - as you know ! -only 2013 MB ?? on that disk ---no way !
see if this link might be of some aid:
[/COLOR][http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04](http://askubuntu.com/questions/137655/boot-up-fails-drops-to-initramfs-prompt-12-04)

no help, but any step now is a good step.

---

