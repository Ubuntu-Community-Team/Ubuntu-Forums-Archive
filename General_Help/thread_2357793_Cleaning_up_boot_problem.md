---
title: "Cleaning up /boot problem"
date: 2017-04-06
forum: General Help
---

### Post by grey1beard on 2017-04-06
Please advise re cleaning up the boot folder.
I've run sudo apt-get clean as instructed by the small pop up window in the screen shot, but that seems to have no effect.
I've shown in the background part of the contents of the /boot folder, but I don't know what is safe to delete, nor how to go about it.

---

### Post by howefield on 2017-04-06
apt-get clean will remove packages from your /var/cache/apt/archives/ folder which in some cases will free up space, but it won't free up space from your/boot folder.

Try..

```
sudo apt-get autoremove
```

and if you are lucky, it will free enough space for apt to do it's job, if not you'll have to remove some packages manually.

---

### Post by grey1beard on 2017-04-06
Thanks, howefield.
Unfortunately it only removed about 1.7mb, so it looks like a manual clean.
Question then is what is it that I can safely remove ?

I feel like I'm about to go walking through a minefield !
John

---

### Post by howefield on 2017-04-06
Nah, no minefield.. just a few package removals via the command line :)

First, for someone to help you it might be useful to get some more information.. what is the output from these commands ?

```
cat /etc/*-release
```
```
df -h
```
```
df -i
```
```
sudo parted -l
```
```
dpkg -l | grep linux
```

---

### Post by grey1beard on 2017-04-06
Before I post the results, how do I turn it into an attachment, if that's what I need to do, to stop the post becoming a great page full of code ?
John

---

### Post by howefield on 2017-04-06
> **grey1beard said:**
> Before I post the results, how do I turn it into an attachment, if that's what I need to do, to stop the post becoming a great page full of code ?
John

Posting the code is fine.. just put each block of code between [noparse]```

```[/noparse] tags.

---

### Post by grey1beard on 2017-04-06
```
john@john-RM:~$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```
j```
ohn@john-RM:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.4G  4.0K  1.4G   1% /dev
tmpfs           289M  1.4M  288M   1% /run
/dev/dm-0       144G  6.8G  130G   5% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  292K  1.5G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sda1       236M  172M   52M  77% /boot
```
```
john@john-RM:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            211358    516  210842    1% /dev
tmpfs           217130    572  216558    1% /run
/dev/dm-0      9568256 344119 9224137    4% /
none            217130      2  217128    1% /sys/fs/cgroup
none            217130      4  217126    1% /run/lock
none            217130      6  217124    1% /run/shm
none            217130     30  217100    1% /run/user
/dev/sda1        62248    322   61926    1% /boot
```
```
john@john-RM:~$ sudo parted -l
[sudo] password for john: 
Model: ATA Hitachi HTS54501 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   160GB  160GB  extended
 5      257MB   160GB  160GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 157GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  157GB  157GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 3074MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3074MB  3074MB  linux-swap(v1)

```

```
john@john-RM:~$ dpkg -l | grep linux
ii  libselinux1:i386                                      2.2.2-1ubuntu0.1                                    i386         SELinux runtime shared libraries
ii  libv4l-0:i386                                         1.0.1-1                                             i386         Collection of video4linux support libraries
ii  libv4lconvert0:i386                                   1.0.1-1                                             i386         Video4linux frame format conversion library
ii  linux-firmware                                        1.127.23                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-xenial                              4.4.0.71.58                                         i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-57                                4.4.0-57.78~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                        4.4.0-57.78~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-66                                4.4.0-66.87~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-66-generic                        4.4.0-66.87~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-67                                4.4.0-67.88~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-67-generic                        4.4.0-67.88~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-70                                4.4.0-70.91~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-70-generic                        4.4.0-70.91~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-71                                4.4.0-71.92~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-71-generic                        4.4.0-71.92~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-xenial                      4.4.0.71.58                                         i386         Generic Linux kernel headers
rc  linux-image-4.4.0-31-generic                          4.4.0-31.50~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-57-generic                          4.4.0-57.78~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-62-generic                          4.4.0-62.83~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-66-generic                          4.4.0-66.87~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-67-generic                          4.4.0-67.88~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-70-generic                          4.4.0-70.91~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-71-generic                          4.4.0-71.92~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic                    4.4.0-31.50~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic                    4.4.0-62.83~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic                    4.4.0-66.87~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-67-generic                    4.4.0-67.88~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-70-generic                    4.4.0-70.91~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-71-generic                    4.4.0-71.92~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-xenial                        4.4.0.71.58                                         i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-115.162                                      i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                            1.7.2-7                                             i386         Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:4.05+dfsg-6+deb8u1                                i386         collection of boot loaders
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.20.1-5.1ubuntu20.9                                i386         Miscellaneous system utilities
```

