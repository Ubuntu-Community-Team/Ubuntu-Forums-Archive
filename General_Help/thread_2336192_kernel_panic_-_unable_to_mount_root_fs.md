---
title: "kernel panic - unable to mount root fs"
date: 2016-09-05
forum: General Help
---

### Post by xenon3 on 2016-09-05
After grub menu chosing normal boot I get;:  kernel  panic -  not syncing  vfs unable to mount root fs on unknown block . in terminal, boot stops at that point

During start up i get after logging the message the volume boot has only 0 bytes remaining. what does that mean and what can i do?

---

### Post by jimmy-frydkaer on 2016-09-05
You can free up some space by running:

```
sudo apt autoremove
```

---

### Post by Bashing-om on 2016-09-05
xenon3; Hey, hey ..

What release do you have installed ? 

Have you run a file system check/repair from a liveDVD ? Look'n possible that the superblock may be in an inconsistent state.
The simpler thing here is to see what the file system check reveals. 
Show what we are working with so we point 'fsck'  to the correct target:
```

sudo parted -l
sudo fdisk -lu

```

and we also consider the options
[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-09-05
I assume from this that you are probably using an LVM partitions, and/or an encrypted system both of which require a separate /boot partition which is created at installation for you.  Unfortunately that auto-created partition is much too small once extra kernels come along in normal upgrades.

As you are so short of space that autoremove command to remove any old, unused kernels will probably fail and we will need to get down and dirty using dpkg to find kernels installed and remove one or two of them.  We may then be able to use the autoremove command suggested by jimmy-frydkaer.

Start with command ```
dpkg -l linux-image*
``` and we can move on slowly from there.

---

### Post by xenon3 on 2016-09-05
Thanks! But I rather backup $HOME and rebuild.

Can it be because my separate boot partition (from encrypted installation) has zero bytes free space? I got a warning of this fact, last boot, the warning said I should clean up files, but I don´t know how. Tried: sudo apt-get autoremove, seem to have removed something but also exit with errorcode (1)

---

### Post by Bashing-om on 2016-09-05
xenon3; Sure;

Possible that you are attempting to boot with a kernel that is not fully installed .
What release is this ?

Can you boot to the grub boot menu and see what results when booting older kernels ?

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-05
> **Bashing-om said:**
> xenon3; Sure;

What release is this ?



The one with the booting problem is 14.04.03 LTS

Older kernels boot fine

> **ajgreeny said:**
> I assume from this that you are probably using an LVM partitions, and/or an encrypted system

Yes its an encrypted system which used to boot normally, can it be that because of the 0 bytes empty space boot partition that: After grub menu chosing normal boot I get:  kernel  panic -  not  syncing  vfs unable to mount root fs on unknown block . in terminal,  boot stops at that point?

---

### Post by ajgreeny on 2016-09-06
Are you saying that you can not even boot into Ubuntu at the moment?  I did not get that impression from your first post, but if that is your current position I am not sure what is the quickest and easiest action to take.

Wait for more answers from users who know more than I do if you can't boot to the OS.

---

### Post by xenon3 on 2016-09-06
> **ajgreeny said:**
> Are you saying that you can not even boot into Ubuntu at the moment?  I did not get that impression from your first post, but if that is your current position I am not sure what is the quickest and easiest action to take.

Wait for more answers from users who know more than I do if you can't boot to the OS.

I can only boot from an older version ubuntu in GRUB "ubuntu advanced options" would be nice to know for sure if the newest (default) version gives that KERNEL PANIC during boot because of the ubuntu upgrade update I did: Which only seems to have been done partially because of the now 0 bytes empty space on boot partition.

---

### Post by ajgreeny on 2016-09-06
If you are able to boot to the previous kernel then it would appear that the newest kernel version you have is the problem.

This could be simply due to the lack of space not allowing that new kernel to fully configure and the only way to know for sure is to do what I suggested in post #3 and try to remove some old kernels.

So please boot to the previous kernel that allows you to run Ubuntu and then use that command I showed ```
dpkg -l linux-image*
```  post back here the output you get and we can try to sort this out for you.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Bashing-om on 2016-09-06
xenon3; Well ...

Able to boot older kernels narrows things down a bunch .

OK, what kernels are installed, and what is the disk space usage ?
```

dpkg -l | grep linux-
ls -al /boot
df -h
df -i

```
to get an idea of what needs to be done.

[INDENT][INDENT]so far so good
[/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-06
> **Bashing-om said:**
> xenon3; Well ...

OK, what kernels are installed, and what is the disk space usage ?

...

to get an idea of what needs to be done.[INDENT][INDENT]so far so good
[/INDENT]
[/INDENT]



Why do you need to know all this stuff? :D

---

### Post by Bashing-om on 2016-09-06
xenon3; Hey .......

> **xenon3 said:**
> Why do you need to know all this stuff? :D

I do not need it, you do . that info to aid me in my thought process to aid you.

[INDENT][INDENT]one is only as good as the tools one works with
[/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-06
> **Bashing-om said:**
> xenon3; Hey .......



I do not need it, you do . that info to aid me in my thought process to aid you.
[INDENT][INDENT]one is only as good as the tools one works with
[/INDENT]
[/INDENT]


OK! Just tell me can I keep on using the older kernel as long I don't do the upgrade update? I think because of encrypted installation my limited space boot partition gets corrupted, i.e. the upgraded kernel in question gets corrupted, by an ubuntu upgrade update, since there is 0 bytes empty space in boot partition.

---

### Post by Bashing-om on 2016-09-06
xenon3l So ....

We look, see what is installed, what we can remove .. and what it takes to insure the latest kernel is fully installed .

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-06
> **Bashing-om said:**
> xenon3l So ....

We look, see what is installed, what we can remove .. and what it takes to insure the latest kernel is fully installed .[INDENT][INDENT]no step for a stepper
[/INDENT]
[/INDENT]


OK I do! I like you, you're funny, I will do the whole shebang of commands tomorrow


                                                             ...........................................................I'll be back

> **Bashing-om said:**
> xenon3l So ....

We look, see what is installed, what we can remove .. and what it takes to insure the latest kernel is fully installed .[INDENT][INDENT]no step for a stepper
[/INDENT]
[/INDENT]


```
kingdom@king-MS-7728:~$ dpkg -l | grep linus-
kingdom@king-MS-7728:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.68.50                                        i386         Complete Generic Linux kernel and headers
iU  linux-generic-lts-xenial                              4.4.0.36.26                                         i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-65                               3.19.0-65.73~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-65-generic                       3.19.0-65.73~14.04.1                                i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-68                               3.19.0-68.76~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-68-generic                       3.19.0-68.76~14.04.1                                i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-34                                4.4.0-34.53~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic                        4.4.0-34.53~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-36                                4.4.0-36.55~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic                        4.4.0-36.55~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.68.50                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-xenial                      4.4.0.36.26                                         i386         Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-65-generic                         3.19.0-65.73~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-66-generic                         3.19.0-66.74~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-68-generic                         3.19.0-68.76~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-34-generic                          4.4.0-34.53~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-36-generic                          4.4.0-36.55~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rH  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-65-generic                   3.19.0-65.73~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic                   3.19.0-66.74~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
iF  linux-image-extra-3.19.0-68-generic                   3.19.0-68.76~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic                    4.4.0-34.53~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-36-generic                    4.4.0-36.55~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.68.50                                        i386         Generic Linux kernel image
iU  linux-image-generic-lts-xenial                        4.4.0.36.26                                         i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-95.142                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
kingdom@king-MS-7728:~$ 
```

```
kingdom@king-MS-7728:~$ ls -al /boot
total 145643
drwxr-xr-x  4 root root     3072 sep  5 21:47 .
drwxr-xr-x 22 root root     4096 sep  5 21:47 ..
-rw-r--r--  1 root root  1269099 jun 30 02:54 abi-3.19.0-65-generic
-rw-r--r--  1 root root  1269146 aug 12 15:47 abi-3.19.0-68-generic
-rw-r--r--  1 root root  1237729 jul 27 21:53 abi-4.4.0-34-generic
-rw-r--r--  1 root root  1238066 aug 12 15:50 abi-4.4.0-36-generic
-rw-r--r--  1 root root   182091 jun 30 02:54 config-3.19.0-65-generic
-rw-r--r--  1 root root   182091 aug 12 15:47 config-3.19.0-68-generic
-rw-r--r--  1 root root   193127 jul 27 21:53 config-4.4.0-34-generic
-rw-r--r--  1 root root   193147 aug 12 15:50 config-4.4.0-36-generic
drwxr-xr-x  5 root root     1024 sep  5 21:47 grub
-rw-r--r--  1 root root 29710798 aug  6 12:07 initrd.img-3.19.0-65-generic
-rw-r--r--  1 root root 35634810 aug 31 07:28 initrd.img-3.19.0-68-generic
-rw-r--r--  1 root root 39159054 aug 24 17:36 initrd.img-4.4.0-34-generic
drwx------  2 root root    12288 jul 15 05:47 lost+found
-rw-r--r--  1 root root   176500 mrt 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 mrt 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 mrt 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2885787 jun 30 02:54 System.map-3.19.0-65-generic
-rw-------  1 root root  2885917 aug 12 15:47 System.map-3.19.0-68-generic
-rw-------  1 root root  3097534 jul 27 21:53 System.map-4.4.0-34-generic
-rw-------  1 root root  3098435 aug 12 15:50 System.map-4.4.0-36-generic
-rw-------  1 root root  6213008 jun 30 02:54 vmlinuz-3.19.0-65-generic
-rw-------  1 root root  6212400 aug 12 15:47 vmlinuz-3.19.0-68-generic
-rw-------  1 root root  6656608 jul 27 21:53 vmlinuz-4.4.0-34-generic
-rw-------  1 root root  6653760 aug 12 15:50 vmlinuz-4.4.0-36-generic
kingdom@king-MS-7728:~$
```

 ```
kingdom@king-MS-7728:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    4,0G  4,0K  4,0G   1% /dev
tmpfs                   808M  1,3M  807M   1% /run
/dev/dm-1                66G  6,5G   56G  11% /
none                    4,0K     0  4,0K   0% /sys/fs/cgroup
none                    5,0M     0  5,0M   0% /run/lock
none                    4,0G  1,5G  2,6G  36% /run/shm
none                    100M   40K  100M   1% /run/user
/dev/sda1               236M  151M   73M  68% /boot
/home/kingdom/.Private   66G  6,5G   56G  11% /home/kingdom
/dev/sdc1               3,8G  607M  3,2G  16% /media/kingdom/CANON_DC
/dev/sr0                4,3G  4,3G     0 100% /media/kingdom/LG_COMBI_RECORDER
/dev/sdb1               1,8T  1,1T  736G  60% /media/kingdom/Data
kingdom@king-MS-7728:~$ df -i
Filesystem                Inodes   IUsed     IFree IUse% Mounted on
udev                      194461     596    193865    1% /dev
tmpfs                     204271     649    203622    1% /run
/dev/dm-1                4349952  305248   4044704    8% /
none                      204271       2    204269    1% /sys/fs/cgroup
none                      204271       4    204267    1% /run/lock
none                      204271      10    204261    1% /run/shm
none                      204271      26    204245    1% /run/user
/dev/sda1                  62248     316     61932    1% /boot
/home/kingdom/.Private   4349952  305248   4044704    8% /home/kingdom
/dev/sdc1                      0       0         0     - /media/kingdom/CANON_DC
/dev/sr0                      16      16         0  100% /media/kingdom/LG_COMBI_RECORDER
/dev/sdb1              774914404 2927656 771986748    1% /media/kingdom/Data
kingdom@king-MS-7728:~$ 
```

are you now happy you fortune cookie boxing pinguin?

---

### Post by ian-weisser on 2016-09-07
> **ajgreeny said:**
> Unfortunately that auto-created partition is much too small once extra kernels come along in normal upgrades

Happily, that issue was fixed in 16.04. So it depends upon the OP's release.

---

### Post by ajgreeny on 2016-09-07
> **ian-weisser said:**
> Happily, that issue was fixed in 16.04. So it depends upon the OP's release.
Thanks Ian.

I had not caught up with that fact.

---

### Post by Bashing-om on 2016-09-07
xenon3; Welp;

As you can now see .. we have out work cut out for us .
> 
are you now happy you fortune cookie boxing pinguin?

Maybe not happy but sure occupied .. no devil's playground here .


OK, next is what kernel are you booting ?? and will continue to boot until we have this situation under control ?

show us :
```

uname -r

```
and also provide the output of :
```

dpkg -l | grep linux-

```
between code tags .. sure will help to have it formatted and in a better readable state:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]see what we can do
[INDENT][INDENT][INDENT]clean this mess up
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-09-07
ajgreeny; xenon3;

We are duplicating efforts . Working the same same:
[https://ubuntuforums.org/showthread.php?t=2336192&p=13541070#post13541070](https://ubuntuforums.org/showthread.php?t=2336192&p=13541070#post13541070)
should not these threads be merged ?

[INDENT]'buntu
[INDENT][INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2016-09-07
Yes, thanks Bashing-om; I just spotted this duplicate in another place.

@ xenon3
Please do not create duplicate threads on the same subject; it is confusing for all of us including you and dilutes our ability to answer your queries properly, as you've seen here.

Threads merged.

---

### Post by xenon3 on 2016-09-08
> **Bashing-om said:**
> xenon3l So ....

We look, see what is installed, what we can remove .. and what it takes to insure the latest kernel is fully installed .[INDENT][INDENT]no step for a stepper
[/INDENT]
[/INDENT]


I trust you, so I gave the info, but you do not reply anymore :(

EDIT: Oh sorry (there was another page) you gave me new assignments :D , I will do them Thursday night, thanks

> **Bashing-om said:**
> xenon3; Welp;

As you can now see .. we have out work cut out for us .

Maybe not happy but sure occupied .. no devil's playground here .


OK, next is what kernel are you booting ?? and will continue to boot until we have this situation under control ?

show us :
```

uname -r

```
and also provide the output of :
```

dpkg -l | grep linux-

```
between code tags .. sure will help to have it formatted and in a better readable state:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]see what we can do[INDENT][INDENT][INDENT]clean this mess up
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks I will do so as I said earlier, but please answer this question too (I asked before) will the older kernel be OK and stay OK? despite its on a 0 bytes empty space boot partition? Can I keep booting from that older kernel, as a kind of roll back?

> **ajgreeny said:**
> 

@ xenon3
Please do not create duplicate threads on the same subject; it is confusing for all of us including you and dilutes our ability to answer your queries properly, as you've seen here.

  

I made one for the 0 bytes empty space boot partition and one for the Kernel Panic, I thought at that moment it were separate issues, is that what you mean?

---

### Post by ajgreeny on 2016-09-08
> **xenon3 said:**
> I made one for the 0 bytes empty space boot partition and one for the Kernel Panic, I thought at that moment it were separate issues, is that what you mean?
Yes, that is what I did mean but I can see why you thought they may be different problems so don't worry about that.

The kernel panic may have been a result of an incomplete configuration of the latest kernel that yu were trying to boot, so if we can remove some of the old unwanted kernels and then fully configure the newest version all may be well again in your Ubuntu world.

The older kernel that you can still boot to should not be damaged in any way by what Bashing-om and I are suggesting you do, as long as we do not change it in way with the dpkg commands which will be needed; that is why we are asking for all the terminal output.  We need that information in order to ensure we do not do more damage to your system.

Stick with it and we'll get there!

---

### Post by xenon3 on 2016-09-09
> **Bashing-om said:**
> xenon3; Welp;

show us :
```

uname -r

```
and also provide the output of :
```

dpkg -l | grep linux-

```



```


kingdom@king-MS-7728:~$ rm -fr /home/kingdom/.cache/mozilla/firefox/
kingdom@king-MS-7728:~$ uname -r
4.4.0-34-generic
kingdom@king-MS-7728:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.68.50                                        i386         Complete Generic Linux kernel and headers
iU  linux-generic-lts-xenial                              4.4.0.36.26                                         i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-65                               3.19.0-65.73~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-65-generic                       3.19.0-65.73~14.04.1                                i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-68                               3.19.0-68.76~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-68-generic                       3.19.0-68.76~14.04.1                                i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-34                                4.4.0-34.53~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic                        4.4.0-34.53~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-36                                4.4.0-36.55~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic                        4.4.0-36.55~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.68.50                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-xenial                      4.4.0.36.26                                         i386         Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-65-generic                         3.19.0-65.73~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-66-generic                         3.19.0-66.74~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-68-generic                         3.19.0-68.76~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-34-generic                          4.4.0-34.53~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-36-generic                          4.4.0-36.55~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rH  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-65-generic                   3.19.0-65.73~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic                   3.19.0-66.74~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
iF  linux-image-extra-3.19.0-68-generic                   3.19.0-68.76~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic                    4.4.0-34.53~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-36-generic                    4.4.0-36.55~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.68.50                                        i386         Generic Linux kernel image
iU  linux-image-generic-lts-xenial                        4.4.0.36.26                                         i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-95.142                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
kingdom@king-MS-7728:~$ 


```

......................................................................difficult to say, always in motion, the future

---

### Post by Bashing-om on 2016-09-09
xenon3; Ho Kay !

Let's take a gentle poke at this .. see what bites back.
Remove all the old kernels and related support for them, leaving the 2 latest kernels, and get this system stable and updated.
We start with but one kernel;
So, what results:
```

sudo dpkg -P linux-image-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65
sudo dpkg -P linux-image-extra-3.19.0-65-generic

```
(vivid - EOL )
Depending on what happens and what the package manager reports is what we do next - hopefully remove the 3.19.0-68 kernel and the vivid HWE stack. Keeping in mind that 3.19.0-25-generic is staring us in the face, and might be a problem !

The good news is that this will not be as trying to accomplish as I had at 1st anticipated.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-09
> **Bashing-om said:**
> xenon3; Ho Kay !

Let's take a gentle poke at this .. see what bites back.[INDENT][INDENT]
we can do this
[/INDENT]
[/INDENT]


Will do next Sunday evening

.......................honey for the bees and I will be the reaper

> **Bashing-om said:**
> xenon3; Ho Kay !

Remove all the old kernels and related support for them, leaving the 2 latest kernels, and get this system stable and updated.



Will this free up space in the boot partition, or something?

............................a friend asks only for your time not your money

---

### Post by ajgreeny on 2016-09-10
> **xenon3 said:**
> Will this free up space in the boot partition, or something?

............................a friend asks only for your time not your money
Yes, that is what both Bashing-om and I are both trying to do.

Old kernels use space in your /boot partition but more than two kernels are not needed, (the current version and the previous version should remain), so we want to see exactly which kernel versions are installed, which version you are currently using, and then use dpkg to remove the unwanted versions and make some more space in /boot.

---

### Post by xenon3 on 2016-09-12
> **Bashing-om said:**
> xenon3; 

Let's take a gentle poke at this .. see what bites back.

```

sudo dpkg -P linux-image-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65
sudo dpkg -P linux-image-extra-3.19.0-65-generic

```



kingdom@king-MS-7728:~$ sudo dpkg -P linux-image-3.19.0-65-generic
[sudo] password for kingdom: 
Sorry, try again.
[sudo] password for kingdom: 
dpkg: dependency problems prevent removal of linux-image-3.19.0-65-generic:
 linux-image-extra-3.19.0-65-generic depends on linux-image-3.19.0-65-generic.

dpkg: error processing package linux-image-3.19.0-65-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.19.0-65-generic
kingdom@king-MS-7728:~$ 

...........................................the man or woman you desire feels the same about you

---

### Post by Bashing-om on 2016-09-12
xenon3; Humm ....

I wudda swore the order of operations was and is correct .. however !
Try as :
```

sudo dpkg -P linux-image-extra-3.19.0-65-generic
sudo dpkg -P linux-image-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65

```
where we attempt to remove that problematic linux-image-extra- component first .

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT]try something else
[INDENT][INDENT]( sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-12
> **Bashing-om said:**
> xenon3; Humm ....

I wudda swore the order of operations was and is correct ... 



should I do it in a TTY? CTRL + ALT + F1 (to F6) you are automatically root than, so have root privileges

I did it in a X-Session TERMINAL, so I could copy paste the commands :-o

maybe this needs root privileges, and it does not say that in TERMINAL errors

............................................never give up. you're not a failure if you don't give up

---

### Post by ian-weisser on 2016-09-12
Follow Bashing-om's instructions in an ordinary user-level Terminal window. 
The 'sudo' takes care of the admin permissions needed. You don't seems to have a permissions problem; don't get distracted.

Please post the complete output of all four commands. Just two is usually not enough.

---

### Post by xenon3 on 2016-09-12
> **Bashing-om said:**
> xenon3; Humm ....

I wudda swore the order of operations was and is correct .. however !
Try as :
```

sudo dpkg -P linux-image-extra-3.19.0-65-generic
sudo dpkg -P linux-image-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65-generic
sudo dpkg -P linux-headers-3.19.0-65

```
where we attempt to remove that problematic linux-image-extra- component first .
[INDENT][INDENT]if at 1st you do not succeed[INDENT][INDENT]try something else[INDENT][INDENT]( sky diving excepted )
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```


kingdom@king-MS-7728:~$ sudo dpkg -P linux-image-extra-3.19.0-65-generic
[sudo] password for kingdom: 
(Reading database ... 269180 files and directories currently installed.)
Removing linux-image-extra-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-68-generic
Found initrd image: /boot/initrd.img-3.19.0-68-generic
Found linux image: /boot/vmlinuz-3.19.0-65-generic
Found initrd image: /boot/initrd.img-3.19.0-65-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...
kingdom@king-MS-7728:~$ sudo dpkg -P linux-image-3.19.0-65-generic
(Reading database ... 264755 files and directories currently installed.)
Removing linux-image-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
dkms: removing: bbswitch 0.7 (3.19.0-65-generic) (i686)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.19.0-65-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: nvidia-367 367.44 (3.19.0-65-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-367
Version: 367.44
Kernel:  3.19.0-65-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_367.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-65-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-65-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-68-generic
Found initrd image: /boot/initrd.img-3.19.0-68-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-65-generic /boot/vmlinuz-3.19.0-65-generic
kingdom@king-MS-7728:~$ sudo dpkg -P linux-headers-3.19.0-65-generic
(Reading database ... 263786 files and directories currently installed.)
Removing linux-headers-3.19.0-65-generic (3.19.0-65.73~14.04.1) ...
kingdom@king-MS-7728:~$ sudo dpkg -P linux-headers-3.19.0-65
(Reading database ... 254543 files and directories currently installed.)
Removing linux-headers-3.19.0-65 (3.19.0-65.73~14.04.1) ...
kingdom@king-MS-7728:~$ lightdm stop --test-mode


```

............................you will marry your lover

---

### Post by ian-weisser on 2016-09-12
Well done!
That seems successful at clearing a bit of breathing room.

Next, try
```
sudo apt remove linux-generic-lts-vivid, linux-headers-generic-lts-vivid, linux-image-extra-3.19.0-25-generic, linux-headers-3.19.0-68-generic, linux-headers-3.19.0-68, linux-image-3.19.0-68-generic, linux-image-extra-3.19.0-68-generic
```

Let us know how that step goes.
As before, please show us the complete output.

---

### Post by xenon3 on 2016-09-12
> **ian-weisser said:**
> Well done!
That seems successful at clearing a bit of breathing room.

Next, try
```
sudo apt remove linux-generic-lts-vivid, linux-headers-generic-lts-vivid, linux-image-extra-3.19.0-25-generic, linux-headers-3.19.0-68-generic, linux-headers-3.19.0-68, linux-image-3.19.0-68-generic, linux-image-extra-3.19.0-68-generic
```

Let us know how that step goes.
As before, please show us the complete output.

```


kingdom@king-MS-7728:~$ sudo apt remove linux-generic-lts-vivid, linux-headers-generic-lts-vivid, linux-image-extra-3.19.0-25-generic, linux-headers-3.19.0-68-generic, linux-headers-3.19.0-68, linux-image-3.19.0-68-generic, linux-image-extra-3.19.0-68-generic
[sudo] password for kingdom: 
Sorry, try again.
[sudo] password for kingdom: 
Sorry, try again.
[sudo] password for kingdom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-generic-lts-vivid,
E: Unable to locate package linux-headers-generic-lts-vivid,
E: Unable to locate package linux-image-extra-3.19.0-25-generic,
E: Couldn't find any package by regex 'linux-image-extra-3.19.0-25-generic,'
E: Unable to locate package linux-headers-3.19.0-68-generic,
E: Couldn't find any package by regex 'linux-headers-3.19.0-68-generic,'
E: Unable to locate package linux-headers-3.19.0-68,
E: Couldn't find any package by regex 'linux-headers-3.19.0-68,'
E: Unable to locate package linux-image-3.19.0-68-generic,
E: Couldn't find any package by regex 'linux-image-3.19.0-68-generic,'
kingdom@king-MS-7728:~$ 


```

Thats what is on it now:

```


kingdom@king-MS-7728:~$ 
kingdom@king-MS-7728:~$ 
kingdom@king-MS-7728:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
iU  linux-generic-lts-vivid                               3.19.0.68.50                                        i386         Complete Generic Linux kernel and headers
iU  linux-generic-lts-xenial                              4.4.0.36.26                                         i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-68                               3.19.0-68.76~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-68-generic                       3.19.0-68.76~14.04.1                                i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-34                                4.4.0-34.53~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic                        4.4.0-34.53~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-36                                4.4.0-36.55~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic                        4.4.0-36.55~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-vivid                       3.19.0.68.50                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-xenial                      4.4.0.36.26                                         i386         Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-66-generic                         3.19.0-66.74~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-68-generic                         3.19.0-68.76~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-34-generic                          4.4.0-34.53~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
iF  linux-image-4.4.0-36-generic                          4.4.0-36.55~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rH  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic                   3.19.0-66.74~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
iF  linux-image-extra-3.19.0-68-generic                   3.19.0-68.76~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic                    4.4.0-34.53~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-extra-4.4.0-36-generic                    4.4.0-36.55~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
iU  linux-image-generic-lts-vivid                         3.19.0.68.50                                        i386         Generic Linux kernel image
iU  linux-image-generic-lts-xenial                        4.4.0.36.26                                         i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-95.142                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
kingdom@king-MS-7728:~$ 


```

---

### Post by Bashing-om on 2016-09-12
xenon3; Hey !

A skip in the thought process .. lost in translation.
Try the command sequence  with out the comas :
```

sudo apt remove linux-generic-lts-vivid linux-headers-generic-lts-vivid linux-image-extra-3.19.0-25-generic linux-headers-3.19.0-68-generic linux-image-3.19.0-68-generic  linux-image-extra-3.19.0-68-generic

```

Doing this all at one throw .

[INDENT][INDENT]I betcha
[/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-13
> **Bashing-om said:**
> xenon3; Hey !

A skip in the thought process .. lost in translation.
Try the command sequence  with out the comas :
```

sudo apt remove linux-generic-lts-vivid linux-headers-generic-lts-vivid linux-image-extra-3.19.0-25-generic linux-headers-3.19.0-68-generic linux-image-3.19.0-68-generic  linux-image-extra-3.19.0-68-generic

```

Doing this all at one throw .
[INDENT][INDENT]I betcha
[/INDENT]
[/INDENT]


```


kingdom@king-MS-7728:~$ sudo apt remove linux-generic-lts-vivid linux-headers-generic-lts-vivid linux-image-extra-3.19.0-25-generic linux-headers-3.19.0-68-generic linux-image-3.19.0-68-generic  linux-image-extra-3.19.0-68-generic
[sudo] password for kingdom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  linux-headers-3.19.0-68
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  linux-generic-lts-vivid linux-headers-3.19.0-68-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-68-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-68-generic
  linux-image-generic-lts-vivid
0 upgraded, 0 newly installed, 7 to remove and 22 not upgraded.
8 not fully installed or removed.
After this operation, 288 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 238719 files and directories currently installed.)
Removing linux-generic-lts-vivid (3.19.0.68.50) ...
Removing linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-25-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Error! Your kernel headers for kernel 3.19.0-25-generic cannot be found.
Please install the linux-headers-3.19.0-25-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.19.0-25-generic cannot be found.
Please install the linux-headers-3.19.0-25-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
grep: /boot/config-3.19.0-25-generic: No such file or directory
WARNING: missing /lib/modules/3.19.0-25-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.19.0-25-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_0mm9ap/lib/modules/3.19.0-25-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_0mm9ap/lib/modules/3.19.0-25-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-68-generic
Found initrd image: /boot/initrd.img-3.19.0-68-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-generic-lts-vivid (3.19.0.68.50) ...
Removing linux-image-extra-3.19.0-68-generic (3.19.0-68.76~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-68-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-3.19.0-68-generic
Found initrd image: /boot/initrd.img-3.19.0-68-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-headers-generic-lts-vivid (3.19.0.68.50) ...
Removing linux-headers-3.19.0-68-generic (3.19.0-68.76~14.04.1) ...
Removing linux-image-3.19.0-68-generic (3.19.0-68.76~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
dkms: removing: bbswitch 0.7 (3.19.0-68-generic) (i686)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.19.0-68-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-68-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: nvidia-367 367.44 (3.19.0-68-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-367
Version: 367.44
Kernel:  3.19.0-68-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_367.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-68-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_modeset.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-68-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


nvidia_367_drm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-68-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-68-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-68-generic /boot/vmlinuz-3.19.0-68-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Setting up linux-image-4.4.0-36-generic (4.4.0-36.55~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
vmlinuz(/boot/vmlinuz-4.4.0-36-generic
) points to /boot/vmlinuz-4.4.0-36-generic
 (/boot/vmlinuz-4.4.0-36-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-4.4.0-36-generic (4.4.0-36.55~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic-lts-xenial (4.4.0.36.26) ...
Setting up linux-generic-lts-xenial (4.4.0.36.26) ...
kingdom@king-MS-7728:~$ 


```

................................may you live to be a thousand ears...one thousand ears!!! =d>=d>=d>

---

### Post by ian-weisser on 2016-09-13
How does your df look now?
Is your booting problem solved?

What happened is that older kernels were prevented from auto-uninstall by the header packages, and those older kernels filled your tiny /boot partition.
The system won't autoremove anything you specified to install (kernel headers)...and also won't autoremove those dependencies (kernel images). 

If you use LVM (including encryption), keeping track of your /boot space is the tiny admin price you pay for the benefit of LVM/encryption.
Occasionally check /boot. If more than two kernels are there (current and last-good), find out why *before* it breaks your system.

---

### Post by xenon3 on 2016-09-14
> **ian-weisser said:**
> How does your df look now?

Is your booting problem solved?



```


kingdom@king-MS-7728:~$ df -ah
Filesystem              Size  Used Avail Use% Mounted on
sysfs                      0     0     0    - /sys
proc                       0     0     0    - /proc
udev                    4,0G   12K  4,0G   1% /dev
devpts                     0     0     0    - /dev/pts
tmpfs                   808M  1,3M  807M   1% /run
/dev/dm-1                66G  6,4G   56G  11% /
none                    4,0K     0  4,0K   0% /sys/fs/cgroup
none                       0     0     0    - /sys/fs/fuse/connections
none                       0     0     0    - /sys/kernel/debug
none                       0     0     0    - /sys/kernel/security
none                    5,0M     0  5,0M   0% /run/lock
none                    4,0G  3,0G 1003M  76% /run/shm
none                    100M   60K  100M   1% /run/user
none                       0     0     0    - /sys/fs/pstore
/dev/sda1               236M  114M  111M  51% /boot
systemd                    0     0     0    - /sys/fs/cgroup/systemd
/home/kingdom/.Private   66G  6,4G   56G  11% /home/kingdom
gvfsd-fuse                 0     0     0    - /run/user/1000/gvfs
/dev/sr0                4,3G  4,3G     0 100% /media/kingdom/LG_COMBI_RECORDER
/dev/sdd1               3,8G  674M  3,1G  18% /media/kingdom/CANON_DC
/dev/sdb1               1,8T  1,1T  736G  60% /media/kingdom/Data
kingdom@king-MS-7728:~$ 


```

I rather not try the booting because the newest kernel is still corrupt (in an update upgrade attempt which failed of to small boot partition as you know), anyways I will always suspend not shutdown until I am certain I got a pristine newest kernel

Moreover I'm not going to upgrade the older still booting and working fine kernel, booting I hope and working fine I know at least in RAM memory

---

### Post by ian-weisser on 2016-09-15
> **xenon3 said:**
> I rather not try the booting because the newest kernel is still corrupt (in an update upgrade attempt which failed of to small boot partition as you know), anyways I will always suspend not shutdown until I am certain I got a pristine newest kernel

That's a rather scary way to operate - power loss or a crash could hit at any time.
Let's fix your 'corrupt' kernel.

Let's look again at the status of all your kernels, both installed and uninstalled:
```
dpkg -l | grep linux-
```

---

### Post by xenon3 on 2016-09-15
> **ian-weisser said:**
> That's a rather scary way to operate - power loss or a crash could hit at any time.
Let's fix your 'corrupt' kernel.

Let's look again at the status of all your kernels, both installed and uninstalled:
```
dpkg -l | grep linux-
```

```


kingdom@king-MS-7728:~$ 
kingdom@king-MS-7728:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.22                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-xenial                              4.4.0.36.26                                         i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-68                               3.19.0-68.76~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-4.4.0-34                                4.4.0-34.53~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic                        4.4.0-34.53~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-36                                4.4.0-36.55~14.04.1                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic                        4.4.0-36.55~14.04.1                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-xenial                      4.4.0.36.26                                         i386         Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-66-generic                         3.19.0-66.74~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-3.19.0-68-generic                         3.19.0-68.76~14.04.1                                i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-34-generic                          4.4.0-34.53~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-36-generic                          4.4.0-36.55~14.04.1                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-66-generic                   3.19.0-66.74~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-68-generic                   3.19.0-68.76~14.04.1                                i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic                    4.4.0-34.53~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic                    4.4.0-36.55~14.04.1                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-xenial                        4.4.0.36.26                                         i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-95.142                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
kingdom@king-MS-7728:~$ 


```

---

### Post by ian-weisser on 2016-09-15
Try the following command to clean out the last of the old headers. If it succeeds, we don't need to see it. If it fails, please show us the complete output.
```
sudo apt remove linux-headers-3.19.0-68
```

Second, let's test your package manager for proper function.
```
sudo apt update
sudo apt upgrade
```

Third, let's take a look at your /boot
Try the following, and please show us the complete output.
```
ls -l /boot       //Those are both lower-case 'L's.
```

Finally, please show us the complete contents of your file /boot/grub/grub.cfg

---

### Post by Bashing-om on 2016-09-16
@ian-weisser' Opppsss //

Apologize for missing:
> 
linux-headers-3.19.0-68

I did think I was exercising care ! I hope my lapse did not cause you stress to see the error .

@ xenon3; See Ian's last, let us know how goes .


[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-18
> **ian-weisser said:**
> 

```
ls -l /boot       //Those are both lower-case 'L's.
```



```


kingdom@king-MS-7728:~$ ls -l /boot
total 106893
-rw-r--r-- 1 root root  1237729 jul 27 21:53 abi-4.4.0-34-generic
-rw-r--r-- 1 root root  1238066 aug 12 15:50 abi-4.4.0-36-generic
-rw-r--r-- 1 root root   193127 jul 27 21:53 config-4.4.0-34-generic
-rw-r--r-- 1 root root   193147 aug 12 15:50 config-4.4.0-36-generic
drwxr-xr-x 5 root root     1024 sep 13 14:38 grub
-rw-r--r-- 1 root root  7781473 sep 13 14:36 initrd.img-3.19.0-25-generic
-rw-r--r-- 1 root root 39159054 aug 24 17:36 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root 39156638 sep 13 14:38 initrd.img-4.4.0-36-generic
drwx------ 2 root root    12288 jul 15 05:47 lost+found
-rw-r--r-- 1 root root   176500 mrt 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 mrt 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 mrt 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3097534 jul 27 21:53 System.map-4.4.0-34-generic
-rw------- 1 root root  3098435 aug 12 15:50 System.map-4.4.0-36-generic
-rw------- 1 root root  6656608 jul 27 21:53 vmlinuz-4.4.0-34-generic
-rw------- 1 root root  6653760 aug 12 15:50 vmlinuz-4.4.0-36-generic
kingdom@king-MS-7728:~$ 


```

> **ian-weisser said:**
> 

Finally, please show us the complete contents of your file /boot/grub/grub.cfg

```


Can I yank it and paste it in VI editor? How do I do that? Or can I simply open it in a basic terminal command line text editor? And how do I do that?

GOT IT! Can be accessed from the GUI too:

[code]

   # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig
using templates # from /etc/grub.d and settings from
/etc/default/grub # 

### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi if [ "${next_entry}" ] ; then    set default="${next_entry}"    set next_entry=    save_env next_entry    set boot_once=true else    set default="0" fi 

if [ x"${feature_menuentry_id}" = xy
]; then   menuentry_id_option="--id" else   menuentry_id_option="" fi 

export menuentry_id_option 

if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi 

function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi } function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if
[ -z "${boot_once}" ]; then save_env recordfail; fi; fi } function load_video {   if [ x$feature_all_video_module = xy ]; then     insmod all_video   else     insmod efi_gop     insmod efi_uga     insmod ieee1275_fb     insmod vbe     insmod vga     insmod video_bochs     insmod video_cirrus   fi } 

if [ x$feature_default_font_path = xy ] ; then    font=unicode else insmod part_msdos insmod ext2 set root='hd0,msdos1' if [ x$feature_platform_search_hint = xy ]; then   search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 else   search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 fi     font="/grub/unicode.pf2" fi 

if loadfont $font ; then   set gfxmode=auto   load_video   insmod gfxterm   set locale_dir=$prefix/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ] ; then   set timeout=30 else   if [ x$feature_timeout_style = xy ] ; then     set timeout_style=hidden     set timeout=0   # Fallback hidden-timeout code in case the
timeout_style feature is   # unavailable.   elif sleep --interruptible 0 ; then     set timeout=0   fi fi ### END /etc/grub.d/00_header ### 

### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30,0; then   clear fi ### END /etc/grub.d/05_debian_theme ### 

### BEGIN /etc/grub.d/10_linux ### function gfxmode { 	set gfxpayload="${1}" 	if [ "${1}" = "keep" ];
then 		set vt_handoff=vt.handoff=7 	else 		set vt_handoff= 	fi } if [ "${recordfail}" != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3;
then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode menuentry 'Ubuntu' --class ubuntu --class
gnu-linux --class gnu --class os $menuentry_id_option
'gnulinux-simple-e40bbadd-eec9-4f0d-ba45-4e218812b91b' { 	recordfail 	load_video 	gfxmode $linux_gfx_mode 	insmod gzio 	insmod part_msdos 	insmod ext2 	set root='hd0,msdos1' 	if [ x$feature_platform_search_hint = xy ];
then 	  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 	else 	  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 	fi 	linux	/vmlinuz-4.4.0-36-generic
root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff 	initrd	/initrd.img-4.4.0-36-generic } submenu 'Advanced options for Ubuntu'
$menuentry_id_option
'gnulinux-advanced-e40bbadd-eec9-4f0d-ba45-4e218812b91b' { 	menuentry 'Ubuntu, with Linux 4.4.0-36-generic'
--class ubuntu --class gnu-linux --class gnu --class os
$menuentry_id_option
'gnulinux-4.4.0-36-generic-advanced-e40bbadd-eec9-4f0d-ba45-4e218812b91b'
{ 		recordfail 		load_video 		gfxmode $linux_gfx_mode 		insmod gzio 		insmod part_msdos 		insmod ext2 		set root='hd0,msdos1' 		if [ x$feature_platform_search_hint = xy ];
then 		  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 		else 		  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 		fi 		echo	'Loading Linux 4.4.0-36-generic ...' 		linux	/vmlinuz-4.4.0-36-generic
root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff 		echo	'Loading initial ramdisk ...' 		initrd	/initrd.img-4.4.0-36-generic 	} 	menuentry 'Ubuntu, with Linux 4.4.0-36-generic
(recovery mode)' --class ubuntu --class gnu-linux --class gnu --class
os $menuentry_id_option
'gnulinux-4.4.0-36-generic-recovery-e40bbadd-eec9-4f0d-ba45-4e218812b91b'
{ 		recordfail 		load_video 		insmod gzio 		insmod part_msdos 		insmod ext2 		set root='hd0,msdos1' 		if [ x$feature_platform_search_hint = xy ];
then 		  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 		else 		  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 		fi 		echo	'Loading Linux 4.4.0-36-generic ...' 		linux	/vmlinuz-4.4.0-36-generic
root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
		echo	'Loading initial ramdisk ...' 		initrd	/initrd.img-4.4.0-36-generic 	} 	menuentry 'Ubuntu, with Linux 4.4.0-34-generic'
--class ubuntu --class gnu-linux --class gnu --class os
$menuentry_id_option
'gnulinux-4.4.0-34-generic-advanced-e40bbadd-eec9-4f0d-ba45-4e218812b91b'
{ 		recordfail 		load_video 		gfxmode $linux_gfx_mode 		insmod gzio 		insmod part_msdos 		insmod ext2 		set root='hd0,msdos1' 		if [ x$feature_platform_search_hint = xy ];
then 		  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 		else 		  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 		fi 		echo	'Loading Linux 4.4.0-34-generic ...' 		linux	/vmlinuz-4.4.0-34-generic
root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff 		echo	'Loading initial ramdisk ...' 		initrd	/initrd.img-4.4.0-34-generic 	} 	menuentry 'Ubuntu, with Linux 4.4.0-34-generic
(recovery mode)' --class ubuntu --class gnu-linux --class gnu --class
os $menuentry_id_option
'gnulinux-4.4.0-34-generic-recovery-e40bbadd-eec9-4f0d-ba45-4e218812b91b'
{ 		recordfail 		load_video 		insmod gzio 		insmod part_msdos 		insmod ext2 		set root='hd0,msdos1' 		if [ x$feature_platform_search_hint = xy ];
then 		  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 		else 		  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 		fi 		echo	'Loading Linux 4.4.0-34-generic ...' 		linux	/vmlinuz-4.4.0-34-generic
root=/dev/mapper/ubuntu--vg-root ro recovery nomodeset 
		echo	'Loading initial ramdisk ...' 		initrd	/initrd.img-4.4.0-34-generic 	} } 

### END /etc/grub.d/10_linux ### 

### BEGIN /etc/grub.d/20_linux_xen ### 

### END /etc/grub.d/20_linux_xen ### 

### BEGIN /etc/grub.d/20_memtest86+ ### menuentry 'Memory test (memtest86+)' { 	insmod part_msdos 	insmod ext2 	set root='hd0,msdos1' 	if [ x$feature_platform_search_hint = xy ];
then 	  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 	else 	  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 	fi 	knetbsd	/memtest86+.elf } menuentry 'Memory test (memtest86+, serial
console 115200)' { 	insmod part_msdos 	insmod ext2 	set root='hd0,msdos1' 	if [ x$feature_platform_search_hint = xy ];
then 	  search --no-floppy --fs-uuid --set=root
--hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1
--hint-baremetal=ahci0,msdos1  e0157685-260d-4ee6-b3a9-14b06600df39 	else 	  search --no-floppy --fs-uuid --set=root
e0157685-260d-4ee6-b3a9-14b06600df39 	fi 	linux16	/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ### 

### BEGIN /etc/grub.d/30_os-prober ### ### END /etc/grub.d/30_os-prober ### 

### BEGIN /etc/grub.d/30_uefi-firmware ### ### END /etc/grub.d/30_uefi-firmware ### 

### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom
menu entries.  Simply type the # menu entries you want to add after this
comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ### 

### BEGIN /etc/grub.d/41_custom ### if [ -f  ${config_directory}/custom.cfg ]; then   source ${config_directory}/custom.cfg elif [ -z "${config_directory}" -a -f 
$prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ###


```

---

### Post by ian-weisser on 2016-09-18
rm /boot/initrd.img-3.19.0-25-generic

After that, seems safe to try a reboot. Grub looks pointing to the current kernels, which seem installed and have initrd files created.

---

### Post by xenon3 on 2016-09-18
> **ian-weisser said:**
> rm /boot/initrd.img-3.19.0-25-generic

After that, seems safe to try a reboot. Grub looks pointing to the current kernels, which seem installed and have initrd files created.

Can I still be able to rollback to kernel 4.4.0-34-generic in UBUNTU advanced options GRUB menu?

---

### Post by Bashing-om on 2016-09-18
xenon3; Hey .

> **xenon3 said:**
> Can I still be able to rollback to kernel 4.4.0-34-generic in UBUNTU advanced options GRUB menu?

Yep, these will not effect that ability .

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by xenon3 on 2016-09-19
Thanks! It worked, however I don't get GRUB menu, but this was always the case before, only when default kernel was corrupt GRUB menu appeared

```


kingdom@king-MS-7728:~$ uname -r
4.4.0-36-generic
kingdom@king-MS-7728:~$ 


```

---

### Post by xenon3 on 2016-09-19
> **Bashing-om said:**
> xenon3; Hey .[INDENT]
it is what it is
[/INDENT]



Thanks it worked!!!

..............................how can it not know what it is?   BLADERUNNER

---

### Post by xenon3 on 2016-09-19
In the future I can't of course not update and upgrade kernel again? Not enough free space boot partition?

---

### Post by ajgreeny on 2016-09-19
Great news! I am very glad that we eventually got this figured out for you.

Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by ian-weisser on 2016-09-19
> **xenon3 said:**
> In the future I can't of course not update and upgrade kernel again? Not enough free space boot partition?

You must perform basic maintenance each time you upgrade the kernel.
On most Ubuntu systems, this can be easily automated. Yours is different - you told the system that you want kernel headers, and the system won't delete those kernels automatically.

Each time the system upgrades the kernel, you must use apt to unsintall the oldest kernel and kernel-headers package.

Example: Let's pretend that tomorrow you install kernel 4.4.0-38.
```
$ dpkg -l | grep linux-

ii  linux-headers-4.4.0-34   
ii  linux-headers-4.4.0-34-generic 
ii  linux-headers-4.4.0-36 
ii  linux-headers-4.4.0-36-generic 
[B]ii  linux-headers-4.4.0-38 
ii  linux-headers-4.4.0-38-generic [/B]
ii  linux-image-4.4.0-34-generic  
ii  linux-image-4.4.0-36-generic  
**ii  linux-image-4.4.0-38-generic**  
ii  linux-image-extra-4.4.0-34-generic  
ii  linux-image-extra-4.4.0-36-generic 
**ii  linux-image-extra-4.4.0-38-generic**
```

Your system now has three sets of kernel packages: -34, -36, and the new -38.
You must now delete the **oldest** kernel (-34) packages:
```
sudo apt remove linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-34-generic
```

It's that easy.

It's harder than it needs to be for two reasons:
1) You chose an LVM/encrypted install, which limits your /boot. As the admin, you must manage that limited resource.
2) You chose to add kernel headers, which prevents autoremoval of old kernel packages...so you must do those removals manually. As you can see, using apt it's still very easy.

---

### Post by ajgreeny on 2016-09-19
If it's any help to you, I use synaptic to remove unwanted kernels and associate packages.

I set it to search by name alone, use the kernel version number of the unwanted kernel as my search term, eg 4.4.0-34, and then choose to remove all the packages that show in synaptic.

Synaptic is **always** worth installing in my opinion, it is a great deal more flexible than any of the software-centres have been, and it is possible to search all 48,000 packages available to me (I have some ppa repos increasing the number from about 36,000 I believe).

It used to be the default package manager for all debian and debian based OSs, including Ubuntu, and I use it and the command-line more than anything else for package management.

---

### Post by Bashing-om on 2016-09-19
> **ajgreeny said:**
> Great news! I am very glad that we eventually got this figured out for you.

Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

Good job team ! ..Way to go ..
Dough nuts and coffee all around . :)

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

