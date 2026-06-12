---
title: "Disk space message"
date: 2017-03-11
forum: General Help
---

### Post by glendavee on 2017-03-11
I am running 16.10, 64 bit. I have suddenly started getting message "this computer has only 453 MB disk space remaining" on every startup. I have checked partitions and this doesn't make sense. I have a 2TB drive. There is 3.37GB unused on /sda2 (linux system) and 1.67TB on /sda4 (home ) There is 8.8GB on /sda3 (swop). Is this a bug or should I do something
Grateful for any help

---

### Post by ian-weisser on 2017-03-11
One imagines you should investigate before your system becomes unbootable.
Start with 'df' and 'df -i'

---

### Post by gordintoronto on 2017-03-11
Do you have a /boot? Have you ever removed old kernels which have built up over time?

---

### Post by glendavee on 2017-03-11
df -i gives  
```
david@david-H61M-S2V-B3:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            489640    579  489061    1% /dev
tmpfs           495073    856  494217    1% /run
/dev/sda2      3842048 455397 3386651   12% /
tmpfs           495073     15  495058    1% /dev/shm
tmpfs           495073      5  495068    1% /run/lock
tmpfs           495073     18  495055    1% /sys/fs/cgroup
tmpfs           495073     58  495015    1% /run/user/1000
```

---

### Post by Bashing-om on 2017-03-11
glendavee; Hello;

That do say it is NOT a inode issue .
So what is the (D)isk (U)sage ? The 'df' command, with a different switch , will give a quick look:
```

df -h

```
 If one desires a deeper analysis one can install the ncdu tool - as a side note - .
'df -h' I expect here to tell all that needs told.

[INDENT][INDENT]we like clean systems, make it so 
[/INDENT][/INDENT]

---

### Post by glendavee on 2017-03-11
Output from df -h is```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  6.5M  381M   2% /run
/dev/sda2        58G   55G  451M 100% /
tmpfs           1.9G   31M  1.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           387M  120K  387M   1% /run/user/1000
```

---

### Post by Bashing-om on 2017-03-11
glendavee; Well,

Yeah the tale is told:
> 
/dev/sda2 58G 55G 451M 100% /

Now at 100% usage we may have a problem.
But let's try anyway and see if apt is able to operate :
```

sudo apt autoclean
sudo apt clean
sudp apt autoremove

```
else we have to roll our sleeves up and get that disk space manually.
Post back - Between Code Tags - to maintain readability and formatting !
```

uname -r
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by glendavee on 2017-03-11
Did the apt thing - seems to have done something. I rebooted and didn't get the disk message
I haven't done anything else

---

### Post by Bashing-om on 2017-03-11
glendavee; Hey !

If apt "did it's thing" we have no need to do anything else.
But, verify !
```

df -h

```
show now that here is ample space in /boot ?

[INDENT][INDENT]maybe YeS
[INDENT][INDENT]maybe not so yes[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by glendavee on 2017-03-11
Indeed
df -h gives```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  6.5M  381M   2% /run
/dev/sda2        58G   53G  2.3G  96% /
tmpfs           1.9G   12M  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           387M  108K  387M   1% /run/user/1000
```

---

### Post by Bashing-om on 2017-03-11
glendavee; nope !

There is a problem !
> 
/dev/sda2 58G 53G 2.3G 96% /


We are still at 96% capacity .. linux chokes at 90% as file journalling begins to break down .

So we need to know the why we did not get that disk space back with ' autoremove '.

Post back BETWEEN code tags :
```

sudo apt autoremove
dpkg -l | grep linux-
ls -al /boot/

```

[INDENT][INDENT]a process in discovery
[/INDENT][/INDENT]

---

### Post by glendavee on 2017-03-12
Here's the result of your suggestions
```

david@david-H61M-S2V-B3:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
```
```