---

### Post by howefield on 2017-04-06
OK, thanks for posting that, you almost got it but used quote tags instead of code tags. ;) Code tags preserve the formatting of the terminal output making it easier to read.

One further point I meant to ask for was ..

```
uname -r
```

and check that it isn't one of the below.. it is almost certainly the -71 kernel but just want to make sure that you don't attempt to remove the current kernel.

Try the following..

```
sudo dpkg -P linux-image-4.4.0-{31,57,62}-generic
```
```
sudo dpkg -P linux-image-extra-4.4.0-{31,57,62}-generic
```
```
sudo dpkg -P linux-headers-4.4.0-57-generic
```
```
sudo dpkg -P linux-headers-4.4.0-57
```

That should give you enough headroom to allow apt to do it's work.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Post back any errors.

---

### Post by grey1beard on 2017-04-06
4.4.0-71-generic is the response to uname -r, and thanks for the guidance.
Now going to perform the file-ectomy ! Will post, if there are any further problems.
Regards
John

---

### Post by howefield on 2017-04-06
> **grey1beard said:**
> 4.4.0-71-generic is the response to uname -r, and thanks for the guidance.

Cool, and good luck :)

---

### Post by grey1beard on 2017-04-06
Seemed to be dependency problems with the first code
```
Removing linux-image-4.4.0-31-generic (4.4.0-31.50~14.04.1) ...
Purging configuration files for linux-image-4.4.0-31-generic (4.4.0-31.50~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic.

dpkg: error processing package linux-image-4.4.0-57-generic (--purge):
 dependency problems - not removing
Removing linux-image-4.4.0-62-generic (4.4.0-62.83~14.04.1) ...
Purging configuration files for linux-image-4.4.0-62-generic (4.4.0-62.83~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Errors were encountered while processing:
 linux-image-4.4.0-57-generic
john@john-RM:~$
```

Do I proceed with the others, or wait your input ?

---

### Post by grey1beard on 2017-04-06
I've now completed the removal, but with no further error messages. Perhaps the later code did the necessary ?
John

---

### Post by howefield on 2017-04-06
OK, so *sudo apt-get update* and *sudo apt-get upgrade* completed successfully without error ?

---

### Post by grey1beard on 2017-04-06
Yes, they seemed to work without any error messages.
Thanks for your help,
John

---

### Post by howefield on 2017-04-06
> **grey1beard said:**
> Yes, they seemed to work without any error messages.

That's great but you are not done yet.

Your LVM installation means a pretty small /boot folder so the next kernel update or so is going to see you in the same position again.

Now that apt appears to be working, I'd try.. 

```
sudo apt-get autoremove
```

hopefully that will offer to remove all bar the current and next to current kernel but this will be something that you need to repeat on a regular basis, preferably before it becomes a problem. There are various ways to achieve this.

If that doesn't remove the old kernels, we can try an alternative method.

---

### Post by grey1beard on 2017-04-06
Ah, right.
Ran autoremove, but I suspect that nothing went.
I've just had a look at the boot folder and that still looks the same to me.
Checked 'properties', and it has 66MB free space, with about 164MB used.
What next ?
John
EDIT
Just rebooted, and the software updater tries again, but this time it needs about another 3MB to run.
So, in effect, I still have the same problem !
I can see a lot of files in the /boot folder that date from 10 Dec 2016, which all seem to be 4.4.0-57 related, and add up to about 25MB.
Can these be manually deleted, or even selected for deletion via Terminal ?

---

### Post by SeijiSensei on 2017-04-06
Post the results of "ls -l /boot".  Let's see how much cruft is left behind.  My /boot has just two kernels and associated files; it occupies about 110 MB.

