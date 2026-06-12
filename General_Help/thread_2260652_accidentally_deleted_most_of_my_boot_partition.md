---
title: "accidentally deleted most of my /boot partition"
date: 2015-01-13
forum: General Help
---

### Post by jdix123 on 2015-01-13
I was getting all sorts of memory low messages about my /boot partition in edubuntu 14.04, so I decided to delete some duplicates/obsolete archives in the /boot partition, but it looks like I deleted all of them instead. Oops.

lost and found folder is untouched, as is the grub folder

Other files still in the partition include memtest86+.bin, memtest86+.elf, and memtest86+_multiboot.bin

What files do I need to download, and how do I get them back on the /boot partition? I have a live CD I'm booted from currently (Ubuntu 14.04, not edubuntu like my system), but don't want to do a complete reinstall if I don't need to.

---

### Post by sandyd on 2015-01-13
The /boot folder contains:
[LIST]
[*]Kernels (new/old) - linux-image-generic
[*]memtest
[*]grub
[/LIST]

The EFI partition is also mounted there if you are using a GPT partition.

If you do a chroot into your system, and reinstall the packages, it should be fine.

---

### Post by jdix123 on 2015-01-13
I've never used chroot before.

I'm looking at the man page right now. Basically I run

```

sudo chroot /media/ubuntu apt-get install linux-image-generic(whatever the current version is)

```

except that apt-get isn't a recognized command, or I've got the syntax wrong

---

### Post by sandyd on 2015-01-13
Can you post the output of
```

sudo fdisk -l
```

I will see how it it supposed to be mounted and chrooted and provide you with a command to reinstall the packages.

---

### Post by jdix123 on 2015-01-13
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x235091ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/edubuntu--vg-root: 495.8 GB, 495804481536 bytes
255 heads, 63 sectors/track, 60278 cylinders, total 968368128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/edubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/edubuntu--vg-swap_1: 3992 MB, 3992977408 bytes
255 heads, 63 sectors/track, 485 cylinders, total 7798784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/edubuntu--vg-swap_1 doesn't contain a valid partition table


```

---

### Post by sandyd on 2015-01-13
Ok, lets mount the root and the boot partition into place....

Lets make sure needed partitions are already unmounted...
```

sudo umount /dev/mapper/edubuntu--vg-root
sudo umount /dev/sda1
```

Lets mount the partitions...
```

sudo mount /dev/mapper/edubuntu--vg-root /mnt
sudo mount /dev/sda1 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

```

Chroot into the ubuntu installation
```

sudo chroot /mnt /bin/bash
```

See if the above is successful and we shall continue on

---

### Post by jdix123 on 2015-01-13
Almost made it! Everything looks good til the last.
```

ubuntu@ubuntu:~$ sudo umount /dev/mapper/edubuntu--vg-root
ubuntu@ubuntu:~$ sudo umount /dev/sda1
ubuntu@ubuntu:~$ sudo mount /dev/mapper/edubuntu--vg-rot /mnt
mount: special device /dev/mapper/edubuntu--vg-rot does not exist
ubuntu@ubuntu:~$ sudo mount /dev/mapper/edubuntu--vg-root /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo chroot /mnt /bin/bash
sudo: unable to resolve host ubuntu
chroot: failed to run command &#8216;/bin/bash&#8217;: No such file or directory

```

---

### Post by sandyd on 2015-01-13
Sorry about this, seems I didn't manage to make a correction before you ran the command.

Just run
```

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
```

Can you also post the output of```

ls -l /mnt
ls -l /mnt/bin/bash
ls -l /mnt/bin/sh
mount -l

```

Thanks!

---

### Post by jdix123 on 2015-01-13
```