david@david-H61M-S2V-B3:~$ dpkg -l | grep linux
ii  console-setup-linux                             1.142ubuntu5                                all          Linux specific part of console-setup
ii  libselinux1:amd64                               2.5-3                                       amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                2.5-3                                       i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                  1.10.1-1                                    amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                            1.10.1-1                                    amd64        Video4linux frame format conversion library
ii  linux-base                                      4.0ubuntu1                                  all          Linux image base package
ii  linux-firmware                                  1.161.1                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                   4.8.0.41.52                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.8.0-37                          4.8.0-37.39                                 all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-37-generic                  4.8.0-37.39                                 amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-4.8.0-41                          4.8.0-41.44                                 all          Header files related to Linux kernel version 4.8.0
ii  linux-headers-4.8.0-41-generic                  4.8.0-41.44                                 amd64        Linux kernel headers for version 4.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                           4.8.0.41.52                                 amd64        Generic Linux kernel headers
rc  linux-image-4.8.0-22-generic                    4.8.0-22.24                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-26-generic                    4.8.0-26.28                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-27-generic                    4.8.0-27.29                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-28-generic                    4.8.0-28.30                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-30-generic                    4.8.0-30.32                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-32-generic                    4.8.0-32.34                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-34-generic                    4.8.0-34.36                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-37-generic                    4.8.0-37.39                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-41-generic                    4.8.0-41.44                                 amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-22-generic              4.8.0-22.24                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-26-generic              4.8.0-26.28                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-27-generic              4.8.0-27.29                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-28-generic              4.8.0-28.30                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-30-generic              4.8.0-30.32                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-32-generic              4.8.0-32.34                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-34-generic              4.8.0-34.36                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-37-generic              4.8.0-37.39                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-41-generic              4.8.0-41.44                                 amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic                             4.8.0.41.52                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                            4.8.0-41.44                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                                1.0.25+dfsg-0ubuntu5                        all          base package for ALSA and OSS sound systems
ii  pptp-linux                                      1.8.0-1                                     amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                        3:6.03+dfsg-14                              amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                 3:6.03+dfsg-14                              all          collection of bootloaders (common)
ii  syslinux-legacy                                 2:3.63+dfsg-2ubuntu8                        amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                      2.28.2-1ubuntu1.1                           amd64        miscellaneous system utilities
```

```
david@david-H61M-S2V-B3:~$ ls -al /boot/
total 106804
drwxr-xr-x  3 root root     4096 Mar 11 23:26 .
drwxr-xr-x 24 root root     4096 Mar  9 10:56 ..
-rw-r--r--  1 root root  1407843 Jan 25 18:12 abi-4.8.0-37-generic
-rw-r--r--  1 root root  1408261 Mar  3 11:23 abi-4.8.0-41-generic
-rw-r--r--  1 root root   199567 Jan 25 18:12 config-4.8.0-37-generic
-rw-r--r--  1 root root   199567 Mar  3 11:23 config-4.8.0-41-generic
drwxr-xr-x  5 root root     4096 Mar 11 23:26 grub
-rw-r--r--  1 root root 41235028 Feb  4 13:15 initrd.img-4.8.0-37-generic
-rw-r--r--  1 root root 41230605 Mar 11 14:36 initrd.img-4.8.0-41-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4061046 Jan 25 18:12 System.map-4.8.0-37-generic
-rw-------  1 root root  4068067 Mar  3 11:23 System.map-4.8.0-41-generic
-rw-------  1 root root  7472928 Jan 25 18:12 vmlinuz-4.8.0-37-generic
-rw-------  1 root root  7489312 Mar  3 11:23 vmlinuz-4.8.0-41-generic
```

Hope it makes sense to you

---

### Post by Impavidus on 2017-03-12
> **glendavee said:**
> I am running 16.10, 64 bit. I have suddenly started getting message "this computer has only 453 MB disk space remaining" on every startup. I have checked partitions and this doesn't make sense. I have a 2TB drive. There is 3.37GB unused on /sda2 (linux system) and **1.67TB on /sda4 (home )** There is 8.8GB on /sda3 (swop). Is this a bug or should I do something
Grateful for any help

> **glendavee said:**
> Indeed
df -h gives
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  6.5M  381M   2% /run
/dev/sda2        58G   53G  2.3G  96% /
tmpfs           1.9G   12M  1.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           387M  108K  387M   1% /run/user/1000Here is a contradiction. You state there is 1.67TB free space on your /home partition, but according to df you don't have a /home partition. Maybe something went wrong when you last reinstalled. Maybe you wanted to keep a /home partition but didn't create the right entry in /etc/fstab, keeping /home on the root partition and allowing it to fill up.

---

### Post by glendavee on 2017-03-12
iI what you suggest is true, how do I go about fixing it? I would like to have my home on a separate partition (which I think already exists)

---

### Post by Bashing-om on 2017-03-12
glendavee; Hey ..

According to 'df' you do not have a separate /home .
We can verify that :
```

sudo parted -l

```
And, there are but the 2 kernels now installed, so where is the space consumed from ?
show us a new :
```

df -h

```
We then get ready to delve deeper .

[INDENT][INDENT]better to know
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-03-12
First find your supposed /home partition. You say it's /dev/sda4. Verify that. Mount the partition somewhere and browse it. You can do that using the file manager. Does it look like your /home partition? Then you can go on with the next step.

It may be easiest to do this from a live disk, but it is possible from within your installed system. In the latter case, changing files while you're fixing this may have some funny effects, so close all non-essential applications. Make sure your /home partition and your root partition with your /home directory are both mounted. Make sure than on both you have the same user ID, but normally, that should already be the case. Next you probably want to sync all files on the /home partition with those on the root partition. You can use rsync:```
sudo rsync -au /path/to/root-partition/home/. /path/to/home-partition/.
```Maybe you want different options to make sure you don't throw away files from your /home partition that have the same name as files on your root partition. Read the manual of rsync.

Then modify /etc/fstab on your root partition. Add the line```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /home           ext4    defaults 0 2
```substituting the correct UUID and whatever is non-standard on your system. Then rename the /home/ directory on your root partition, for example to /old-home/. If you do this within your installed system, you can now mount the /home/ partition:```
sudo mount -a
```If you did it from a live system, you can reboot. Make sure everything works and you haven't lost any files. If everything is OK, you can delete your old home directory, now named /old-home/.

If you feel unsure about anything, ask.

---

### Post by glendavee on 2017-03-12
Everybody
I decided (maybe foolishly) to move my home directory to the existing partition in which I thought it was. I followed these directions ps://help.ubuntu.com/community/Partitioning/Home/Moving. I've done this and now parted-l gives```

Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1049kB  62.9GB  62.9GB  ext4
 4      62.9GB  1990GB  1927GB  ext4                  msftdata
 3      1990GB  1999GB  9452MB  linux-swap(v1)
```
and df -h gives```

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  6.5M  381M   2% /run
/dev/sda2        58G   53G  2.3G  96% /
tmpfs           1.9G   32M  1.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda4       1.8T   67G  1.6T   4% /home
tmpfs           387M  120K  387M   1% /run/user/1000
```

All seems ok, but I'm waiting!

---

### Post by Impavidus on 2017-03-13
That should work.

That guide instructed you to rename the /home directory on your root partition to /old_home. I assume you did so. Once you have verified that all files you still need have been copied to your /home partition, you can delete /old_home. That will free some disk space on your root partition, which is now still 96% full.

---

### Post by glendavee on 2017-03-13
Thanks all. I won't delete old_home for a while (until I'm happy)

---

