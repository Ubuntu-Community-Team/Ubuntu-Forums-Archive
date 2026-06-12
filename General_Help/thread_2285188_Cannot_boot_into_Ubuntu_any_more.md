---
title: "Cannot boot into Ubuntu any more"
date: 2015-07-03
forum: General Help
---

### Post by istvan5 on 2015-07-03
Hi !

I had the problem with my Ubuntu installation that it had not enough space any more on the ~ ubuntu partition,
so I get in troubles when automatic software updates wanted to install.

Now I resized my ~ ubuntu partition, but I Ubuntu cannot load any more. This is a dual boot, windows is still working,
I can access GRUB menu to select and start windows, but when I want to start Ubuntu, nothing happens any more, even,
when pressing NumLock on the keyboard, the led is not going off and and on, so it looks like it is freezing.
I does not matter if I want to start Ubuntu oder Ubuntu in Recovery mode.

I tried to use boot-repair. But it does not work.

I can start from USB live disk with ubuntu, also I tried to use menu "installing ubuntu", but it says, all ubuntu progamms would be gone,
it is not saying, "my programs will not be deleted".

I have my home folder on different partition, I have a backup, 
but I don't want to loose all the settings I made in the current Ubuntu installation.

It would be great if I could solve this problem, WITHOUT installing new.


Any idea?
Can I fix something?


thx,

---

### Post by istvan5 on 2015-07-05
I found out that I have a 
  KERNEL PANIC