ubuntu@ubuntu:~$ ls -l /mnt
total 103
drwxr-xr-x   2 root root  4096 Jan  9 17:13 bin
drwxr-xr-x   4 root root  3072 Jan 13 19:21 boot
drwxrwxr-x   2 root root  4096 Jun  3  2014 cdrom
drwxr-xr-x  18 root root  4320 Jan 13 19:37 dev
drwxr-xr-x 157 root root 12288 Jan 13 19:22 etc
drwxr-xr-x   3 root root  4096 Jun  3  2014 home
lrwxrwxrwx   1 root root    33 Jan 13 19:13 initrd.img -> boot/initrd.img-3.13.0-44-generic
lrwxrwxrwx   1 root root    33 Dec 16 22:05 initrd.img.old -> boot/initrd.img-3.13.0-43-generic
drwxr-xr-x  25 root root  4096 Dec 11 19:21 lib
drwxr-xr-x   2 root root  4096 Dec 11 19:21 lib32
drwxr-xr-x   2 root root  4096 Dec 11 19:21 lib64
drwx------   2 root root 16384 Jun  3  2014 lost+found
drwxr-xr-x   3 root root  4096 Jun  3  2014 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   5 root root  4096 Sep 24 17:14 opt
dr-xr-xr-x 266 root root     0 Jan 13 19:26 proc
drwx------   4 root root  4096 Jun  3  2014 root
drwxr-xr-x  14 root root  4096 Jun  3  2014 run
drwxr-xr-x   2 root root 12288 Dec 11 19:23 sbin
drwxr-xr-x   2 root root  4096 Apr 17  2014 srv
dr-xr-xr-x  13 root root     0 Jan 13 19:26 sys
drwxrwxrwt  11 root root  4096 Jan 13 19:22 tmp
drwxr-xr-x  16 root root  4096 Jul 16 20:49 usr
drwxr-xr-x  15 root root  4096 Jun  4  2014 var
lrwxrwxrwx   1 root root    30 Jan 13 19:13 vmlinuz -> boot/vmlinuz-3.13.0-44-generic
lrwxrwxrwx   1 root root    30 Dec 16 22:05 vmlinuz.old -> boot/vmlinuz-3.13.0-43-generic
ubuntu@ubuntu:~$ ls -l /mnt/bin/bash
-rwxr-xr-x 1 root root 1021112 Oct  7 19:22 /mnt/bin/bash
ubuntu@ubuntu:~$ ls -l /mnt/bin/sh
lrwxrwxrwx 1 root root 4 Jun  3  2014 /mnt/bin/sh -> dash
ubuntu@ubuntu:~$ mount -l
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime) [Ubuntu 14.04 LTS amd64]
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/mapper/edubuntu--vg-root on /mnt type ext4 (rw)
/dev/sda1 on /mnt/boot type ext2 (rw)
/dev on /mnt/dev type none (rw,bind)
/proc on /mnt/proc type none (rw,bind)
/sys on /mnt/sys type none (rw,bind)
ubuntu@ubuntu:~$ 

```

---

### Post by sandyd on 2015-01-13
Try running
```

sudo chroot /mnt
```, does that return any errors?

---

### Post by jdix123 on 2015-01-13
Nope. Got the magic pound sign.

```

ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# 

```

---

### Post by sandyd on 2015-01-13
Excellent.

Lets try reinstalling the linux kernel and grub files
```

apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub

```

See if anything is missing
```

ls -l /boot
ls -l /boot/grub
```

---

### Post by jdix123 on 2015-01-13
Uh oh, got an error here

```

