---
title: "The volume &quot;boot&quot; has only 0 bytes disk space remaining"
date: 2014-05-24
forum: General Help
---

### Post by lunaservant on 2014-05-24
Everytime I boot up my computer I get this error.  My understanding of computers in general is pretty advanced but I am new to linux so please explain anything that you are having me type into the terminal so I understand what it is I am typing.  Info on my computer can be found below.

```
inxi -Fxz
System:    Host: ridge-X550EA Kernel: 3.13.0-24-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: ASUSTeK model: X550EA version: 1.0 Bios: American Megatrends version: X550EA.206 date: 09/24/2013
CPU:       Quad core AMD A4-5000 APU with Radeon HD Graphics (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 11977 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 1500.00 MHz 4: 800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8330] bus-ID: 00:01.0 
           X.Org: 1.15.1 drivers: ati,fglrx (unloaded: fbdev,vesa,radeon,intel) Resolution: 1366x768@60.0hz 
           GLX Renderer: AMD Radeon HD 8330 GLX Version: 4.3.12798 - CPC 13.35.1005 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2 
           Card-2: Advanced Micro Devices [AMD/ATI] Device 9840 driver: snd_hda_intel bus-ID: 00:01.1 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-24-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 01:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (15.2% used) 1: id: /dev/sda model: HGST_HTS545050A7 size: 500.1GB 
Partition: ID: / size: 254G used: 71G (30%) fs: ext4 ID: /boot size: 237M used: 237M (100%) fs: ext2 
           ID: swap-1 size: 7.99GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 220 Uptime: 15 min Memory: 1058.8/7357.9MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 

```

```
ridge@ridge-X550EA:~$ sudo fdisk -l
[sudo] password for ridge: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x568814a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/ubuntu--vg-root: 479.5 GB, 479497027584 bytes
255 heads, 63 sectors/track, 58295 cylinders, total 936517632 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 7985 MB, 7985954816 bytes
255 heads, 63 sectors/track, 970 cylinders, total 15597568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```

```
ridge@ridge-X550EA:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  488386584 sda
   8        1     524288 sda1
   8        2     249856 sda2
   8        3  487610368 sda3
  11        0    4590208 sr0
 252        0  468258816 dm-0
 252        1    7798784 dm-1

```

according to the GParted partition manager the partitions have the following setup:

/dev/sda1 has file system fat32, mount point is /boot/efi, size is 512.00 MiB, used is 19.53 MiB, Flags is boot

/dev/sda2 has file system ext2, mount point is /boot, size is 244.00 MiB used is 244.00 MiB

/dev/sda3 has file system lvm2 pv, mount point is ubuntu-vg, size is 465.02 GiB, unused is 11.02 GiB, and Flags is lvm

there are 1.02 Mib unallocated

the above parititions are the default that were installed automatically when I installed ubuntu 14 about 2-3 weeks ago.  If you need any further info just ask.  THank you for your time and assistance.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Hellko, Welcome to the forum.

You know from this:
> 
/dev/sda2 has file system ext2, mount point is /boot, size is 244.00 MiB used is 244.00 MiB

Where the problem lies. The boot partition contains the code to boot the system as well as the operating kernels. Presently you have no operating headroom due to that partition being full.

With absolutely no headroom, I can see where removing unneeded files from /boot may be a challenge.

Let's try the easy direct way and see if the package manager will deal with this for us.
As of release 13.10 apt-get has the ability to remove old no-longer used kernels that reside primarily in the /boot partition.

What release are you running ? IF 13.10 and greater try this terminal command:
```

sudo apt-get autoremove

```
See: man apt-get in terminal for the manual's  entry - the 'q' key to quit and return to terminal.

Else, release 12.04 ? Will have to roll our sleeves up and get dirty.

