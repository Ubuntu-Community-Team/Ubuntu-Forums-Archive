---
title: "Problem with booting ubuntu"
date: 2013-01-21
forum: General Help
---

### Post by AwAk3e on 2013-01-21
This morning I woke up to this error - "Reboot and Select proper boot device" on my ubuntu installation. 

I've checked to see that the BIOS detects the hard drive and it does, I also went through the installation process again and it detected the hard drive there, however when I use fdisk and having booted from a bootable disc, it can't find the drive. 

Does anyone know how to resolve this?
Thanks in advance.

*EDIT: Using lshw -class disk I am able to see the drive with a logical name of /dev/sdb, however if I try to mount it I can the error: "can't find /dev/sdb in /etc/fstab or /etc/mtab".
I figured out you need a mount point, so after trying sudo mount /dev/sdb /mnt I get: "mount: dev/sdb: can't read superblock". Does this mean my hard drive has become corrupt?

---

### Post by dino99 on 2013-01-21
which ubuntu is used ? how is formatting made ?

---

### Post by AwAk3e on 2013-01-21
> **dino99 said:**
> which ubuntu is used ? how is formatting made ?

I'm using Ubuntu Server Edition 12.10

I'm sorry I don't know what you mean by how the formatting is made? From what I recall I just went through the standard install procedure and I have 1 hard drive inside the computer.

---

### Post by dino99 on 2013-01-21
formatting: i was asking about ext2/3/4/else and/or raid

as you says having 1 hdd, your bootloader might be installed on /dev/sda, not sdb. Have you set special "server" partitions like /boot, /var, ... or is it a standard installation (/, /home, /swap ) only ?

output of "sudo blkid " please

to install grub on sda, boot on a livecd/usb and run:

sudo grub-install /dev/sda

---

### Post by AwAk3e on 2013-01-21
> **dino99 said:**
> formatting: i was asking about ext2/3/4/else and/or raid

as you says having 1 hdd, your bootloader might be installed on /dev/sda, not sdb. Have you set special "server" partitions like /boot, /var, ... or is it a standard installation (/, /home, /swap ) only ?

output of "sudo blkid " please

to install grub on sda, boot on a livecd/usb and run:

sudo grub-install /dev/sda

The output of "sudo blkid" is:
/dev/loop0: TYPE="squashfs
/dev/sda1: UUID="9016-6367" TYPE="vfat"

Maybe an important bit of information is that I'm booting to a live ubuntu using a USB drive.
If I recall correctly it was a standard install with /home/ etc
*EDIT: Sorry it has server partitions like /boot /var /etc etc

Should I run "sudo grub-install /dev/sda"? Or should I use /dev/sdb as that is what says when I use lshw -class disk and I get logical_name /dev/sdb under the HD

Thank you for your help!

---

### Post by oldfred on 2013-01-21
If it cannot read super block it has some file corruption. Generally you need to run fsck on that partition or maybe all the ext partitions.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by AwAk3e on 2013-01-21
> **oldfred said:**
> If it cannot read super block it has some file corruption. Generally you need to run fsck on that partition or maybe all the ext partitions.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Trying to run the first command but altered for my drive: 
"sudo e2fsck -C0 -p -f -v /dev/sdb"
I get the error:
"e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?"

I get the same error when running the second command.

---

### Post by AwAk3e on 2013-01-21
A bit more research and I found this:
[http://ubuntuforums.org/archive/index.php/t-1245536.html](http://ubuntuforums.org/archive/index.php/t-1245536.html)

However before following it what exactly does this do:
sudo mke2fs -n /dev/sdb1

The data on my drive is important and I want wiping it to be a last resort.

Will running that command risk me losing my data?

Thank you, AwAk3e

---

### Post by oldfred on 2013-01-21
My post was just an example using sdb1, you have to use your partitions. You probably do not have an sdb1 so that is the error you got.

If you do not know which are ext partitions run this:

sudo fdisk -lu

---

### Post by AwAk3e on 2013-01-21
> **oldfred said:**
> My post was just an example using sdb1, you have to use your partitions. You probably do not have an sdb1 so that is the error you got.

If you do not know which are ext partitions run this:

sudo fdisk -lu

When running fdisk -lu I only see the USB drive that I'm using to use the Live version of Ubuntu.
The output is pretty much:
 Device   Boot Start   End    Blocks  Id   System
/dev/sda1   *   63   7962623 3981280+  b W95 FAT32

---

### Post by oldfred on 2013-01-21
Does BIOS show hard drive? If not check connections for both power & signal.

---

### Post by AwAk3e on 2013-01-21
> **oldfred said:**
> Does BIOS show hard drive? If not check connections for both power & signal.

The BIOS does indeed detect the hard drive.

---

### Post by oldfred on 2013-01-21
From Disk Utility is drive shown. Click on it and what does smartdata say about it. It can run lots of tests, but all I really know is green is good and anything else is an issue.

---