root@ubuntu:/# apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc mdadm fdutils linux-lts-utopic-tools
  linux-headers-3.16.0-29-generic
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub linux-image-3.16.0-29-generic
0 upgraded, 2 newly installed, 2 reinstalled, 3 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 18.7 MB of archives.
After this operation, 45.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.16.0-29-generic amd64 3.16.0-29.39~14.04.1 [16.1 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main grub amd64 0.97-29ubuntu66 [913 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main grub-common amd64 2.02~beta2-9ubuntu1 [1,680 kB]
Fetched 18.7 MB in 42s (435 kB/s)                                              
E: Internal Error, No file name for linux-image-generic:amd64
root@ubuntu:/# ls -l /boot
total 538
drwxr-xr-x 5 root root   1024 Dec 16 16:05 grub
drwx------ 2 root root  12288 Jun  3  2014 lost+found
-rw-r--r-- 1 root root 176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root 178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root 178680 Mar 12  2014 memtest86+_multiboot.bin
root@ubuntu:/# ls -l /boot/grub
total 2390
drwxr-xr-x 2 root root    1024 Jun  3  2014 fonts
-rw-r--r-- 1 root root     699 Apr 16  2014 gfxblacklist.txt
-r--r--r-- 1 root root   17374 Dec 16 16:05 grub.cfg
-rw-rw-r-- 1 root root    1024 Jan  6 11:34 grubenv
drwxr-xr-x 2 root root    8192 Aug  5 09:18 i386-pc
drwxr-xr-x 2 root root    1024 Aug  5 09:18 locale
-rw-r--r-- 1 root root 2405285 Aug  5 09:18 unicode.pf2
root@ubuntu:/# 


```

---

### Post by sandyd on 2015-01-13
Try the command again - removed unnecessary package.

---

### Post by jdix123 on 2015-01-13
looks like it mostly ran, with some errors.

```

root@ubuntu:/# apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc mdadm fdutils linux-lts-utopic-tools
  linux-headers-3.16.0-29-generic
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc grub2-common
The following NEW packages will be installed:
  grub linux-image-3.16.0-29-generic
0 upgraded, 2 newly installed, 1 reinstalled, 3 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/18.7 MB of archives.
After this operation, 45.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
(Reading database ... 507364 files and directories currently installed.)
Removing grub-pc (2.02~beta2-9ubuntu1) ...
Removing grub2-common (2.02~beta2-9ubuntu1) ...
Removing grub-gfxpayload-lists (0.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Selecting previously unselected package linux-image-3.16.0-29-generic.
(Reading database ... 507326 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-29-generic_3.16.0-29.39~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-29-generic (3.16.0-29.39~14.04.1) ...
Selecting previously unselected package grub.
Preparing to unpack .../grub_0.97-29ubuntu66_amd64.deb ...
Unpacking grub (0.97-29ubuntu66) ...
Preparing to unpack .../grub-common_2.02~beta2-9ubuntu1_amd64.deb ...
Unpacking grub-common (2.02~beta2-9ubuntu1) over (2.02~beta2-9ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Internal Error: Could not find image (/boot/vmlinuz-3.13.0-44-generic)
dpkg: error processing package linux-image-3.13.0-44-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-44-generic:
 linux-image-extra-3.13.0-44-generic depends on linux-image-3.13.0-44-generic; however:
  Package linux-image-3.13.0-44-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-44-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-44-generic; however:
  Package linux-image-3.13.0-44-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-44-generic; however:
  Package linux-image-extra-3.13.0-44-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.44.51); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.16.0-29-generic (3.16.0-29.39~14.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-44-generic
The link /vmlinuz is a dangling linkto /boot/vmlinuz-3.13.0-44-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /memtest86+.bin
Found kernel: /vmlinuz-3.16.0-29-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up grub-common (2.02~beta2-9ubuntu1) ...
Setting up grub (0.97-29ubuntu66) ...

Configuration file `/etc/event.d/last-good-boot', does not exist on system.
Installing new config file as you requested.
Installing new version of config file /etc/kernel/postinst.d/zz-update-grub ...
Installing new version of config file /etc/kernel/postrm.d/zz-update-grub ...

Configuration file `/etc/kernel/prerm.d/last-good-boot', does not exist on system.
Installing new config file as you requested.

Configuration file `/etc/default/kernel-helper-rc', does not exist on system.
Installing new config file as you requested.
Errors were encountered while processing:
 linux-image-3.13.0-44-generic
 linux-image-extra-3.13.0-44-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```

looks like everything is there though!

```

root@ubuntu:/# ls -l /boot
total 18094
-rw-r--r-- 1 root root 1207195 Dec 16 15:33 abi-3.16.0-29-generic
-rw-r--r-- 1 root root  171768 Dec 16 15:33 config-3.16.0-29-generic
drwxr-xr-x 5 root root    1024 Jan 13 15:59 grub
-rw-r--r-- 1 root root 6663183 Jan 13 15:59 initrd.img-3.16.0-29-generic
drwx------ 2 root root   12288 Jun  3  2014 lost+found
-rw-r--r-- 1 root root  176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root  178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root  178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root 3510761 Dec 16 15:33 System.map-3.16.0-29-generic
-rw------- 1 root root 6344816 Dec 16 15:33 vmlinuz-3.16.0-29-generic
root@ubuntu:/# ls -l /boot/grub
total 2395
-rw-r--r-- 1 root root     191 Jan 13 15:59 default
drwxr-xr-x 2 root root    1024 Jun  3  2014 fonts
-r--r--r-- 1 root root   17374 Dec 16 16:05 grub.cfg
-rw-rw-r-- 1 root root    1024 Jan 13 15:59 grubenv
drwxr-xr-x 2 root root    8192 Aug  5 09:18 i386-pc
drwxr-xr-x 2 root root    1024 Aug  5 09:18 locale
-rw-r--r-- 1 root root    4534 Jan 13 15:59 menu.lst
-rw-r--r-- 1 root root 2405285 Aug  5 09:18 unicode.pf2
root@ubuntu:/# 

```

---

### Post by sandyd on 2015-01-13
Did I forget to write a command to mount /dev/pts?

Yes, I did.... :oops:

Lets try that again.....
```

exit
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt
apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub

```

If that is successful, lets give grub a kickstart...
```

grub-install /dev/sda
update-grub
```

Then do a restart

---

### Post by jdix123 on 2015-01-13
Couple more errors.

```

ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/18.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 508317 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-29-generic_3.16.0-29.39~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-29-generic (3.16.0-29.39~14.04.1) over (3.16.0-29.39~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
Preparing to unpack .../grub_0.97-29ubuntu66_amd64.deb ...
Unpacking grub (0.97-29ubuntu66) over (0.97-29ubuntu66) ...
Preparing to unpack .../grub-common_2.02~beta2-9ubuntu1_amd64.deb ...
Unpacking grub-common (2.02~beta2-9ubuntu1) over (2.02~beta2-9ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up linux-image-3.13.0-44-generic (3.13.0-44.73) ...
Internal Error: Could not find image (/boot/vmlinuz-3.13.0-44-generic)
dpkg: error processing package linux-image-3.13.0-44-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-44-generic:
 linux-image-extra-3.13.0-44-generic depends on linux-image-3.13.0-44-generic; however:
  Package linux-image-3.13.0-44-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-44-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-44-generic; however:
  Package linux-image-3.13.0-44-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-44-generic; however:
  Package linux-image-extra-3.13.0-44-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problemsNo apport report written because the error message indicates its a followup error from a previous failure.
                                                   No apport report written because the error message indicates its a followup error from a previous failure.
                                                                             No apport report written because MaxReports is reached already
                                                            prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.44.51); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.16.0-29-generic (3.16.0-29.39~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.16.0-29.39~14.04.1 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.16.0-29.39~14.04.1 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-29-generic /boot/vmlinuz-3.16.0-29-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.16.0-29-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up grub-common (2.02~beta2-9ubuntu1) ...
Setting up grub (0.97-29ubuntu66) ...
Errors were encountered while processing:
 linux-image-3.13.0-44-generic
 linux-image-extra-3.13.0-44-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 

```

---

### Post by sandyd on 2015-01-13
Seems to be complaining about old kernel

Try
```

apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub linux-image-3.13.0-44-generic
```

If that doesn't work, post the output of
```

dpkg -l | grep linux-image
```

---

### Post by jdix123 on 2015-01-13
```

root@ubuntu:/# apt-get -o DPkg::Options::="--force-confmiss" install --reinstall linux-image-3.16.0-29-generic grub-common grub linux-image-3.13.0-44-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/18.7 MB of archives.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for linux-image-3.13.0-44-generic:amd64
root@ubuntu:/# 

```

---

### Post by sandyd on 2015-01-13
Post the output of
```

dpkg -l | grep linux-image-

```

---

### Post by jdix123 on 2015-01-13
```

root@ubuntu:/# dpkg -l | grep linux-image-
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic                         3.13.0-27.50                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-30-generic                         3.13.0-30.55                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-29-generic                         3.16.0-29.39~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic                   3.13.0-27.50                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                   3.13.0-30.55                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-generic                                   3.13.0.44.51                                        amd64        Generic Linux kernel image


```

---

### Post by sandyd on 2015-01-13
I feel we are making progress

linux-image-generic depends on linux-image-3.13.0-44-generic. While that package is installed, the files in the package are missing, and so are the files in the other kernels.

So, lets just remove all the old kernels that don't exist anymore, and reinstall linux-image-3.13.0-44-generic
```
dpkg --force-depends --purge linux-image-3.13.0-24-generic
dpkg --force-depends --purge linux-image-3.13.0-27-generic
dpkg --force-depends --purge linux-image-3.13.0-29-generic
dpkg --force-depends --purge linux-image-3.13.0-30-generic
dpkg --force-depends --purge linux-image-3.13.0-32-generic
dpkg --force-depends --purge linux-image-3.13.0-34-generic
dpkg --force-depends --purge linux-image-3.13.0-35-generic
dpkg --force-depends --purge linux-image-3.13.0-43-generic
dpkg --force-depends --purge linux-image-3.13.0-44-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-24-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-27-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-29-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-30-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-32-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-34-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-35-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-43-generic
dpkg --force-depends --purge linux-image-extra-3.13.0-44-generic
apt-get install linux-image-3.13.0-44-generic linux-image-extra-3.13.0-44-generic

```

---

### Post by jdix123 on 2015-01-13
Syntax error maybe?

```

root@ubuntu:/# dpkg --ignore-depends --purge linux-image-3.13.0-24-generic
dpkg: error: --ignore-depends needs a valid package name but '--purge' is not: illegal package name in specifier '--purge': must start with an alphanumeric character

```

---

### Post by sandyd on 2015-01-13
fixed

---

### Post by jdix123 on 2015-01-13
Hooray! Looks like everything ran, no errors. 

This looks good too:
```

root@ubuntu:/# ls -l /boot
total 51309
-rw-r--r-- 1 root root  1164720 Dec 15 19:17 abi-3.13.0-44-generic
-rw-r--r-- 1 root root  1207195 Dec 16 15:33 abi-3.16.0-29-generic
-rw-r--r-- 1 root root   165748 Dec 15 19:17 config-3.13.0-44-generic
-rw-r--r-- 1 root root   171768 Dec 16 15:33 config-3.16.0-29-generic
drwxr-xr-x 5 root root     1024 Jan 13 17:12 grub
-rw-r--r-- 1 root root  3328120 Jan 13 17:11 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 20006334 Jan 13 17:11 initrd.img-3.13.0-44-generic
-rw-r--r-- 1 root root  6663276 Jan 13 16:17 initrd.img-3.16.0-29-generic
drwx------ 2 root root    12288 Jun  3  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3388834 Dec 15 19:17 System.map-3.13.0-44-generic
-rw------- 1 root root  3510761 Dec 16 15:33 System.map-3.16.0-29-generic
-rw------- 1 root root  5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
-rw------- 1 root root  6344816 Dec 16 15:33 vmlinuz-3.16.0-29-generic
root@ubuntu:/# ls -l /boot/grub
total 2400
-rw-r--r-- 1 root root     191 Jan 13 15:59 default
drwxr-xr-x 2 root root    1024 Jun  3  2014 fonts
-r--r--r-- 1 root root   17374 Dec 16 16:05 grub.cfg
-rw-rw-r-- 1 root root    1024 Jan 13 16:17 grubenv
drwxr-xr-x 2 root root    8192 Aug  5 09:18 i386-pc
drwxr-xr-x 2 root root    1024 Aug  5 09:18 locale
-rw-r--r-- 1 root root    5010 Jan 13 17:12 menu.lst
-rw-r--r-- 1 root root    5010 Jan 13 17:12 menu.lst~
-rw-r--r-- 1 root root 2405285 Aug  5 09:18 unicode.pf2
root@ubuntu:/# 

```

Time to try a reboot?

---

### Post by sandyd on 2015-01-13
Dpkg seems to have missed one file, initrd.img-3.13.0-43-generic
```
rm /boot/initrd.img-3.13.0-43-generic
```

Seems like I forgot the -extra package for kernel
```

apt-get install linux-image-extra-3.16.0-29-generic
```

Update grub to make sure things are fine
```

update-grub
```

Other than that, everything looks like its ready to go.

I will unfortunately be unavaliable in a few minutes, so someone else will have to take over.

---

### Post by jdix123 on 2015-01-13
Whoops.

```

root@ubuntu:/# apt-get linux-image-extra-3.16.0-29-generic
E: Invalid operation linux-image-extra-3.16.0-29-generic

```

---

### Post by sandyd on 2015-01-13
> **jdix123 said:**
> Whoops.

```

root@ubuntu:/# apt-get linux-image-extra-3.16.0-29-generic
E: Invalid operation linux-image-extra-3.16.0-29-generic

```

fixed typo

---

### Post by oldos2er on 2015-01-13
You left out "install" ```
# apt-get install linux-image-extra-3.16.0-29-generic
```

---

### Post by jdix123 on 2015-01-13
Think I'm learning, I actually caught that one and knew the fix :)

Ok, everything ran. Here's this again

```

root@ubuntu:/# ls -l /boot
total 61372
-rw-r--r-- 1 root root  1164720 Dec 15 19:17 abi-3.13.0-44-generic
-rw-r--r-- 1 root root  1207195 Dec 16 15:33 abi-3.16.0-29-generic
-rw-r--r-- 1 root root   165748 Dec 15 19:17 config-3.13.0-44-generic
-rw-r--r-- 1 root root   171768 Dec 16 15:33 config-3.16.0-29-generic
drwxr-xr-x 5 root root     1024 Jan 13 17:29 grub
-rw-r--r-- 1 root root 20006334 Jan 13 17:11 initrd.img-3.13.0-44-generic
-rw-r--r-- 1 root root 20257882 Jan 13 17:29 initrd.img-3.16.0-29-generic
drwx------ 2 root root    12288 Jun  3  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3388834 Dec 15 19:17 System.map-3.13.0-44-generic
-rw------- 1 root root  3510761 Dec 16 15:33 System.map-3.16.0-29-generic
-rw------- 1 root root  5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
-rw------- 1 root root  6344816 Dec 16 15:33 vmlinuz-3.16.0-29-generic
root@ubuntu:/# ls -l /boot/grub
total 2400
-rw-r--r-- 1 root root     191 Jan 13 15:59 default
drwxr-xr-x 2 root root    1024 Jun  3  2014 fonts
-r--r--r-- 1 root root   17374 Dec 16 16:05 grub.cfg
-rw-rw-r-- 1 root root    1024 Jan 13 16:17 grubenv
drwxr-xr-x 2 root root    8192 Aug  5 09:18 i386-pc
drwxr-xr-x 2 root root    1024 Aug  5 09:18 locale
-rw-r--r-- 1 root root    5010 Jan 13 17:29 menu.lst
-rw-r--r-- 1 root root    5010 Jan 13 17:29 menu.lst~
-rw-r--r-- 1 root root 2405285 Aug  5 09:18 unicode.pf2

```

---

### Post by jdix123 on 2015-01-13
No go on the reboot. Grub seems to hang, then just back to the system splash and grub comes up again.

---

### Post by sandyd on 2015-01-13
Are any of the other kernels working under the advanced menu?

---

### Post by jdix123 on 2015-01-14
every one of them gives an error message

```

Loading Linux 3.13.0-29-generic ...
error: file '\vmlinuz-3.13.0-29-generic' not found.
Loading initial ramdisk ...

```

the filename changes with the linux kernel version I try, of course

---

### Post by sandyd on 2015-01-14
> **jdix123 said:**
> every one of them gives an error message

```

Loading Linux 3.13.0-29-generic ...
error: file '\vmlinuz-3.13.0-29-generic' not found.
Loading initial ramdisk ...

```

the filename changes with the linux kernel version I try, of course

Did you run
```

update-grub
```

in [http://ubuntuforums.org/showthread.php?t=2260652&p=13206981&viewfull=1#post13206981](http://ubuntuforums.org/showthread.php?t=2260652&p=13206981&viewfull=1#post13206981) - Linux shouldn't be showing vmlinuz-3.13.0-29-generic if grub menu is updated as we just removed it.

---

### Post by jdix123 on 2015-01-15
```

ubuntu@ubuntu:~$ sudo umount /dev/mapper/edubuntu--vg-root
umount: /dev/mapper/edubuntu--vg-root: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/mapper/edubuntu--vg-root /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf
cp: missing destination file operand after &#8216;/etc/resolv.conf&#8217;
Try 'cp --help' for more information.
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf mnt/etc/resolv.conf
cp: cannot create regular file &#8216;mnt/etc/resolv.conf&#8217;: No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.16.0-29-generic
Found kernel: /vmlinuz-3.13.0-44-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Ran all that, then went to reboot and I get the same error(s). Specifically I tried the 29 and 44 kernels, as they are the ones that it said grub found.

Also just for kicks, I ran the memtest86+ and that worked just fine.

---

### Post by cigtoxdoc on 2015-01-15
Two thoughts here based on some similar experiences.  First, keep as much of your daat as possible in partitions other than the one with the Ubuntu on it.  For example, a partition that is at /media/mydata.  Second, keep a 20 GB portion of your disk free.  If you need to reinstall Ubuntu, you can reinstall it there under username1 (for exmaple) instead of your usual username.  Data files can them be copied from home/username to home/username1 at your convenience.

John

---

### Post by jdix123 on 2015-01-15
Both pieces of advice are excellent, I might just be looking at copying the contents of my /home to a thumbdrive and reinstalling. Kind of obnoxious but might be my best bet at this point.

Although, I'm still willing to try some stuff because it seems like we made a bunch of progress.

---

### Post by jdix123 on 2015-01-15
And actually its proving harder than I thought to just copy my /home folder. I'm guessing I need to chroot into the system to do so?

Unfortunately I have been unable to glean just what pieces are necesary to mount, where to mount them, etc to then be able to successfully chroot in and copy them.

---

### Post by sandyd on 2015-01-16
> **jdix123 said:**
> ```

ubuntu@ubuntu:~$ sudo umount /dev/mapper/edubuntu--vg-root
umount: /dev/mapper/edubuntu--vg-root: not mounted
ubuntu@ubuntu:~$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted
ubuntu@ubuntu:~$ sudo mount /dev/mapper/edubuntu--vg-root /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf
cp: missing destination file operand after &#8216;/etc/resolv.conf&#8217;
Try 'cp --help' for more information.
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf mnt/etc/resolv.conf
cp: cannot create regular file &#8216;mnt/etc/resolv.conf&#8217;: No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt /bin/bash
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-3.16.0-29-generic
Found kernel: /vmlinuz-3.13.0-44-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Ran all that, then went to reboot and I get the same error(s). Specifically I tried the 29 and 44 kernels, as they are the ones that it said grub found.

Also just for kicks, I ran the memtest86+ and that worked just fine.
Seems to be a bootloader problem now. Unfortunately, I am not familiar with grub/2, though others on the forum may be.

Ubuntu 14.04 (At least) should have Grub2, yet the grub you are using is grub1 (/boot/grub/menu.lst)

Can you post the output of
```

dpkg -l | grep grub
cat /boot/grub/menu.lst

```

---

### Post by sandyd on 2015-01-16
> **jdix123 said:**
> And actually its proving harder than I thought to just copy my /home folder. I'm guessing I need to chroot into the system to do so?

Unfortunately I have been unable to glean just what pieces are necesary to mount, where to mount them, etc to then be able to successfully chroot in and copy them.

```
sudo mount /dev/mapper/edubuntu--vg-root /mnt
```

The home folder should be in /mnt/home/youruser

---

### Post by jdix123 on 2015-01-16
```

ubuntu@ubuntu:~$ sudo mount /dev/mapper/edubuntu--vg--root /mnt
mount: special device /dev/mapper/edubuntu--vg--root does not exist
ubuntu@ubuntu:~$ dpkg -l | grep grub
ii  grub-common                                           2.02~beta2-9                                        amd64        GRand Unified Bootloader (common files)
ii  grub-gfxpayload-lists                                 0.6                                                 amd64        GRUB gfxpayload blacklist
ii  grub-pc                                               2.02~beta2-9                                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS version)
ii  grub-pc-bin                                           2.02~beta2-9                                        amd64        GRand Unified Bootloader, version 2 (PC/BIOS binaries)
ii  grub2-common                                          2.02~beta2-9                                        amd64        GRand Unified Bootloader (common files for version 2)
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

```

Hmm. I don't really get why the mount didn't work that time.

---

### Post by sandyd on 2015-01-16
What does
```

sudo fdisk -l
```
output?

---

### Post by jdix123 on 2015-01-16
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x235091ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/edubuntu--vg-root: 495.8 GB, 495804481536 bytes
255 heads, 63 sectors/track, 60278 cylinders, total 968368128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/edubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/edubuntu--vg-swap_1: 3992 MB, 3992977408 bytes
255 heads, 63 sectors/track, 485 cylinders, total 7798784 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/edubuntu--vg-swap_1 doesn't contain a valid partition table

Disk /dev/sdb: 4043 MB, 4043284480 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7897039     3948488+   b  W95 FAT32
ubuntu@ubuntu:~$

```

---

### Post by jdix123 on 2015-01-17
I wonder if I could get anyone else to help with the Grub issue? Or even the mounting issue so I can get my home folder onto this USB drive and just do a fresh install.  

Either would be wonderful.

---

### Post by jdix123 on 2015-01-19
Any suggestions or should I start a new thread for the grub issue / USB drive transfer?

---