---

### Post by grey1beard on 2017-04-06
ls -l /boot
```
john@john-RM:~$ ls -l /boot
total 157438
-rw-r--r-- 1 root root  1239906 Dec 10 02:48 abi-4.4.0-57-generic
-rw-r--r-- 1 root root  1241618 Mar  3 20:17 abi-4.4.0-66-generic
-rw-r--r-- 1 root root  1241765 Mar  9 17:42 abi-4.4.0-67-generic
-rw-r--r-- 1 root root  1241765 Mar 22 18:00 abi-4.4.0-70-generic
-rw-r--r-- 1 root root  1241765 Mar 24 18:48 abi-4.4.0-71-generic
-rw-r--r-- 1 root root   193394 Dec 10 02:48 config-4.4.0-57-generic
-rw-r--r-- 1 root root   193650 Mar  3 20:17 config-4.4.0-66-generic
-rw-r--r-- 1 root root   193639 Mar  9 17:42 config-4.4.0-67-generic
-rw-r--r-- 1 root root   193639 Mar 22 18:00 config-4.4.0-70-generic
-rw-r--r-- 1 root root   193639 Mar 24 18:48 config-4.4.0-71-generic
drwxr-xr-x 5 root root     1024 Apr  6 12:08 grub
-rw-r--r-- 1 root root  3310283 Apr  2 21:04 initrd.img-4.4.0-31-generic
-rw-r--r-- 1 root root 10047589 Apr  6 12:08 initrd.img-4.4.0-57-generic
-rw-r--r-- 1 root root 22612396 Mar  8 01:33 initrd.img-4.4.0-66-generic
-rw-r--r-- 1 root root 22618005 Mar 16 11:48 initrd.img-4.4.0-67-generic
-rw-r--r-- 1 root root 22626502 Apr  2 21:05 initrd.img-4.4.0-70-generic
-rw-r--r-- 1 root root 22630369 Apr  2 21:17 initrd.img-4.4.0-71-generic
drwx------ 2 root root    12288 Dec 23 12:01 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3104738 Dec 10 02:48 System.map-4.4.0-57-generic
-rw------- 1 root root  3111783 Mar  3 20:17 System.map-4.4.0-66-generic
-rw------- 1 root root  3110502 Mar  9 17:42 System.map-4.4.0-67-generic
-rw------- 1 root root  3110489 Mar 22 18:00 System.map-4.4.0-70-generic
-rw------- 1 root root  3110489 Mar 24 18:48 System.map-4.4.0-71-generic
-rw------- 1 root root  6672656 Dec 10 02:48 vmlinuz-4.4.0-57-generic
-rw------- 1 root root  6688560 Mar  3 20:17 vmlinuz-4.4.0-66-generic
-rw------- 1 root root  6689168 Mar  9 17:42 vmlinuz-4.4.0-67-generic
-rw------- 1 root root  6688912 Mar 22 18:00 vmlinuz-4.4.0-70-generic
-rw------- 1 root root  6688912 Mar 24 18:48 vmlinuz-4.4.0-71-generic
```

---

### Post by SeijiSensei on 2017-04-06
You want to get rid of the 57, 66, and 67 kernels.  The proper way is to use apt.  Let's start with the oldest one:
```
sudo apt-get remove linux-image-4.4.0-57-generic
```
If that works correctly, move on to the other two.

If for some reason this doesn't work, you can brute-force the deletion with 
```

cd /boot
sudo rm *4.4.0-57*

```
but it's better to have apt do the removals so it will update its database of installed packages.

---

### Post by grey1beard on 2017-04-06
Thanks, Seiji Sensei, that has worked OK. Just left with 0-70 and 0-71.
Noticed one oddity - there is a folder initrd.img-4.4.0-31-generic with no other folders that appear to relate to it, like an orphan !

Regards
John

---

### Post by SeijiSensei on 2017-04-07
Initrd is a file, not a folder.  It's basically a stripped down operating system image that contains just the files needed to boot the machine before mounting the drive where the actual operating system is located.  If you have one of these left around that is not related to a working kernel, then you can delete it as well.

---

### Post by grey1beard on 2017-04-07
Thanks. I think that you have finally laid my problem to rest, and this is now truly 'Solved'.
John

---

