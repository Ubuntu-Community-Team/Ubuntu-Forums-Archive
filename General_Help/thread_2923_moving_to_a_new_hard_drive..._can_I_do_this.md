---
title: "moving to a new hard drive... can I do this?"
date: 2004-11-01
forum: General Help
---

### Post by negativ on 2004-11-01
Can I use something like Ghost or Drive Image to simply copy my existing Ubuntu installation to a larger hd and have it work, or is there some problem I don't know about (i.e. partitions tied to hd geometry somehow?

---

### Post by diebels on 2004-11-02
dd works like ghost, but I think you need drives of same size or you will get some wasted space. Try partition new drive, make filesystem,  mount new drives root partition, copy files, chroot to new drive, install grub.

Get root shell ```
sudo -s
```
Partition with fdisk (cfdisk or qtparted for nicer UI) ```
fdisk /dev/xxx
``` xxx=hdb or something, make a big root and a swap at least.
Make filesystem:```
mke2fs -j /dev/xxx1
``` if you want ext3.
Make swap:```
mkswap /dev/xxx2
```
Make dir to mount new drive on:```
mkdir /media/newdrive
```
Mount it:```
mount /dev/xxx1 /media/newdrive
```
Copy files:```
cp -a / /media/newdrive
```
Chroot to newdrive:```
chroot /media/newdrive /bin/bash
```
Install grub:```
grub-install /dev/xxx
```
Check /etc/fstab.
Reeboot.
Swap harddisks in BIOS or physically.
Done.

---

### Post by negativ on 2004-11-10
I finally tried this last night, and it didn't work.  I ran cp -av (wanted to see verbose) and it seems to be hung up at

`/proc/kmsg' -> `/media/newdrive/proc/kmsg'

5 hours later, it's still doing that.


I also noticed:

cp: reading `/proc/sysrq-trigger': Invalid argument

Should I care?

---

### Post by rune on 2004-11-10
I've done it easily with a debian system.

You should NOT copy /proc and /dev. There are quite a few tutorials out there about how to do it. I remember it somthing like this:

copy everything but /proc and /dev
make new /proc  and /dev
remeber to edit either grub or lilo and /etc/fstab afterwards.

also there are some caveats regarding symlinks.

/Rune

---

### Post by rupert on 2004-11-10
i tried the same some weeks ago,
run also into trouble, because of the udev in ubuntu.
I finaly installed ubuntu new, took me some hours less than my tries before.
I used tar to copy the files, i copies the links etc. correctly.

In the mailing list I had a discussion about it.
```
Cleanup your 'new' partitions and then mount them under your 'existing'
system.


>> mkdir /new
>> mount -t ext3 /dev/hdb1 /new


Repeat if you have multiple partitions and mount them under /new

Copy your installation over


>> cd /
>> tar cpf - / | tar xpvf - -C /new


Edit /new/etc/fstab and /new/grub/menu.lst as appropriate

Chroot into your new install and install grub


>> chroot /new

(chroot)> grub
(grub)> root (hdx,y) <- with your new root partition
(grub)> setup (hdx) <- where you want to install the boot loader

Exit the chroot and reboot

```
here after i run into trouble.
[code]
> can´t get it  to boot,
>> it boots the kernel and than it tells me it cant find /dev/console and 
>> pivot_root


Whoops ... I ran into this just recently when restoring a system that
had migrated to udev (as ubunutu).  I copied the contents of /.dev into
/dev and then re-booted.  


>> but the files are on the hd.
>> I think the drives are mapped different ,
>> my new root is sdb4, root=/dev/sdb4 is set.
>> I copied the file with -l option,
>> but it didnt copied the /dev files, so i copied them again including the 
>> /proc files.


The /dev files are re-created by a dynamic filesystem created after
boot, but you need a /dev filesystem and some devices early in the boot.
They seemed to exist in the /.dev directory.

---