([http://askubuntu.com/questions/71332/kernel-panics-with-cannot-open-root-device-error-where-do-i-append-the-root](http://askubuntu.com/questions/71332/kernel-panics-with-cannot-open-root-device-error-where-do-i-append-the-root))

it says
"cannot open root devide sda5"
and get
"corret "root=" boot option


now I am looking how to configure the boot ...

---

### Post by istvan5 on 2015-07-05
**problem solved**


here is a summary


It was not enough space any more where the Ubuntu files are installed,
automatic software updates needed space,

I tried to get rid off unnecessary files, with autoremove, remove, clear cache etc
2 times, Ubuntu was able to restart, but then, Ubuntu was not able to start any more

it was a kernel panic with 

[COLOR=#000000]"cannot open root devide sda5"
[/COLOR]
[COLOR=#000000]and get
[/COLOR]
[COLOR=#000000]"corret "root=" boot option[/COLOR]


I took the partition directly behind the Ubuntu partition and deleted it,
resized the Ubuntu partition with the new space.

still the Ubuntu could not start, also BOOT-REPAIR did not help,
(also BOOT-REPAIR sayed something, "it can be that you cannot start Ubuntu because low space on disk..)


**The solution was:**

I had to boot with the "recovery mode" of the previous kernel version.

The latest kernel I had installed was  3.13.0-55-generic
this did not start, also not the "recovery mode" of 3.13.0-55-generic

I started the previous kernel's "recovery mode", 3.13.0-53-generic
here I tried to use the "clean" option.
Which did not work at the beginning, it stuck with the second partition,
I had to hard reset my machine when "clean" option was not doing anything any more

I booted from Live USB, looked at the /etc/fstab on the harddisk and deactivated unneccesary mountings.

I booted from the harddisk, and could use the "clean" option of the previous kernel's "recovery mode", 3.13.0-53-generic  successfully.
The "clean" was finished.

In the menu, it was asking if I want to resume the Ubuntu startup. I said yes, it also warned the graphical
will be maybe not perfect. In this case, I should reboot Ubuntu normally.
So I did this, I started previous kernel's normal startup,   3.13.0-53-generic

After booting up successfully, I deleted in synaptic manager the latest kernel which has troubles, the 3.13.0-55-generic
(so the working 3.13.0-53-generic is now in my dual boot GRUB menu... not the bad 3.13.0-55-generic one)

Now I have kernel 3.13.0-53-generic and a working system

---

### Post by istvan5 on 2015-07-05
[COLOR=#000000]I tried to install and use [/COLOR][COLOR=#000000]3.13.0-54-generic 
and [/COLOR][COLOR=#000000]3.13.0-55-generic 

but booth of them don't work for me...


[/COLOR]

---

### Post by Bashing-om on 2015-07-05
istvan5; Hello;

A out-of-space condition can have it frustrations, and you have done well in booting the -53 kernel.

Let's get a look at the hardrive/space issue as is presently:
```

sudo fdisk -lu
sudo parted -l
df -h
df -i

```

And what do we have now for installed kernels ?
```

dpkg -l | grep linux-

```
These outputs should point in the direction we need to go.

[INDENT][INDENT]it is in the process
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-07-09
thx for your support, here is the data you requested
I resized [COLOR=#000000][FONT=Ubuntu Mono]/dev/sda5 
[/FONT][/COLOR]now it is double size than before my problem with free space occured

```
xy@xy:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   125045423    62522711+  ee  GPT


Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003007d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    93782015    46889984   83  Linux
/dev/sdb2        93784064   125044735    15630336    7  HPFS/NTFS/exFAT




xy@xy:~$ sudo parted -l
Model: ATA SanDisk SDSSDP06 (scsi)
Disk /dev/sda: 64,0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  135MB   134MB                   Microsoft reserved partition  msftres
 2      135MB   316MB   180MB                   Basic data partition          msftdata
 3      316MB   419MB   104MB   fat32           EFI system partition          boot
 4      419MB   32,6GB  32,1GB  ntfs            Basic data partition          msftdata
 5      32,6GB  57,3GB  24,7GB  ext4                                          msftdata
 7      60,0GB  64,0GB  4000MB  linux-swap(v1)




Model: ATA TS64GMSA340 (scsi)
Disk /dev/sdb: 64,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  48,0GB  48,0GB  primary  ext4
 2      48,0GB  64,0GB  16,0GB  primary  ntfs

xy@xy:~$ df -h
#Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        23G  7,7G   14G  36% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,7G  4,0K  1,7G   1% /dev
tmpfs           341M  1,2M  339M   1% /run
none            5,0M     0  5,0M   0% /run/lock
tmpfs           1,7G   43M  1,7G   3% /run/shm
none            100M   20K  100M   1% /run/user
/dev/sdb1        44G   18G   25G  42% /home
/dev/sda3        95M   50M   46M  52% /boot/efi




xy@xy:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda5      1515520 218317 1297203   15% /
none            435349      2  435347    1% /sys/fs/cgroup
udev            432652    530  432122    1% /dev
tmpfs           435349    558  434791    1% /run
none            435349      3  435346    1% /run/lock
tmpfs           435349    161  435188    1% /run/shm
none            435349     19  435330    1% /run/user
/dev/sdb1      2932736 120041 2812695    5% /home
/dev/sda3            0      0       0     - /boot/efi


xy@xy:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.127.13                                all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-52                     3.13.0-52.86                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic             3.13.0-52.86                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                     3.13.0-53.89                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic             3.13.0-53.89                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic               3.13.0-36.63                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-37-generic               3.13.0-37.64                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic               3.13.0-39.66                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic               3.13.0-40.69                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic               3.13.0-43.72                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic               3.13.0-44.73                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic               3.13.0-45.74                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic               3.13.0-46.79                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic               3.13.0-48.80                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic               3.13.0-49.83                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic               3.13.0-52.86                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic               3.13.0-53.89                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic         3.13.0-36.63                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-37-generic         3.13.0-37.64                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic         3.13.0-39.66                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic         3.13.0-40.69                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic         3.13.0-43.72                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic         3.13.0-44.73                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic         3.13.0-45.74                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic         3.13.0-46.79                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic         3.13.0-48.80                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic         3.13.0-49.83                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic         3.13.0-51.84                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic         3.13.0-52.86                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic         3.13.0-53.89                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                        3.13.0-57.95                            amd64        Linux Kernel Headers for development
rc  linux-signed-image-3.11.0-26-generic        3.11.0-26.45                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-36-generic        3.13.0-36.63                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-37-generic        3.13.0-37.64                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-39-generic        3.13.0-39.66                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-40-generic        3.13.0-40.69                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-43-generic        3.13.0-43.72                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-44-generic        3.13.0-44.73                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-45-generic        3.13.0-45.74                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-46-generic        3.13.0-46.79                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-48-generic        3.13.0-48.80                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-49-generic        3.13.0-49.83                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-51-generic        3.13.0-51.84                            amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-52-generic        3.13.0-52.86                            amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-53-generic        3.13.0-53.89                            amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-55-generic        3.13.0-55.94                            amd64        Signed kernel image generic
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:4.05+dfsg-6+deb8u1                    all          collection of boot loaders (common files)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                      12-3ubuntu0.14.04.1                     all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy               12-3ubuntu0.14.04.1                     all          collection of boot loaders (debian-wheezy theme)





```

---

### Post by Bashing-om on 2015-07-09
istvan5; Hey, hey ;

Not look'n real bad.
A bit of cleanup first:
The state is rc, the package is (r)emoved, but the (c)onfig files are not removed.
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now, let's try and get you up on the latest kernel:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

If there is a problem post back the outputs of the above commands.

[INDENT][INDENT]maybe all is well now ?
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-07-19
Hi bashing-om,

I did the purge and **worked** **fine**
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
now I don't have "rc" stuff any more

Thank you very much !!

> xy@xy:~$ dpkg -l | grep linux-ii  linux-firmware                              1.127.13                                all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-52                     3.13.0-52.86                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic             3.13.0-52.86                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                     3.13.0-53.89                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic             3.13.0-53.89                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic               3.13.0-52.86                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic               3.13.0-53.89                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic         3.13.0-52.86                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic         3.13.0-53.89                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                        3.13.0-57.95                            amd64        Linux Kernel Headers for development
ii  linux-signed-image-3.13.0-52-generic        3.13.0-52.86                            amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-53-generic        3.13.0-53.89                            amd64        Signed kernel image generic
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:4.05+dfsg-6+deb8u1                    all          collection of boot loaders (common files)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                      12-3ubuntu0.14.04.1                     all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy               12-3ubuntu0.14.04.1                     all          collection of boot loaders (debian-wheezy theme)
xy@xy:~$ 




But somehow, it don't want  update to the lastest kernel  (so my kernel now is still 3.13.0-53-generic)   
- I am even not sure, would it be better to upgrade to the lastest kernel ?
or can it be that newer kernel would not have hardware support for "older" hardware?
( I mean my system is from 2014, so not too old)

I did this, but no new kernel found 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by Bashing-om on 2015-07-19
istvan5; Welp;

The latest kernels should install !
After running the 'dist-upgrade' command, let's look and see what is available in /boot .
```

dpkg -l | grep linux-
ls -al /boot

```

If the -57 kernel is not there, we start the process of finding out the why-not.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-07-21
dist-upgrade don't work...
   sudo apt-get dist-upgrade


-57 is only here:

ii  linux-libc-dev:amd64                        3.13.0-57.95                             amd64        Linux Kernel Headers for development

--> maybe this is blocking the installation of kernel -57 ?
--> maybe I sould delete this?

> xy@xy:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.127.13                                all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-52                     3.13.0-52.86                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic             3.13.0-52.86                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                     3.13.0-53.89                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic             3.13.0-53.89                            amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic               3.13.0-52.86                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic               3.13.0-53.89                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic         3.13.0-52.86                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic         3.13.0-53.89                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                        3.13.0-57.95                            amd64        Linux Kernel Headers for development
ii  linux-signed-image-3.13.0-52-generic        3.13.0-52.86                            amd64        Signed kernel image generic
ii  linux-signed-image-3.13.0-53-generic        3.13.0-53.89                            amd64        Signed kernel image generic
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:4.05+dfsg-6+deb8u1                    all          collection of boot loaders (common files)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                      12-3ubuntu0.14.04.1                     all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy               12-3ubuntu0.14.04.1                     all          collection of boot loaders (debian-wheezy theme)
xy@xy:~$ 

xy@xy:~$ ls -al /boot
total 83333
drwxr-xr-x  6 root root     4096 Jul  5 20:12 .
drwxr-xr-x 23 root root     4096 Jul  5 20:12 ..
-rw-r--r--  1 root root  1164671 Mai  4 07:09 abi-3.13.0-52-generic
-rw-r--r--  1 root root  1164671 Mai 20 13:11 abi-3.13.0-53-generic
-rw-r--r--  1 root root   165762 Mai  4 07:09 config-3.13.0-52-generic
-rw-r--r--  1 root root   165762 Mai 20 13:11 config-3.13.0-53-generic
drwxr-xr-x  4 root root     1024 Jän  1  1970 efi
drwxr-xr-x  3 root root     4096 Jul 10 19:15 extlinux
drwxr-xr-x  5 root root     4096 Jul 16 01:37 grub
drwxr-xr-x  5 root root     4096 Mai  7  2014 grub.bak
-rw-r--r--  1 root root  2709108 Feb  1 21:24 initrd.img-3.13.0-40-generic
-rw-r--r--  1 root root  2709371 Feb  1 21:24 initrd.img-3.13.0-43-generic
-rw-r--r--  1 root root  2709365 Feb  1 21:24 initrd.img-3.13.0-44-generic
-rw-r--r--  1 root root  2708085 Mai 12 18:33 initrd.img-3.13.0-46-generic
-rw-r--r--  1 root root  2708075 Mai 12 18:33 initrd.img-3.13.0-48-generic
-rw-r--r--  1 root root 19204935 Mai 12 18:03 initrd.img-3.13.0-52-generic
-rw-r--r--  1 root root 19208649 Jun 20 18:15 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389875 Mai  4 07:09 System.map-3.13.0-52-generic
-rw-------  1 root root  3390132 Mai 20 13:11 System.map-3.13.0-53-generic
-rw-------  1 root root  5818592 Mai  4 07:09 vmlinuz-3.13.0-52-generic
-rw-------  1 root root  5820504 Mai 12 18:03 vmlinuz-3.13.0-52-generic.efi.signed
-rw-------  1 root root  5821152 Mai 20 13:11 vmlinuz-3.13.0-53-generic
-rw-------  1 root root  5823064 Mai 23 13:50 vmlinuz-3.13.0-53-generic.efi.signed
xy@xy:~$ 


I have a Lubuntu, upgraded 1 or 2 times... maybe this is the reason for several initrd.img*



---

### Post by Bashing-om on 2015-07-21
istvan5l Maybe ?
Removing the development kernel sure might help;
This however:
```

-rw-r--r-- 1 root root 2709108 Feb 1 21:24 initrd.img-3.13.0-40-generic
-rw-r--r-- 1 root root 2709371 Feb 1 21:24 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 2709365 Feb 1 21:24 initrd.img-3.13.0-44-generic
-rw-r--r-- 1 root root 2708085 Mai 12 18:33 initrd.img-3.13.0-46-generic
-rw-r--r-- 1 root root 2708075 Mai 12 18:33 initrd.img-3.13.0-48-generic

```
Is making me sit back and consider. What are these old initrd.img files doing hanging about ? I am not real sure of a proper way to remove them at this time.

May take more than a trip to the potty
[INDENT][INDENT]to come up with an answer
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-22
istvan5; Morning .

My considered opinion, we remove the -dev kernel, and we get prepared to get dirty.

What else are we looking at ?
Post back also the results:
```

ls -la /lib/modules/
ls -al /usr/src/

```

We remove the obstructions manually, and have the package manager 'fix' the damage.

[INDENT][INDENT]I think we can
[INDENT][INDENT][INDENT]I think we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by istvan5 on 2015-07-24
Hi Bashing-Om,

I deleted the development kernel
> 
xy@xy:~$ sudo apt-get --purge remove linux-libc-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  build-essential* comerr-dev* g++* g++-4.8* krb5-multidev* libc6-dev*
  libcurl4-openssl-dev* libgcrypt11-dev* libgnutls-dev* libkrb5-dev*
  librtmp-dev* libssl-dev* libstdc++-4.8-dev* linux-libc-dev* zlib1g-dev*
0 upgraded, 0 newly installed, 15 to remove and 1 not upgraded.
After this operation, 66,1 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 207477 files and directories currently installed.)
Removing build-essential (11.6ubuntu6) ...
Removing libcurl4-openssl-dev:amd64 (7.35.0-1ubuntu2.5) ...
Removing libkrb5-dev (1.12+dfsg-2ubuntu5.1) ...
Removing krb5-multidev (1.12+dfsg-2ubuntu5.1) ...
Removing comerr-dev (2.1-1.42.9-3ubuntu1.2) ...
Removing g++ (4:4.8.2-1ubuntu6) ...
Removing g++-4.8 (4.8.4-2ubuntu1~14.04) ...
Removing libstdc++-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04) ...
Removing librtmp-dev (2.4+20121230.gitdf6c518-1) ...
Removing libgnutls-dev (2.12.23-12ubuntu2.2) ...
Removing libgcrypt11-dev (1.5.3-2ubuntu4.2) ...
Removing libssl-dev:amd64 (1.0.1f-1ubuntu2.15) ...
Removing zlib1g-dev:amd64 (1:1.2.8.dfsg-1ubuntu1) ...
Removing libc6-dev:amd64 (2.19-0ubuntu6.6) ...
Removing linux-libc-dev:amd64 (3.13.0-58.97) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...

then I made 
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-update
no new kernel found.. (just a new chrome..)

Here are the commands you suggested
> xy@xy:~$ ls -la /lib/modules/total 16
drwxr-xr-x  4 root root 4096 Jul  5 20:12 .
drwxr-xr-x 23 root root 4096 Feb 28 01:02 ..
drwxr-xr-x  5 root root 4096 Mai 12 18:02 3.13.0-52-generic
drwxr-xr-x  5 root root 4096 Mai 23 13:50 3.13.0-53-generic

xy@xy:~$ ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 Jul  5 20:11 .
drwxr-xr-x 10 root root 4096 Feb  1 21:18 ..
drwxr-xr-x 24 root root 4096 Mai 12 18:01 linux-headers-3.13.0-52
drwxr-xr-x  7 root root 4096 Mai 12 18:01 linux-headers-3.13.0-52-generic
drwxr-xr-x 24 root root 4096 Mai 23 13:49 linux-headers-3.13.0-53
drwxr-xr-x  7 root root 4096 Mai 23 13:49 linux-headers-3.13.0-53-generic

I have a Lubuntu, upgraded 1 or 2 times... maybe this is the reason for several initrd.img*  ?

---

### Post by Bashing-om on 2015-07-24
istvan5; Welp ;

The directories /lib/modules/, and /usr/src/ are in order and correct for the kernels that are installed, No work to be done there as I had suspected.

Let's see if the package manager will work to remove those orphaned initrd.img files.
```

sudo apt-get autoremove

```

Else we remove them with 'dpkg' and try and fix the package manager afterward.
Then we see what it will take to get the now current -58 kernel installed.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-07-31
Hi Bashing-om,

autoremove did not work,
now I tried to remove by dpkg ..

> xy@xy:/boot$ sudo dpkg -r initrd.img-3.13.0-40-genericdpkg: warning: ignoring request to remove initrd.img-3.13.0-40-generic which isn't installed


I also tried the purge parameter.. it did not work
> xy@Shuttle:/xy$ sudo dpkg -p initrd.img-3.13.0-40-genericdpkg-query: package 'initrd.img-3.13.0-40-generic' is not available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


I also tried to get some info about this 
> xy@xy:/boot$ sudo dpkg-deb --info initrd.img-3.13.0-40-genericdpkg-deb: error: `initrd.img-3.13.0-40-generic' is not a debian format archive
xy@xy:/boot$ sudo dpkg --contents initrd.img-3.13.0-40-generic
dpkg-deb: error: `initrd.img-3.13.0-40-generic' is not a debian format archive


these are gzip files, says the PcManFM file browser..

I moved them to another directory, this worked..
> xy@xy:/boot$ sudo mv initrd.img-3.13.0-43-generic ~/Documents/Ubuntu
xy@xy:/boot$ sudo mv initrd.img-3.13.0-44-generic ~/Documents/Ubuntu
xy@xy:/boot$ sudo mv initrd.img-3.13.0-46-generic ~/Documents/Ubuntu
xy@xy:/boot$ sudo mv initrd.img-3.13.0-48-generic ~/Documents/Ubuntu

Now I have
> xy@xy:/boot$ ls -la
total 70065
drwxr-xr-x  6 root root     4096 Jul 31 22:58 .
drwxr-xr-x 23 root root     4096 Jul 21 23:10 ..
-rw-r--r--  1 root root  1164671 Mai  4 07:09 abi-3.13.0-52-generic
-rw-r--r--  1 root root  1164671 Mai 20 13:11 abi-3.13.0-53-generic
-rw-r--r--  1 root root   165762 Mai  4 07:09 config-3.13.0-52-generic
-rw-r--r--  1 root root   165762 Mai 20 13:11 config-3.13.0-53-generic
drwxr-xr-x  4 root root     1024 Jän  1  1970 efi
drwxr-xr-x  3 root root     4096 Jul 10 19:15 extlinux
drwxr-xr-x  5 root root     4096 Jul 16 01:37 grub
drwxr-xr-x  5 root root     4096 Mai  7  2014 grub.bak
-rw-r--r--  1 root root 19204935 Mai 12 18:03 initrd.img-3.13.0-52-generic
-rw-r--r--  1 root root 19204243 Jul 28 21:42 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389875 Mai  4 07:09 System.map-3.13.0-52-generic
-rw-------  1 root root  3390132 Mai 20 13:11 System.map-3.13.0-53-generic
-rw-------  1 root root  5818592 Mai  4 07:09 vmlinuz-3.13.0-52-generic
-rw-------  1 root root  5820504 Mai 12 18:03 vmlinuz-3.13.0-52-generic.efi.signed
-rw-------  1 root root  5821152 Mai 20 13:11 vmlinuz-3.13.0-53-generic
-rw-------  1 root root  5823064 Mai 23 13:50 vmlinuz-3.13.0-53-generic.efi.signed


---

### Post by Bashing-om on 2015-07-31
istvan5; K

Are you able now to boot up ?

What returns now :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
What has the system set to boot ?
```

ls -al /
ls -al /boot

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
hi !

Yes I am able to boot up, my system works.
The updates do nothing.

In "software & updates", i have activated these onces:
- important updates (trusty-security)
- recommended updates (trusty-updates)

So i don't have activated this 2 :
- pre-released updates (trusty-proposed)
- unsupported updates (trusty-backports)


> 
xy@xy:~$ sudo apt-get update
[sudo] password for xy: 
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty InRelease
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty Release.gpg                            
Get:1 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty Release                                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:2 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates Release [63,5 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/main Sources                           
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/restricted i386 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/universe Translation-en                
Get:3 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/universe amd64 Packages [301 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:4 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/main amd64 Packages [598 kB] 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:5 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [11,8 kB]
Get:6 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [12,0 kB]
Get:7 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/universe i386 Packages [302 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Get:8 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/main i386 Packages [579 kB]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Get:9 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/restricted i386 Packages [11,8 kB]
Get:10 [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12,1 kB]
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) trusty/universe Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 1.892 kB in 8s (212 kB/s)                                              
Reading package lists... Done


> 
xy@xy:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

xy@xy:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.






> xy@xy:~$ ls -al /
total 108
drwxr-xr-x  23 root root  4096 Jul 21 23:10 .
drwxr-xr-x  23 root root  4096 Jul 21 23:10 ..
drwxr-xr-x   2 root root  4096 Jul 30 23:15 bin
drwxr-xr-x   6 root root  4096 Jul 31 22:58 boot
drwxr-xr-x   2 root root  4096 Aug 30  2013 cdrom
drwxr-xr-x  15 root root  4280 Aug  2 17:24 dev
drwxr-xr-x 156 root root 12288 Aug  2 17:31 etc
-rwxr-xr-x   1 root root   427 Jun  3  2014 fstrim
drwxr-xr-x   4 root root  4096 Mär 30 07:56 home
drwxr-xr-x  23 root root  4096 Feb 28 01:02 lib
drwxr-xr-x   2 root root  4096 Feb 28 01:02 lib64
drwx------   2 root root 16384 Aug 30  2013 lost+found
drwxr-xr-x   7 root root  4096 Jun 20 20:32 media
drwxr-xr-x   4 root root  4096 Sep  3  2013 mnt
drwxr-xr-x   5 root root  4096 Jul 10 19:51 opt
dr-xr-xr-x 186 root root     0 Aug  2  2015 proc
drwx------  20 root root  4096 Jul 21 23:09 root
drwxr-xr-x  32 root root  1020 Aug  2 17:31 run
drwxr-xr-x   2 root root 12288 Jul 30 23:15 sbin
drwxr-xr-x   2 root root  4096 Apr 23  2013 srv
dr-xr-xr-x  13 root root     0 Aug  2  2015 sys
drwxrwxrwt   7 root root  4096 Aug  2 17:34 tmp
drwxr-xr-x  10 root root  4096 Feb  1 21:18 usr
drwxr-xr-x  13 root root  4096 Okt 25  2013 var
-rw-r--r--   1 root root     0 Jul 21 23:10 xx

xy@xy:~$ ls -al /boot
total 70065
drwxr-xr-x  6 root root     4096 Jul 31 22:58 .
drwxr-xr-x 23 root root     4096 Jul 21 23:10 ..
-rw-r--r--  1 root root  1164671 Mai  4 07:09 abi-3.13.0-52-generic
-rw-r--r--  1 root root  1164671 Mai 20 13:11 abi-3.13.0-53-generic
-rw-r--r--  1 root root   165762 Mai  4 07:09 config-3.13.0-52-generic
-rw-r--r--  1 root root   165762 Mai 20 13:11 config-3.13.0-53-generic
drwxr-xr-x  4 root root     1024 Jän  1  1970 efi
drwxr-xr-x  3 root root     4096 Jul 10 19:15 extlinux
drwxr-xr-x  5 root root     4096 Jul 16 01:37 grub
drwxr-xr-x  5 root root     4096 Mai  7  2014 grub.bak
-rw-r--r--  1 root root 19204935 Mai 12 18:03 initrd.img-3.13.0-52-generic
-rw-r--r--  1 root root 19204243 Jul 28 21:42 initrd.img-3.13.0-53-generic
-rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3389875 Mai  4 07:09 System.map-3.13.0-52-generic
-rw-------  1 root root  3390132 Mai 20 13:11 System.map-3.13.0-53-generic
-rw-------  1 root root  5818592 Mai  4 07:09 vmlinuz-3.13.0-52-generic
-rw-------  1 root root  5820504 Mai 12 18:03 vmlinuz-3.13.0-52-generic.efi.signed
-rw-------  1 root root  5821152 Mai 20 13:11 vmlinuz-3.13.0-53-generic
-rw-------  1 root root  5823064 Mai 23 13:50 vmlinuz-3.13.0-53-generic.efi.signed





---

### Post by Bashing-om on 2015-08-02
istvan5; Ouch ;

This is a new one on me. In the '/' directory there is no directive on the kernels to boot ! I have never ran across this situation.
For reference my output showing the booting kernels:
```

sysop@1404mini:~$ ls -al /
total 108
drwxr-xr-x  25 root root  4096 Jul 30 11:10 .
drwxr-xr-x  25 root root  4096 Jul 30 11:10 ..
drwxr-xr-x   2 root root  4096 Jul 29 11:44 bin
drwxr-xr-x   4 root root  4096 Jul 30 11:11 boot
drwxr-xr-x  14 root root  4360 Aug  2 10:50 dev
drwxr-xr-x  98 root root 12288 Aug  2 10:51 etc
-rw-r--r--   1 root root     0 Jul 18  2013 forcefsdk
drwxr-xr-x   5 root root  4096 Jun  9  2014 grub
drwxr-xr-x   4 root root  4096 May 19  2013 home
lrwxrwxrwx   1 root root    [color=green]33 Jul 30 11:10 initrd.img -> boot/initrd.img-3.13.0-61-generic[/color]
lrwxrwxrwx   1 root root    [color=green]33 Jul 28 13:32 initrd.img.old -> boot/initrd.img-3.13.0-59-generic[/color]
drwxr-xr-x  22 root root  4096 Jul  6  2014 lib
drwxr-xr-x   2 root root  4096 Feb 27 10:31 lib64
drwx------   2 root root 16384 May 19  2013 lost+found
drwxr-xr-x   3 root root  4096 May 19  2013 media
drwxr-xr-x  11 root root  4096 Feb 19 12:51 mnt
drwxr-xr-x   3 root root  4096 May 19  2013 opt
dr-xr-xr-x 151 root root     0 Aug  2 10:49 proc
drwx------   7 root root  4096 May 20  2013 root
drwxr-xr-x  17 root root   520 Aug  2 10:54 run
drwxr-xr-x   2 root root 12288 Jul 29 11:44 sbin
drwxr-xr-x   2 root root  4096 May 19  2013 srv
dr-xr-xr-x  13 root root     0 Aug  2 10:49 sys
drwxr-xr-x   2 root root  4096 Mar 31  2014 test
drwxrwxrwt   6 root root   180 Aug  2 11:17 tmp
drwxr-xr-x  10 root root  4096 May 19  2013 usr
drwxr-xr-x  13 root root  4096 Mar 13  2014 var
lrwxrwxrwx   1 root root    [color=green]30 Jul 30 11:10 vmlinuz -> boot/vmlinuz-3.13.0-61-generic[/color]
lrwxrwxrwx   1 root root    [color=green]30 Jul 28 13:32 vmlinuz.old -> boot/vmlinuz-3.13.0-59-generic[/color]
drwxr-xr-x   2 root root  4096 Mar 31  2014 work
sysop@1404mini:~$

```

As you can see the -61 updated kernel is available BUT, you remain on the old old -53 kernel. Yet the package manager seems in a happy state. So, the question is why ? When we know it is a falsehood.
Is this control package present on your system ?
```

dpkg -l linux-generic

```

If the kernel control file is installed, then ->
Let's see if grub can fix this issue:
```

sudo update-grub

```

[INDENT][INDENT]we know the issue
[INDENT][INDENT][INDENT]now it is an interesting puzzle
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
this 
> 
[FONT=courier new]xy@xy:~$ dpkg -l linux-generic[/FONT]
[FONT=courier new]dpkg-query: no packages found matching linux-generic[/FONT]

Then I installed,
> [FONT=courier new]xy@xy:~$ sudo apt-get install linux-generic[/FONT][FONT=courier new][sudo] password for xy: [/FONT]
[FONT=courier new]Reading package lists... Done[/FONT]
[FONT=courier new]Building dependency tree       [/FONT]
[FONT=courier new]Reading state information... Done[/FONT]
[FONT=courier new]The following extra packages will be installed:[/FONT]
[FONT=courier new]  linux-headers-3.13.0-61 linux-headers-3.13.0-61-generic[/FONT]
[FONT=courier new]  linux-headers-generic linux-image-3.13.0-61-generic[/FONT]
[FONT=courier new]  linux-image-extra-3.13.0-61-generic linux-image-generic[/FONT]
[FONT=courier new]Suggested packages:[/FONT]
[FONT=courier new]  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools[/FONT]
[FONT=courier new]The following NEW packages will be installed:[/FONT]
[FONT=courier new]  linux-generic linux-headers-3.13.0-61 linux-headers-3.13.0-61-generic[/FONT]
[FONT=courier new]  linux-headers-generic linux-image-3.13.0-61-generic[/FONT]
[FONT=courier new]  linux-image-extra-3.13.0-61-generic linux-image-generic[/FONT]
[FONT=courier new]0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=courier new]Need to get 61,5 MB of archives.[/FONT]
[FONT=courier new]After this operation, 271 MB of additional disk space will be used.[/FONT]
[FONT=courier new]Do you want to continue? [Y/n] y[/FONT]

then I get a lot of stuff, I think I don't need now the "[COLOR=#000000][FONT=Ubuntu Mono]sudo update-grub" ([/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]see red line[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono])
[/FONT][/COLOR]
> 
[FONT=courier new]Get:1 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-image-3.13.0-61-generic amd64 3.13.0-61.100 [15,2 MB][/FONT]
[FONT=courier new]Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-image-extra-3.13.0-61-generic amd64 3.13.0-61.100 [36,7 MB][/FONT]
[FONT=courier new]Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-image-generic amd64 3.13.0.61.68 [2.246 B][/FONT]
[FONT=courier new]Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-3.13.0-61 all 3.13.0-61.100 [8.885 kB][/FONT]
[FONT=courier new]Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-3.13.0-61-generic amd64 3.13.0-61.100 [697 kB][/FONT]
[FONT=courier new]Get:6 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-headers-generic amd64 3.13.0.61.68 [2.226 B][/FONT]
[FONT=courier new]Get:7 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-generic amd64 3.13.0.61.68 [1.788 B][/FONT]
[FONT=courier new]Fetched 61,5 MB in 26s (2.361 kB/s)                                            [/FONT]
[FONT=courier new]Selecting previously unselected package linux-image-3.13.0-61-generic.[/FONT]
[FONT=courier new](Reading database ... 205054 files and directories currently installed.)[/FONT]
[FONT=courier new]Preparing to unpack .../linux-image-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...[/FONT]
[FONT=courier new]Done.[/FONT]
[FONT=courier new]Unpacking linux-image-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-image-extra-3.13.0-61-generic.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-image-extra-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...[/FONT]
[FONT=courier new]Unpacking linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-image-generic.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-image-generic_3.13.0.61.68_amd64.deb ...[/FONT]
[FONT=courier new]Unpacking linux-image-generic (3.13.0.61.68) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-headers-3.13.0-61.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-headers-3.13.0-61_3.13.0-61.100_all.deb ...[/FONT]
[FONT=courier new]Unpacking linux-headers-3.13.0-61 (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-headers-3.13.0-61-generic.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-headers-3.13.0-61-generic_3.13.0-61.100_amd64.deb ...[/FONT]
[FONT=courier new]Unpacking linux-headers-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-headers-generic.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-headers-generic_3.13.0.61.68_amd64.deb ...[/FONT]
[FONT=courier new]Unpacking linux-headers-generic (3.13.0.61.68) ...[/FONT]
[FONT=courier new]Selecting previously unselected package linux-generic.[/FONT]
[FONT=courier new]Preparing to unpack .../linux-generic_3.13.0.61.68_amd64.deb ...[/FONT]
[FONT=courier new]Unpacking linux-generic (3.13.0.61.68) ...[/FONT]
[FONT=courier new]Setting up linux-image-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Running depmod.[/FONT]
[FONT=courier new]update-initramfs: deferring update (hook will be called later)[/FONT]
[FONT=courier new]Examining /etc/kernel/postinst.d.[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]update-initramfs: Generating /boot/initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]P: Checking for EXTLINUX directory... found.[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-61-generic...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-53-generic.efi.signed...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-53-generic...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-52-generic.efi.signed...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-52-generic...[/FONT]
[FONT=courier new]P: Updating /boot/extlinux/linux.cfg...[/FONT]
[FONT=courier new]P: Installing debian theme... done.[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[COLOR=#ff0000][FONT=courier new]Generating grub configuration file ...[/FONT][/COLOR]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-53-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-53-generic[/FONT]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-52-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-52-generic[/FONT]
[FONT=courier new]Found Windows Boot Manager on /dev/sda3@/EFI/Microsoft/Boot/bootmgfw.efi[/FONT]
[FONT=courier new]Adding boot menu entry for EFI firmware configuration[/FONT]
[FONT=courier new]done[/FONT]
[FONT=courier new]Setting up linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]update-initramfs: Generating /boot/initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]P: Checking for EXTLINUX directory... found.[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-61-generic...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-53-generic.efi.signed...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-53-generic...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-52-generic.efi.signed...[/FONT]
[FONT=courier new]P: Writing config for /boot/vmlinuz-3.13.0-52-generic...[/FONT]
[FONT=courier new]P: Installing debian theme... done.[/FONT]
[FONT=courier new]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]Generating grub configuration file ...[/FONT]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-53-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-53-generic[/FONT]
[FONT=courier new]Found linux image: /boot/vmlinuz-3.13.0-52-generic[/FONT]
[FONT=courier new]Found initrd image: /boot/initrd.img-3.13.0-52-generic[/FONT]
[FONT=courier new]Found Windows Boot Manager on /dev/sda3@/EFI/Microsoft/Boot/bootmgfw.efi[/FONT]
[FONT=courier new]Adding boot menu entry for EFI firmware configuration[/FONT]
[FONT=courier new]done[/FONT]
[FONT=courier new]Setting up linux-image-generic (3.13.0.61.68) ...[/FONT]
[FONT=courier new]Setting up linux-headers-3.13.0-61 (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Setting up linux-headers-3.13.0-61-generic (3.13.0-61.100) ...[/FONT]
[FONT=courier new]Setting up linux-headers-generic (3.13.0.61.68) ...[/FONT]
[FONT=courier new]Setting up linux-generic (3.13.0.61.68) ...[/FONT]





now I have 
> 
[FONT=courier new]xy@xy:~$ ls -al /[/FONT]
[FONT=courier new]total 108[/FONT]
[FONT=courier new]drwxr-xr-x  23 root root  4096 Aug  2 19:47 .[/FONT]
[FONT=courier new]drwxr-xr-x  23 root root  4096 Aug  2 19:47 ..[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Jul 30 23:15 bin[/FONT]
[FONT=courier new]drwxr-xr-x   6 root root  4096 Aug  2 19:48 boot[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Aug 30  2013 cdrom[/FONT]
[FONT=courier new]drwxr-xr-x  15 root root  4320 Aug  2 19:48 dev[/FONT]
[FONT=courier new]drwxr-xr-x 156 root root 12288 Aug  2 19:48 etc[/FONT]
[FONT=courier new]-rwxr-xr-x   1 root root   427 Jun  3  2014 fstrim[/FONT]
[FONT=courier new]drwxr-xr-x   4 root root  4096 Mär 30 07:56 home[/FONT]
[FONT=courier new]lrwxrwxrwx   1 root root    33 Aug  2 19:47 initrd.img -> boot/initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]drwxr-xr-x  23 root root  4096 Feb 28 01:02 lib[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Feb 28 01:02 lib64[/FONT]
[FONT=courier new]drwx------   2 root root 16384 Aug 30  2013 lost+found[/FONT]
[FONT=courier new]drwxr-xr-x   7 root root  4096 Jun 20 20:32 media[/FONT]
[FONT=courier new]drwxr-xr-x   4 root root  4096 Sep  3  2013 mnt[/FONT]
[FONT=courier new]drwxr-xr-x   5 root root  4096 Jul 10 19:51 opt[/FONT]
[FONT=courier new]dr-xr-xr-x 195 root root     0 Aug  2 19:23 proc[/FONT]
[FONT=courier new]drwx------  20 root root  4096 Jul 21 23:09 root[/FONT]
[FONT=courier new]drwxr-xr-x  32 root root  1080 Aug  2 19:48 run[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root 12288 Jul 30 23:15 sbin[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Apr 23  2013 srv[/FONT]
[FONT=courier new]dr-xr-xr-x  13 root root     0 Aug  2 19:23 sys[/FONT]
[FONT=courier new]drwxrwxrwt  10 root root  4096 Aug  2 19:49 tmp[/FONT]
[FONT=courier new]drwxr-xr-x  10 root root  4096 Feb  1 21:18 usr[/FONT]
[FONT=courier new]drwxr-xr-x  13 root root  4096 Okt 25  2013 var[/FONT]
[FONT=courier new]lrwxrwxrwx   1 root root    30 Aug  2 19:47 vmlinuz -> boot/vmlinuz-3.13.0-61-generic[/FONT]
[FONT=courier new]-rw-r--r--   1 root root     0 Jul 21 23:10 xx[/FONT]



and have 
> 
[FONT=courier new]xy@xy:~$ ls -al /boot[/FONT]
[FONT=courier new]total 99133[/FONT]
[FONT=courier new]drwxr-xr-x  6 root root     4096 Aug  2 19:48 .[/FONT]
[FONT=courier new]drwxr-xr-x 23 root root     4096 Aug  2 19:47 ..[/FONT]
[FONT=courier new]-rw-r--r--  1 root root  1164671 Mai  4 07:09 abi-3.13.0-52-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root  1164671 Mai 20 13:11 abi-3.13.0-53-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root  1165129 Jul 29 14:35 abi-3.13.0-61-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   165762 Mai  4 07:09 config-3.13.0-52-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   165762 Mai 20 13:11 config-3.13.0-53-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   165763 Jul 29 14:35 config-3.13.0-61-generic[/FONT]
[FONT=courier new]drwxr-xr-x  4 root root     1024 Jän  1  1970 efi[/FONT]
[FONT=courier new]drwxr-xr-x  3 root root     4096 Aug  2 19:48 extlinux[/FONT]
[FONT=courier new]drwxr-xr-x  5 root root     4096 Aug  2 19:48 grub[/FONT]
[FONT=courier new]drwxr-xr-x  5 root root     4096 Mai  7  2014 grub.bak[/FONT]
[FONT=courier new]-rw-r--r--  1 root root 19204935 Mai 12 18:03 initrd.img-3.13.0-52-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root 19204243 Jul 28 21:42 initrd.img-3.13.0-53-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root 19209668 Aug  2 19:48 initrd.img-3.13.0-61-generic[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   176500 Mär 12  2014 memtest86+.bin[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   178176 Mär 12  2014 memtest86+.elf[/FONT]
[FONT=courier new]-rw-r--r--  1 root root   178680 Mär 12  2014 memtest86+_multiboot.bin[/FONT]
[FONT=courier new]-rw-------  1 root root  3389875 Mai  4 07:09 System.map-3.13.0-52-generic[/FONT]
[FONT=courier new]-rw-------  1 root root  3390132 Mai 20 13:11 System.map-3.13.0-53-generic[/FONT]
[FONT=courier new]-rw-------  1 root root  3391819 Jul 29 14:35 System.map-3.13.0-61-generic[/FONT]
[FONT=courier new]-rw-------  1 root root  5818592 Mai  4 07:09 vmlinuz-3.13.0-52-generic[/FONT]
[FONT=courier new]-rw-------  1 root root  5820504 Mai 12 18:03 vmlinuz-3.13.0-52-generic.efi.signed[/FONT]
[FONT=courier new]-rw-------  1 root root  5821152 Mai 20 13:11 vmlinuz-3.13.0-53-generic[/FONT]
[FONT=courier new]-rw-------  1 root root  5823064 Mai 23 13:50 vmlinuz-3.13.0-53-generic.efi.signed[/FONT]
[FONT=courier new]-rw-------  1 root root  5822208 Jul 29 14:35 vmlinuz-3.13.0-61-generic[/FONT]


---

### Post by istvan5 on 2015-08-02
Now, after installing -61 , I shut down the PC and started again,
Grub Menu has -61 in it (I watch "advanced options"), so I could
start with -61 

now, "uname -r" says

> [FONT=verdana]xy@xy:~$ uname -r[/FONT][FONT=verdana]3.13.0-61-generic[/FONT]


yeah. :-)

Thank you very much for your time & help

---

### Post by Bashing-om on 2015-08-02
istvan5; Yeah !

Looking much better. I can live with that ... 
But I would be the better satisfied if the backup kernel were available in the '/' directory.
If you are comfortable, we can await the next kernel upgrade and I do expect the system to do the correct thing. OR we can make up the links to the -53 kernel .

Presently, what kernel are you booting after a reboot ?
```

uname -r

```

[INDENT][INDENT]this just maybe a done deal 
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
I also cleaned, I have a batch script, processing following commands
> 
[FONT=trebuchet ms]sudo apt-get clean[/FONT]
[FONT=trebuchet ms]sudo apt-get autoclean[/FONT]
[FONT=trebuchet ms]sudo apt-get autoremove[/FONT]
[FONT=trebuchet ms]sudo deborphan | xargs sudo apt-get -y remove --purge[/FONT]


and did this 
> 
[FONT=trebuchet ms]reading package lists... Done[/FONT]
[FONT=trebuchet ms]Building dependency tree       [/FONT]
[FONT=trebuchet ms]Reading state information... Done[/FONT]
[FONT=trebuchet ms]Reading package lists... Done[/FONT]
[FONT=trebuchet ms]Building dependency tree       [/FONT]
[FONT=trebuchet ms]Reading state information... Done[/FONT]
[FONT=trebuchet ms]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=trebuchet ms]Reading package lists... Done[/FONT]
[FONT=trebuchet ms]Building dependency tree       [/FONT]
[FONT=trebuchet ms]Reading state information... Done[/FONT]
[FONT=trebuchet ms]The following packages will be REMOVED:[/FONT]
[FONT=trebuchet ms]  libkdb5-7* libkeybinder-3.0-0*[/FONT]
[FONT=trebuchet ms]0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.[/FONT]
[FONT=trebuchet ms]After this operation, 241 kB disk space will be freed.[/FONT]
[FONT=trebuchet ms](Reading database ... 234702 files and directories currently installed.)[/FONT]
[FONT=trebuchet ms]Removing libkdb5-7:amd64 (1.12+dfsg-2ubuntu5.1) ...[/FONT]
[FONT=trebuchet ms]Purging configuration files for libkdb5-7:amd64 (1.12+dfsg-2ubuntu5.1) ...[/FONT]
[FONT=trebuchet ms]Removing libkeybinder-3.0-0:amd64 (0.3.0-0ubuntu1) ...[/FONT]
[FONT=trebuchet ms]Purging configuration files for libkeybinder-3.0-0:amd64 (0.3.0-0ubuntu1) ...[/FONT]
[FONT=trebuchet ms]Processing triggers for libc-bin (2.19-0ubuntu6.6) ...[/FONT]


---

### Post by Bashing-om on 2015-08-02
istvan5; Yepper ;

I do believe we are home free. All looks good to me.

We can rest on our laurels and await the next kernel update with no problems, will not be a problem.

OR preventive maintenance is to provide the backup kernel - that presently is not required.
Your call.

[INDENT][INDENT]your system
[INDENT][INDENT][INDENT]watcha wanna do ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
here again, it is -61
> 
[FONT=courier new]xy@xy:~$ uname -r
3.13.0-61-generic[/FONT]


---

### Post by istvan5 on 2015-08-02
I want to do the preventive maintenance
how can I make the "links" to -53  ?
[COLOR=#000000]
[/COLOR]

---

### Post by Bashing-om on 2015-08-02
istvan5; K

We can do that/

> **istvan5 said:**
> I want to do the preventive maintenance
how can I make the "links" to -53  ?
[COLOR=#000000]
[/COLOR]

```

sudo ln -s /boot/vmlinuz-3.13.0-53-generic /vmlinuz.old
sudo update-grub

```

Reboot the system to the grub boot menu -> advanced options; is the -53 kernel now listed as a boot option ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
hi !

I did 
sudo ln -s /boot/vmlinuz-3.13.0-53-generic /vmlinuz.old
sudo update-grub


yes, -53 in under "advanced options",
and this is the output for ...

> 
[FONT=courier new]xy@xy:~$ ls -al /[/FONT]
[FONT=courier new]total 108[/FONT]
[FONT=courier new]drwxr-xr-x  23 root root  4096 Aug  2 21:24 .[/FONT]
[FONT=courier new]drwxr-xr-x  23 root root  4096 Aug  2 21:24 ..[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Jul 30 23:15 bin[/FONT]
[FONT=courier new]drwxr-xr-x   6 root root  4096 Aug  2 19:48 boot[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Aug 30  2013 cdrom[/FONT]
[FONT=courier new]drwxr-xr-x  15 root root  4280 Aug  2 21:27 dev[/FONT]
[FONT=courier new]drwxr-xr-x 156 root root 12288 Aug  2 21:27 etc[/FONT]
[FONT=courier new]-rwxr-xr-x   1 root root   427 Jun  3  2014 fstrim[/FONT]
[FONT=courier new]drwxr-xr-x   4 root root  4096 Mär 30 07:56 home[/FONT]
**[FONT=courier new]lrwxrwxrwx   1 root root    33 Aug  2 19:47 initrd.img -> boot/initrd.img-3.13.0-61-generic[/FONT]**
[FONT=courier new]drwxr-xr-x  23 root root  4096 Feb 28 01:02 lib[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Feb 28 01:02 lib64[/FONT]
[FONT=courier new]drwx------   2 root root 16384 Aug 30  2013 lost+found[/FONT]
[FONT=courier new]drwxr-xr-x   7 root root  4096 Jun 20 20:32 media[/FONT]
[FONT=courier new]drwxr-xr-x   4 root root  4096 Sep  3  2013 mnt[/FONT]
[FONT=courier new]drwxr-xr-x   5 root root  4096 Jul 10 19:51 opt[/FONT]
[FONT=courier new]dr-xr-xr-x 185 root root     0 Aug  2  2015 proc[/FONT]
[FONT=courier new]drwx------  20 root root  4096 Jul 21 23:09 root[/FONT]
[FONT=courier new]drwxr-xr-x  32 root root  1020 Aug  2 21:28 run[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root 12288 Jul 30 23:15 sbin[/FONT]
[FONT=courier new]drwxr-xr-x   2 root root  4096 Apr 23  2013 srv[/FONT]
[FONT=courier new]dr-xr-xr-x  13 root root     0 Aug  2  2015 sys[/FONT]
[FONT=courier new]drwxrwxrwt   6 root root  4096 Aug  2 21:29 tmp[/FONT]
[FONT=courier new]drwxr-xr-x  10 root root  4096 Feb  1 21:18 usr[/FONT]
[FONT=courier new]drwxr-xr-x  13 root root  4096 Okt 25  2013 var[/FONT]
**[FONT=courier new]lrwxrwxrwx   1 root root    30 Aug  2 19:47 vmlinuz -> boot/vmlinuz-3.13.0-61-generic[/FONT]**
**[FONT=courier new]lrwxrwxrwx   1 root root    31 Aug  2 21:24 vmlinuz.old -> /boot/vmlinuz-3.13.0-53-generic[/FONT]**
[FONT=courier new]-rw-r--r--   1 root root     0 Jul 21 23:10 xx[/FONT]


---

### Post by Bashing-om on 2015-08-02
istvan5; Looking better all the time.

OK;
```

sudo ln -s /boot/initrd.img-3.13.0-53-generic initrd.img.old
sudo update-grub

```

If you now select the -53 kernel in the grub boot menu, I do expect it to boot that -53 kernel.

And all should now be
[INDENT][INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by istvan5 on 2015-08-02
yes, as you expected, selecting -53 in grub menu, it is booting with -53 kernel

thxxxxx

---

### Post by yoshii on 2015-08-02
amazing tech support

---

### Post by Bashing-om on 2015-08-02
istvan5; Hey hey ....

Is the fat lady singing ?
If you are now as happy as the operating system appears to be:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and happy trails to you
[/INDENT][/INDENT]

@yoshi2; Yepper :)
> 
amazing tech support

Welcome to open source, where
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