Not a great big deal,
[INDENT][INDENT][INDENT]and can be done
[/INDENT][/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
I am using version 14.  The code did it's work but didn't clear any space.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Humm,

Should have !

OK. Let's take a direct look at things.
Post back - between code tags - the outputs of terminal commands:
```

df -h ## file usage, what and where
df -i ## inode usage. got to have the inodes to allocate files (pointers)
du -h --max-depth=1 | sort -hr ## for finding out which directories are using all your space..
sudo du -h --max-depth=1 /boot ## a closer look at /boot
ls -la /boot ## to list what is contained in the /boot directory
dpkg -l | grep linux- ## to see what is installed for booting kernels onto the system

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once the situation is determined, a direct action will ensue.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
```
ridge@ridge-X550EA:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  254G   71G  171G  30% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.6G   12K  3.6G   1% /dev
tmpfs                        736M  1.4M  735M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.6G  1.4M  3.6G   1% /run/shm
none                         100M   40K  100M   1% /run/user
/dev/sda2                    237M  237M     0 100% /boot
/dev/sda1                    511M   19M  493M   4% /boot/efi
/dev/sr0                     964M  964M     0 100% /media/ridge/Ubuntu 14.04 LTS
```

```
ridge@ridge-X550EA:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 16883712 220666 16663046    2% /
none                          941811      2   941809    1% /sys/fs/cgroup
udev                          939022    528   938494    1% /dev
tmpfs                         941811    589   941222    1% /run
none                          941811      4   941807    1% /run/lock
none                          941811     13   941798    1% /run/shm
none                          941811     26   941785    1% /run/user
/dev/sda2                      62496    567    61929    1% /boot
/dev/sda1                          0      0        0     - /boot/efi
/dev/sr0                           0      0        0     - /media/ridge/Ubuntu 14.04 LTS amd64

```

```
ridge@ridge-X550EA:~$ du -h --max-depth=1 | sort -hr
65G    .
28G    ./Videos
28G    ./.local
5.1G    ./Downloads
3.0G    ./Desktop
1.5G    ./.wine
246M    ./.cache
174M    ./.minecraft
42M    ./.config
37M    ./.mozilla
14M    ./.kde
1.6M    ./.Skype
964K    ./.adobe
664K    ./.gstreamer-0.10
532K    ./.gconf
436K    ./Pictures
352K    ./.macromedia
116K    ./Anki
84K    ./.java
84K    ./.compiz
52K    ./.FBReader
44K    ./.xine
36K    ./.pki
32K    ./.gnome
12K    ./.supertux2
12K    ./.gnome2
12K    ./Documents
12K    ./.dbus
4.0K    ./Templates
4.0K    ./Public
4.0K    ./Podcasts
4.0K    ./Music
4.0K    ./.gnome2_private
4.0K    ./Audiobooks
```

```
ridge@ridge-X550EA:~$ sudo du -h --max-depth=1 /boot
[sudo] password for ridge: 
16M    /boot/boot
12K    /boot/lost+found
7.5M    /boot/grub
19M    /boot/efi
175M    /boot/sources
5.0K    /boot/support
2.0K    /boot/upgrade
782K    /boot/extlinux
253M    /boot

```

```
ridge@ridge-X550EA:~$ ls -la /boot
total 36976
drwxr-xr-x 10 root root     1024 May 17 14:20 .
drwxr-xr-x 24 root root     4096 May 24 11:01 ..
-rw-r--r--  1 root root  1158016 May  2 20:30 abi-3.13.0-24-generic
-rw-r--r--  1 root root      122 Apr 11  2009 autorun.inf
-rw-r--r--  1 root root     1631 Apr 16 19:57 Autounattend.xml
drwxr-xr-x  4 root root     1024 May 17 14:20 boot
-rw-r--r--  1 root root   333257 Apr 11  2009 bootmgr
-rw-r--r--  1 root root   546792 Apr 11  2009 bootmgr.efi
-rw-r--r--  1 root root   165510 May  2 20:30 config-3.13.0-24-generic
drwxr-xr-x  4 root root     4096 Dec 31  1969 efi
drwxr-xr-x  3 root root     1024 May 17 11:51 extlinux
drwxr-xr-x  5 root root     1024 May  9 22:49 grub
-rw-r--r--  1 root root 19890633 May 15 06:45 initrd.img-3.13.0-24-generic
drwx------  2 root root    12288 May  9 22:12 lost+found
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-r--r--  1 root root   107992 Apr 11  2009 setup.exe
drwxr-xr-x 10 root root     1024 May 17 14:20 sources
drwxr-xr-x  4 root root     1024 May 17 14:20 support
-rw-------  1 root root  3372643 May  2 20:30 System.map-3.13.0-24-generic
-rw-r--r--  1 root root     5547 May 17 14:20 ubnpathl.txt
drwxr-xr-x  3 root root     1024 May 17 14:20 upgrade
-rw-------  1 root root  5776416 May  2 20:30 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5778328 May  9 22:48 vmlinuz-3.13.0-24-generic.efi.signed

```

```
ridge@ridge-X550EA:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.2                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.24.29                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                  3.13.0-24.47                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                  3.13.0.24.29                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.13.0-24-generic                  3.13.0-24.47                                        amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.24.29                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
rH  syslinux-themes-debian                                12-3                                                all          collection of boot loaders (theme metapackage)
rc  syslinux-themes-debian-wheezy                         12-3                                                all          collection of boot loaders (debian-wheezy theme)

```

---

### Post by Bashing-om on 2014-05-24
lunaservant; Well, well ...

What is it that you are trying to do here ?
> 
drwxr-xr-x  4 root root     1024 May 17 14:20 boot
drwxr-xr-x  3 root root     1024 May 17 11:51 extlinux
drwxr-xr-x 10 root root     1024 May 17 14:20 sources
drwxr-xr-x  4 root root     1024 May 17 14:20 support
-rw-r--r--  1 root root     5547 May 17 14:20 ubnpathl.txt
drwxr-xr-x  3 root root     1024 May 17 14:20 upgrade

 A standard /boot partition:
```

sysop@1310mini:~$ ls -la /boot
total 54160
drwxr-xr-x  4 root root     4096 May  5 18:23 .
drwxr-xr-x 24 root root     4096 May 13 18:24 ..
-rw-r--r--  1 root root  1007681 Mar 11 14:06 abi-3.11.0-19-generic
-rw-r--r--  1 root root  1008090 May  2 17:01 abi-3.11.0-20-generic
-rw-r--r--  1 root root   163258 Mar 11 14:06 config-3.11.0-19-generic
-rw-r--r--  1 root root   163258 May  2 17:01 config-3.11.0-20-generic
drwxr-xr-x  5 root root     4096 May 22 13:47 grub
drwxr-xr-x  4 root root     4096 Apr 25 14:10 grub_backup
-rw-r--r--  1 root root 17428733 Apr 12 17:25 initrd.img-3.11.0-19-generic
-rw-r--r--  1 root root 17429680 May  5 18:23 initrd.img-3.11.0-20-generic
-rw-r--r--  1 root root   176500 Jun 17  2013 memtest86+.bin
-rw-r--r--  1 root root   178680 Jun 17  2013 memtest86+_multiboot.bin
-rw-------  1 root root  3296414 Mar 11 14:06 System.map-3.11.0-19-generic
-rw-------  1 root root  3296680 May  2 17:01 System.map-3.11.0-20-generic
-rw-------  1 root root  5634416 Mar 11 14:06 vmlinuz-3.11.0-19-generic
-rw-------  1 root root  5634736 May  2 17:01 vmlinuz-3.11.0-20-generic
sysop@1310mini:~$ sudo du -h --max-depth=1 /boot
[sudo] password for sysop: 
6.4M    /boot/grub
4.3M    /boot/grub_backup
64M     /boot
sysop@1310mini:~$

```

Is it possible to move the extra-ordinary applications to some other place ?
Else: ya looking at having to (RE-)partition to accommodate the added applications.

[INDENT][INDENT]what to do oh,
[INDENT][INDENT][INDENT]what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
```
drwxr-xr-x  4 root root     1024 May 17 14:20 boot
drwxr-xr-x  3 root root     1024 May 17 11:51 extlinux
drwxr-xr-x 10 root root     1024 May 17 14:20 sources
drwxr-xr-x  4 root root     1024 May 17 14:20 support
-rw-r--r--  1 root root     5547 May 17 14:20 ubnpathl.txt
drwxr-xr-x  3 root root     1024 May 17 14:20 upgrade
```

I have no idea what that means, but based on the date that may have been from the time that I tried to change the partitions.  I was trying to take some of the main partition and reapportion it to the boot partion but had way too much difficulty.  I'm not sure if I ever reset the unapportioned section to the main partition or not.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Welp,

Now we are in a pickle !

I do not have 14.04 installed, nor do I run with the better GPT partitioning. Tough to say what is a good recommendation. Nor, do I have a clue what might have happened.

As it stands now is your system fully operational, (???). Maybe consider slowly moving these out of the /boot partition -one at a time - see what happens; doing a lot of reboots inbetween.

keep in mind that  "drwxr-xr-x  4 root root     1024 May 17 14:20 boot" might still be required to boot efi .

[INDENT][INDENT]The best thought I have
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
> **Bashing-om said:**
> lunaservant; Welp,

Now we are in a pickle !

I do not have 14.04 installed, nor do I run with the better GPT partitioning. Tough to say what is a good recommendation. Nor, do I have a clue what might have happened.

As it stands now is your system fully operational, (???). Maybe consider slowly moving these out of the /boot partition -one at a time - see what happens; doing a lot of reboots inbetween.

keep in mind that  "drwxr-xr-x  4 root root     1024 May 17 14:20 boot" might still be required to boot efi .
[INDENT][INDENT]The best thought I have
[/INDENT]
[/INDENT]



everything is fully operational I just worry that I'm going to try to update and something will go wrong.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Hey,

Until there is operating headroom in /boot - something is wrong !

Like I say, we can "mv" those extraneous stuff out of /boot to say a temporary directory in /home. See what results when rebooting. In the event there is a problem when files are "moved" we can then always place them back.

Would not hurt a thing at this time to look at what is being moved:
```

ls -la /boot/sources
ls -la /boot/support

```
for an instance.

Once we have some headroom, will run the updates and see that the package manager is happy.

[INDENT]takes time
[INDENT][INDENT][INDENT]but it ain't no big deal
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
EDIT: ignore this, I answered my own question

---

### Post by lunaservant on 2014-05-24
okay I thought this would be easy but it's not.  I can't even find the files I'm supposed to be moving.  I'm sorry for being a newb but I need more specific directions.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Hey,

Not a problem

Try like this.
```

mkdir ~/holding

``` so we have some place to store the files.

Now let's move a directory from /boot to ~/holding;
```

ls -la /boot/sources ## to see that it is there
sudo mv -R /boot/sources ~/holding/ ## moved
ls -la /boot/sources ## see that the directory has been moved out.
ls -la ~/holding ## to see that the directory has been moved to "/holding'

```

Now lets see what the space usage is:
```

df -h

```
Now if all looks good, reboot the machine and see what is.

Back up and looking good, repeat with 
```

sudo mv -R /boot/support ~/holding/

```

And see once more what the situation is.

[INDENT][INDENT]small steps
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
that seems to have done it.  I moved sources to holding as you said and it cleared a lot of space.  /dev/sda2 now has 69.82 MiB used and 174.18 MiB unused.  Thank you so very much for your assistance.

---

### Post by Bashing-om on 2014-05-24
lunaservant; Great, making progress.

Those were but the two larger ones,;
Continuing on, what is on 'boot'
show me please:
```

ls -la /boot/boot

```
I bet there is still a bunch we can get rid of.

[INDENT][INDENT]a long journey can begin with
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
output: 

> ridge@ridge-X550EA:~$ ls -la /boot/boot
total 4363
drwxr-xr-x 4 root root    1024 May 17 14:20 .
drwxr-xr-x 9 root root    1024 May 24 17:45 ..
-rw-r--r-- 1 root root  262144 Apr 11  2009 bcd
-rw-r--r-- 1 root root    1024 Apr 11  2009 bootfix.bin
-rw-r--r-- 1 root root 3170304 Apr 11  2009 boot.sdi
-rw-r--r-- 1 root root  116224 Apr 11  2009 bootsect.exe
drwxr-xr-x 2 root root    1024 May 17 14:20 en-us
-rw-r--r-- 1 root root    2048 Apr 11  2009 etfsboot.com
drwxr-xr-x 2 root root    1024 May 17 14:20 fonts
-rw-r--r-- 1 root root  481768 Apr 11  2009 memtest.efi
-rw-r--r-- 1 root root  405992 Apr 11  2009 memtest.exe


---

### Post by Bashing-om on 2014-05-24
lunaservant; Humm,

I see nothing there that relates to presently booting ubuntu, move it out of there too.
```

sudo mv -R /boot/boot ~/holding

```

Now do me an updated list, to see what else we can "move".
```

ls -la /boot

```

still
[INDENT][INDENT]stepp'n small
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
output: 

> ridge@ridge-X550EA:/$ ls -la /boot
total 36973
drwxr-xr-x  7 root root     1024 May 24 18:18 .
drwxr-xr-x 24 root root     4096 May 24 11:01 ..
-rw-r--r--  1 root root  1158016 May  2 20:30 abi-3.13.0-24-generic
-rw-r--r--  1 root root      122 Apr 11  2009 autorun.inf
-rw-r--r--  1 root root     1631 Apr 16 19:57 Autounattend.xml
-rw-r--r--  1 root root   333257 Apr 11  2009 bootmgr
-rw-r--r--  1 root root   546792 Apr 11  2009 bootmgr.efi
-rw-r--r--  1 root root   165510 May  2 20:30 config-3.13.0-24-generic
drwxr-xr-x  3 root root     4096 Dec 31  1969 efi
drwxr-xr-x  3 root root     1024 May 17 11:51 extlinux
drwxr-xr-x  5 root root     1024 May  9 22:49 grub
-rw-r--r--  1 root root 19890633 May 15 06:45 initrd.img-3.13.0-24-generic
drwx------  2 root root    12288 May  9 22:12 lost+found
-rw-r--r--  1 root root   176500 Mar 12 08:31 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12 08:31 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12 08:31 memtest86+_multiboot.bin
-rw-r--r--  1 root root   107992 Apr 11  2009 setup.exe
-rw-------  1 root root  3372643 May  2 20:30 System.map-3.13.0-24-generic
-rw-r--r--  1 root root     5547 May 17 14:20 ubnpathl.txt
drwxr-xr-x  3 root root     1024 May 17 14:20 upgrade
-rw-------  1 root root  5776416 May  2 20:30 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5778328 May  9 22:48 vmlinuz-3.13.0-24-generic.efi.signed


---

### Post by Bashing-om on 2014-05-24
lunaservant; OK;

So far so good !

Let's move 'upgrade'
```

sudo mv -R /boot/upgrade ~/holding

```

now next take a look at what is in 'lost+found'
```

ls -la /boot/lost+found

```
Bet that one is a gonner too.

What in the world is a Windows type file doing in an ubunt /boot directory ? any idea what "setup.exe" is ?

still a stepp'n

---

### Post by lunaservant on 2014-05-24
output: 

> ridge@ridge-X550EA:/$ sudo ls -la /boot/lost+found
total 13
drwx------ 2 root root 12288 May  9 22:12 .
drwxr-xr-x 6 root root  1024 May 24 18:38 ..


the fact that there is a windows type file is because I did something stupid and I was wondering if it had something to do with this issue to start with.  I tried to open a windows boot disk from inside of ubuntu (i was trying overwrite ubuntu with windows so i could then set up a windows/ubuntu dual boot for school, didn't work for obvious reasons lol)

---

### Post by Bashing-om on 2014-05-24
lunaservant; Hey,

All a process of learning, ya know now that Ubuntu is not Windows. OK, that do explain a lot.
lost+found serves no purpose remove it entirely:
```

sudo rm -R /boot/lost+found

```

next is 'extlinux' - never hear of that one either - but again I have not installed 14.04, so let's look.
```

ls -la /boot/extinux

```

getting close to  text editor time and see what those 'setup' files are as we approach that moment of truth.

[INDENT]aint 'buntu wonderfull, cleanup
[INDENT][INDENT][INDENT]and there is no paper work
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
> ridge@ridge-X550EA:/$ ls -la /boot/extlinux
total 57
drwxr-xr-x 3 root root  1024 May 17 11:51 .
drwxr-xr-x 5 root root  1024 May 24 19:10 ..
-rw-r--r-- 1 root root 20704 May 17 11:50 chain.c32
-rw-r--r-- 1 root root   243 May 17 11:51 extlinux.conf
-rw-r--r-- 1 root root  1098 May 17 11:50 linux.cfg
-rw-r--r-- 1 root root 26140 May 17 11:50 memdisk
-rw-r--r-- 1 root root   178 May 17 11:50 memdisk.cfg
-rw-r--r-- 1 root root   180 May 17 11:51 os-prober.cfg
drwxr-xr-x 3 root root  1024 May 17 11:51 themes


I really do like ubuntu.  got a problem?  fixed in a day and doesn't cost you a penny to fix it.  this comp came with windows 8 preinstalled and it worked for a while then I had 3 straight days of problems and all microsoft could say was "buy our premium help service."

---

### Post by Bashing-om on 2014-05-24
lunaservant; Welll..

Looks to be more of Windows doing for extlinux. let's move it out of the way too:
```

sudo mv -R /boot/extlinux ~/holding

```

Now fire up a text editor and look at:
```

gedit /boot/autorun.inf

``` as it is also a Windows file, move it to ~/holding.

Same same for  bootmgr, setup.exe, ubnpathl.txt.

That done, the moment of truth. run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
 Fingers crossed, all run clean.

And yeah ! ubuntu ! Open Source (FLOSS) operating system by choice -> if it's broke it is fixable !

[INDENT][INDENT]way to go
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
everything ran perfectly :)

---

### Post by Bashing-om on 2014-05-24
lunaservant; Outstanding indeed;

I take it this matter is now concluded, all is well in your ubuntu world.
Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.
 - top of post -> thread tools -

[INDENT][INDENT]it is all in the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by lunaservant on 2014-05-24
thx for the reminder and thank you very much for your help

---

### Post by Bashing-om on 2014-05-24
lunaservant; Hey,

Come back when you can stay longer, 

stay and help others ... making your contribution to what is ubuntu.

[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT]

---

