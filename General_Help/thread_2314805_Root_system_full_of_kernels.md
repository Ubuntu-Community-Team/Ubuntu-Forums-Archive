---
title: "Root system full of kernels?"
date: 2016-02-24
forum: General Help
---

### Post by MibunoOokami on 2016-02-24
Hi everyone,

I've just had a message telling me my root folder is full with less than 1GB free space. There was a prompt to run the disk usage analyser which is telling me 50% is used by usr, 31.6% lib & 11.2% var. Under lib 4.6GB is used by 30 tiny sections labelled "kernel" and under usr there is 3.8GB used by something called "scr" and a further 2.4GB used by "share" and finally a second directory called "lib" is using 1.9GB.

EDIT: For anyone else that might have this same problem. The majority of space was taken up by old kernels. Post [#4]("http://ubuntuforums.org/showthread.php?t=2314805&p=13445372#post13445372") offers one way or removing them. If that fails, post [#8]("http://ubuntuforums.org/showthread.php?t=2314805&p=13445761#post13445761") will work and [#13]("http://ubuntuforums.org/showthread.php?t=2314805&page=2&p=13446067#post13446067") will clarify anything that is uncertain. Post [#16]("http://ubuntuforums.org/showthread.php?t=2314805&page=2&p=13446422#post13446422") will tell you how to do a little extra house keeping once you have removed the old kernels. If in the event you end up with a black screen with a single white non flashing dash like I did, post [#54]("http://ubuntuforums.org/showthread.php?t=2314805&page=6&p=13447162#post13447162") should offer the quickest solution without having to sift through the other posts.

What I don't understand is my root directory should be 20GB because that's the size I partitioned it as, but it's only appearing as 15.6 GB. Home directory is 220GB, Window$ is 50GB and swap is 4GB which all seems to add up for my 320GB HDD less the 1024MB conversion thing which makes less space. (thinking out loud)

Should there be so many little kernels? And, how can I find out exactly what is taking up the space? Or perhaps I should do a fresh install and give root an extra 10GB?

---

### Post by ian-weisser on 2016-02-24
Open a terminal, and show us the complete output (copy-and-paste) of the following command:
```
df
```

---

### Post by MibunoOokami on 2016-02-24
> **ian-weisser said:**
> Open a terminal, and show us the complete output (copy-and-paste) of the following command:
```
df
```

```
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1016704         4   1016700   1% /dev
tmpfs             205264      1080    204184   1% /run
/dev/sda7       19058388  16978540   1088668  94% /
none                   4         0         4   0% /sys/fs/cgroup
none                5120         0      5120   0% /run/lock
none             1026316       636   1025680   1% /run/shm
none              102400        48    102352   1% /run/user
/dev/sda6      232585184 111662896 109084592  51% /home
/dev/sda1         203772     29068    174704  15% /media/mno/SYSTEM
```

---

### Post by Bashing-om on 2016-02-24
MibunoOokami; Hello;


Allow me to step in here while Ian is otherwise occupied ( offline ).
We can see that :
> 
/dev/sda7       19058388  16978540   1088668  94% /

'/' has the space constraints. One can look deeper and for sure know the reason... but 96+% of the time it is a over abundance of old kernels at the heart of the issue. Unless directed otherwise the system will not dictate to you about keeping old kernels. The system will not read your mind as to what you want to do with your system. Removing the kernels that you do not want becomes a part of the general light house keeping.

Let's look at what is:
```

dpkg -l | grep linux-

```

A whole bunch of old kernels installed, Yes ?
Now if you are happy to remove these old kernels, apt can and will do that for us.
Run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt-get autoremove

```
If the package manager is in a consistent state, and has the operating head room, 'autoremove' will remove obsolete - orphaned - packages, inclusive of the old kernels ; keeping the current kernel and one below it for a safety net.

Else ya want to manually take control of what kernels to keep - for whatever reason you want an old kernel around - ; well one can do that too . The package manager tools are versatile and able to handle a variety of situations !

However, I betcha that 'autoremove' will serve your needs.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by efflandt on 2016-02-24
In which Ubuntu versions does **sudo apt-get autoremove** actually remove old kernels? That does not seem to do anything for me in 14.04, although I currently only have 2 versions older than current one.

I usually use **synaptic** doing a Quick search for "linux" to manually select old headers to "completely remove" (which auto selects other headers for that version) and also remove old kernel images.

---

### Post by Bashing-om on 2016-02-24
efflandt; Humm ..

Maybe we best start investigating why
```

sysop@1404mini:~$ sudo apt-get autoremove
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.13.0-76 linux-headers-3.13.0-76-generic
  linux-image-3.13.0-76-generic linux-image-extra-3.13.0-76-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 271 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 148133 files and directories currently installed.)
Removing linux-headers-3.13.0-76-generic (3.13.0-76.120) ...
Removing linux-headers-3.13.0-76 (3.13.0-76.120) ...
Removing linux-image-extra-3.13.0-76-generic (3.13.0-76.120) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
Generating grub configuration file ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 14.04.2 LTS (14.04) on /dev/sda7
Found Ubuntu 14.04.3 LTS (14.04) on /dev/sdc1
Found Ubuntu 12.04.5 LTS (12.04) on /dev/sdc2
Found Ubuntu 15.10 (15.10) on /dev/sdc3
done
Removing linux-image-3.13.0-76-generic (3.13.0-76.120) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-76-generic
<snip>

```
as it works on 14.04 .

[INDENT][INDENT]hope this helps more
[INDENT][INDENT][INDENT]than confusing the issue
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-25
> **Bashing-om said:**
> MibunoOokami; Hello;


Allow me to step in here while Ian is otherwise occupied ( offline ).
We can see that :

'/' has the space constraints. One can look deeper and for sure know the reason... but 96+% of the time it is a over abundance of old kernels at the heart of the issue. Unless directed otherwise the system will not dictate to you about keeping old kernels. The system will not read your mind as to what you want to do with your system. Removing the kernels that you do not want becomes a part of the general light house keeping.

Let's look at what is:
```

dpkg -l | grep linux-

```

A whole bunch of old kernels installed, Yes ?
Now if you are happy to remove these old kernels, apt can and will do that for us.
Run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt-get autoremove

```
If the package manager is in a consistent state, and has the operating head room, 'autoremove' will remove obsolete - orphaned - packages, inclusive of the old kernels ; keeping the current kernel and one below it for a safety net.

Else ya want to manually take control of what kernels to keep - for whatever reason you want an old kernel around - ; well one can do that too . The package manager tools are versatile and able to handle a variety of situations !

However, I betcha that 'autoremove' will serve your needs.[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing,

Ran that code, it spat out
```
ii  linux-firmware                                              1.127.20                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.79.85                                        i386         Complete Generic Linux kernel and headers
ii  linux-generic-lts-raring                                    3.13.0.79.85                                        i386         Generic Linux kernel image and headers
ii  linux-generic-lts-trusty                                    3.13.0.79.85                                        i386         Generic Linux kernel image and headers
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                             3.13.0-30.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-33                                     3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                             3.13.0-33.58                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                                     3.13.0-40.69                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                             3.13.0-40.69                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                                     3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                             3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                                     3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                             3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                             3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                                     3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                             3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                                     3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                             3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                                     3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                             3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                                     3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                             3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                                     3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                             3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                                     3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                             3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                                     3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                             3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                                     3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                             3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                             3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.110                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                             3.13.0-67.110                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                                     3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                             3.13.0-68.111                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                                     3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                             3.13.0-71.114                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-73                                     3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73-generic                             3.13.0-73.116                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                                     3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                             3.13.0-74.118                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-76                                     3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                             3.13.0-76.120                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                                     3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                             3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-raring                            3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                            3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic                               3.13.0-33.58                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                               3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                               3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                               3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                               3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                               3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                               3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                               3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                               3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                               3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                               3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                               3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                               3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                               3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                               3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                               3.13.0-67.110                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                               3.13.0-68.111                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-71-generic                               3.13.0-71.114                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-73-generic                               3.13.0-73.116                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-74-generic                               3.13.0-74.118                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-76-generic                               3.13.0-76.120                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                               3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                               3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-35-generic                                3.8.0-35.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-36-generic                                3.8.0-36.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-37-generic                                3.8.0-37.53~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-38-generic                                3.8.0-38.56~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-39-generic                                3.8.0-39.58~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-41-generic                                3.8.0-41.60~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-42-generic                                3.8.0-42.63~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-44-generic                                3.8.0-44.66~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                         3.13.0-68.111                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                         3.13.0-71.114                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-73-generic                         3.13.0-73.116                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                         3.13.0-74.118                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                         3.13.0-76.120                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-image-generic-lts-raring                              3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-image-generic-lts-trusty                              3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         3.13.0-79.123                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies


```

Then ran sudo apt update, upgrade and autoremove. Autoremove only removed two things, I confirmed this by typing ypur first code again which produced ```
ii  linux-firmware                                              1.127.20                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.79.85                                        i386         Complete Generic Linux kernel and headers
ii  linux-generic-lts-raring                                    3.13.0.79.85                                        i386         Generic Linux kernel image and headers
ii  linux-generic-lts-trusty                                    3.13.0.79.85                                        i386         Generic Linux kernel image and headers
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                             3.13.0-30.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-33                                     3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                             3.13.0-33.58                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-36                                     3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                             3.13.0-36.63                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                                     3.13.0-40.69                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                             3.13.0-40.69                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                                     3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                             3.13.0-43.72                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                                     3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                             3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                             3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                                     3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                             3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                                     3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                             3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                                     3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                             3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                                     3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                             3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                                     3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                             3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                                     3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                             3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                                     3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                             3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                                     3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                             3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                             3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.110                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                             3.13.0-67.110                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                                     3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                             3.13.0-68.111                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                                     3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                             3.13.0-71.114                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-73                                     3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73-generic                             3.13.0-73.116                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                                     3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                             3.13.0-74.118                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-76                                     3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                             3.13.0-76.120                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                                     3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                             3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-raring                            3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                            3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic                               3.13.0-33.58                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-36-generic                               3.13.0-36.63                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                               3.13.0-40.69                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                               3.13.0-46.79                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                               3.13.0-48.80                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                               3.13.0-49.83                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                               3.13.0-52.86                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                               3.13.0-53.89                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                               3.13.0-54.91                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                               3.13.0-55.94                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                               3.13.0-57.95                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                               3.13.0-58.97                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                               3.13.0-61.100                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                               3.13.0-62.102                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                               3.13.0-63.103                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                               3.13.0-65.106                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                               3.13.0-66.108                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                               3.13.0-67.110                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                               3.13.0-68.111                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-71-generic                               3.13.0-71.114                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-73-generic                               3.13.0-73.116                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-74-generic                               3.13.0-74.118                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-76-generic                               3.13.0-76.120                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                               3.13.0-77.121                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                               3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-35-generic                                3.8.0-35.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-36-generic                                3.8.0-36.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-37-generic                                3.8.0-37.53~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-38-generic                                3.8.0-38.56~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-39-generic                                3.8.0-39.58~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-41-generic                                3.8.0-41.60~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-42-generic                                3.8.0-42.63~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-44-generic                                3.8.0-44.66~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                         3.13.0-36.63                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                         3.13.0-46.79                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                         3.13.0-48.80                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                         3.13.0-49.83                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                         3.13.0-52.86                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                         3.13.0-53.89                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                         3.13.0-68.111                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                         3.13.0-71.114                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-73-generic                         3.13.0-73.116                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                         3.13.0-74.118                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                         3.13.0-76.120                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                         3.13.0-77.121                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-image-generic-lts-raring                              3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-image-generic-lts-trusty                              3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         3.13.0-79.123                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies


``` Again.

I too use 14.04.

Edit: ```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-locale-ja libmpdec2
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 964 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1180253 files and directories currently installed.)
Removing firefox-locale-ja (44.0.2+build1-0ubuntu0.14.04.1) ...
Removing libmpdec2:i386 (2.4.0-6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
```

---

### Post by ian-weisser on 2016-02-25
Could be the kernel headers
Could be a specified metapackage or two

1) I assume you recall why you installed kernel headers, and why you actually ned them?
If that reason is no longer valid, then uninstall those 'headers' packages.

2) You have -raring and -trusty kernel packages installed. -raring isn't doing anything for you. Remove those.

3) Remove all the stale kernel images and their headers.
Use 'uname -r' to pinpoint your current kernel. DO NOT REMOVE YOUR CURRENT KERNEL!
Remove the others using apt or Synaptic.

4) Mark your wall calendar (assuming you retain kernel headers) and repeat the cleanout every six months or year or so.

16.04 fixes the most common bug that lets old kernels accumulate. The fix may (or may not) be backported to older releases of Ubuntu.

---

### Post by MibunoOokami on 2016-02-25
> **ian-weisser said:**
> 
1) I assume you recall why you installed kernel headers, and why you actually ned them?
If that reason is no longer valid, then uninstall those 'headers' packages.

They would've been installed by the software updater. I don't even know what a kernel header is, just that it has something to do with the OS.

> **ian-weisser said:**
> 
2) You have -raring and -trusty kernel packages installed. -raring isn't doing anything for you. Remove those.

3) Remove all the stale kernel images and their headers.
Use 'uname -r' to pinpoint your current kernel. DO NOT REMOVE YOUR CURRENT KERNEL!
Remove the others using apt or Synaptic.

Thank you, I'll attempt removal using Synaptic right after breakfast and post the results.

> **ian-weisser said:**
> 
16.04 fixes the most common bug that lets old kernels accumulate. The fix may (or may not) be backported to older releases of Ubuntu.

Now that you mention it, I seem to have a vague recollection of a kernel accumulation problem way back in Ubuntu 7.10 IIRC, but have no idea how it was fixed at that time.

---

### Post by MibunoOokami on 2016-02-25
Is it OK to mark for "complete removal" or should I just mark them just for "removal"?

---

### Post by ian-weisser on 2016-02-25
For kernel images and headers, both commands do exactly the same thing.

The difference is that "complete removal" (equivalent to --purge) also removes any package-placed settings files in /etc. Kernel packages and headers place no settings files in /etc

---

### Post by MibunoOokami on 2016-02-25
> **ian-weisser said:**
> For kernel images and headers, both commands do exactly the same thing.

The difference is that "complete removal" (equivalent to --purge) also removes any package-placed settings files in /etc. Kernel packages and headers place no settings files in /etc

OK thank you. I just have one last question whilst I'm backing everything up. uname -r said this ```
3.13.0-79-generic

``` but many headers labelled 3.13.0-79 have an extra decimal and 2-3 numbers, one of which was ```
linux-headers-generic-lts-raring 3.13.0-79.85
```

Although you said I don't need raring headers, since it is also 3.13.0-79 should I retain it? Or is the only kernel header that I should keep, specifically the one labelled 3.13.0-79-generic? I just want to be absolutely certain about what I'm doing.

Thanks for your help and patience whilst I work this out.

---

### Post by ian-weisser on 2016-02-25
The extra two numbers are not important for this purpose, and can be ignored.
Avoid confusion by using the package *name*, not the package *version number*.

You have a single set of packages for 3.13.0.79:  KEEP THESE
linux-headers-generic
linux-headers-3.13.0-79
linux-headers-3.13.0-79-generic
linux-image-generic
linux-image-3.13.0-79-generic
linux-image-extra-3.13.0-79-generic

Remove all the other linux-headers-* and linux-image-* packages.

You can also safely remove:
linux-headers-generic-lts-raring
linux-headers-generic-lts-trusty
linux-image-generic-lts-raring
linux-image-generic-lts-trusty

---

### Post by MibunoOokami on 2016-02-25
> **Bashing-om said:**
> 
If the package manager is in a consistent state, and has the operating head room, 'autoremove' will remove obsolete - orphaned - packages, inclusive of the old kernels ; keeping the current kernel and one below it for a safety net.


I meant to ask about this yesterday but forgot. How does one ensure their package manager is in a consistent state and has the operating head room for autoremove to work efficiently? Obviously mine isn't since autoremove didn't work properly.

> **ian-weisser said:**
> The extra two numbers are not important for this purpose, and can be ignored.
Avoid confusion by using the package *name*, not the package *version number*.


Thanks for your help, I removed all old headers first which it said would would free up 2.6GB, then I did the images, which interestingly said would free up an additional 4XX GB. Something must have been a bit buggy with my computer because you may recall, at the start of this thread I said the disk usage analyser thought my root directory is only 15.6GB and that 4.6GB was taken by kernels. Now it says I have 20GB as it should be and of course as mentioned above I've removed more than 6.6GB of kernel related headers and images.

Here is the output of ```
df
```
```
~/ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1016704        12   1016692   1% /dev
tmpfs             205264      1056    204208   1% /run
/dev/sda7       19058388   7917148  10150060  44% /
none                   4         0         4   0% /sys/fs/cgroup
none                5120         0      5120   0% /run/lock
none             1026316       400   1025916   1% /run/shm
none              102400        44    102356   1% /run/user
/dev/sda6      232585184 111693124 109054364  51% /home

``` Significant improvement right!?

Next is ```
dpkg -l | grep linux-
```

```
~/ dpkg -l | grep linux-
ii  linux-firmware                                              1.127.20                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.79.85                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-79-generic                               3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-29-generic                                3.8.0-29.42~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-34-generic                                3.8.0-34.49~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-35-generic                                3.8.0-35.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-36-generic                                3.8.0-36.52~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-37-generic                                3.8.0-37.53~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-38-generic                                3.8.0-38.56~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-39-generic                                3.8.0-39.58~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-41-generic                                3.8.0-41.60~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-42-generic                                3.8.0-42.63~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-44-generic                                3.8.0-44.66~precise1                                i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         3.13.0-79.123                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
```

A lot of the images and headers listed above are unchecked or no longer in synaptic so not sure why they still get listed here. The main thing is my root directory is now tidy. Thanks again for all the help.

---

### Post by ian-weisser on 2016-02-25
> **MibunoOokami said:**
> A lot of the images and headers listed above are unchecked or no longer in synaptic so not sure why they still get listed here.

That listing is not a particular directory.
Your system keeps a database of all known packages, and that is the database output.
The database includes packages that are installed (ii) and packages that have been removed (rc).

Your system needs to know about packages that are not actually installed - else you could never install new packages.
Your system never bothers to forget about old packages in case you need to downgrade, or in case you need to compare packages from different sources.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Hey hey .......

Look'n good.

Now my turn to add my 2 cent's worth to the knowledge store:

> 
I meant to ask about this yesterday but forgot. How does one ensure their package manager is in a consistent state and has the operating head room for autoremove to work efficiently? Obviously mine isn't since autoremove didn't work properly.

Consistent state is that 'apt' runs the update/upgrade processes with no complaints.
Headroom is when 'df' returns with less than 90% capacity used .

Now further expounding on packages marked as 'rc':
IF there is no intention of revisiting removed packageS:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package;  The state is rc, the package is removed, but the config files are not removed.
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Once the 'dpkg' command is run, take a look at what it did.
```

dpkg -l | grep linux-

```
compare to the previous outputs, much less clutter !

mind you,
[INDENT][INDENT][INDENT]I am a firm believer in keeping it
[INDENT][INDENT][INDENT]clean behind me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **Bashing-om said:**
> <snip>

Consistent state is that 'apt' runs the update/upgrade processes with no complaints.
Headroom is when 'df' returns with less than 90% capacity used.

Makes sense. I typically only ran apt update, upgrade and autoremove if I installed something via terminal which is very seldom.

> **Bashing-om said:**
> 
Now further expounding on packages marked as 'rc':
IF there is no intention of revisiting removed packageS:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package;  The state is rc, the package is removed, but the config files are not removed.
Now let’s remove all the packages marked as rc.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

WOW! That got rid of tonnes of..... Something. As in a lot more than just old headers and images I believe.

> **Bashing-om said:**
> Once the 'dpkg' command is run, take a look at what it did.
```

dpkg -l | grep linux-

```
compare to the previous outputs, much less clutter !

mind you,[INDENT][INDENT][INDENT]I am a firm believer in keeping it[INDENT][INDENT][INDENT]clean behind me
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```
dpkg -l | grep linux-
ii  linux-firmware                                              1.127.20                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.79.85                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.79.85                                        i386         Generic Linux kernel headers
ii  linux-image-3.13.0-79-generic                               3.13.0-79.123                                       i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                                       i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.79.85                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         3.13.0-79.123                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies


```

That does look even better. I'll be sure to run autoremove after each software update to ensure things run even more smoothly. Unless there are additional things I can do in the form of reducing clutter?

Thanks again.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Welp;

I run a very tight install, and I MUST pay attention to disk space usage.
My methology for housecleaning .
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt update
sudo apt upgrade
##maybe## sudo apt full-upgrade
## A check on what the package manager thinks## sudo dpkg -C
##where a return to prompt is a good thing.

```

That is all I ever ever used for my general house keeping. But make yourself aware of what these commands "clean out" . Be aware of why you do so . There is no looking back once done .

[INDENT][INDENT]all there is too it, all I can say
[INDENT][INDENT][INDENT]ain't 'buntu wonderful
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
Oh dear. Something important must have been purged because I just restarted my computer, it goes to the normal grub screen fine, then for a split second to the login screen but changes to a black screen with a single non flashing dash. Any ideas how to fix this?

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; hey ...

Update broke a proprietary graphic's driver ?

At the login screen can you activate a console interface - ctl+alt_F1 ?

Terminal command :
```

sudo lshw -C display

```
Give the system a bit of time to search and complete.
in that output's configuration line is a driver listed ?

[INDENT][INDENT]in such a case
[INDENT][INDENT][INDENT]not ubuntu's fault
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **Bashing-om said:**
> MibunoOokami; hey ...

Update broke a proprietary graphic's driver ?

At the login screen can you activate a console interface - ctl+alt_F1 ?

Terminal command :
```

sudo lshw -C display

```
Give the system a bit of time to search and complete.
in that output's configuration line is a driver listed ?
[INDENT][INDENT]in such a case[INDENT][INDENT][INDENT]not ubuntu's fault
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I managed to activate a console interface and entered that code, here's the output ```
configuration: driver=gma500 latency=0
```

No doubt yesterday I removed something I shouldn't have which impacted today.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Hummmm ...

Do not know that I can go there as you have a gma500 for graphics, just not a lot of support for that chip set , and my experience here is very limited.

As we do not have a fall back kernel installed, we do "something else" for troubleshooting.
Let's take a look and see what the X layer (GUI) is doing.
Run terminal commands:
```

sudo apt install pastebinit
pastebinit /var/log/Xorg.0.log

```
the result will be a URL back in terminal. Pass that link back here and we can then read that log file.
See if the log file gives us some hints on the nature of the failure, and a direction for resolvement.


[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **Bashing-om said:**
> 
Run terminal commands:
```

sudo apt install pastebinit
pastebinit /var/log/Xorg.0.log

```


Unable to read from /var/log/Xorg.0.log

I didn't back my PC up after removing the kernels yesterday so perhaps I can reinstall one from my back up drive? Edit: It turns out I only back up my /home directory and not /root. I think I have a live cd floating around but am guessing if it were as easy as either of these options you would have suggested it.

---

### Post by ian-weisser on 2016-02-26
GMA500 should work using any Ubuntu kernel without additional package or chenged settings.

'Unable to read from /var/log/Xorg.0.log' is very unusual.
Does the file exist? Can you read it from a shell prompt using 'cat' or 'less'?
Can you read other log files in /var/log?

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Welp;

That log file does not exit or is unpopulated ?
what returns:
```

la -al /var/log/Xorg.0.log

```

If and the stress is on IF - this is a kernel issue ... we can install a kernel .. just do not know how far back we should go . 

Do you recall using the linux-image-extra-3.13.0-67 kernel successfully ?
Won't take much to find out .

[INDENT][INDENT]where there is a will there is a way.[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **ian-weisser said:**
> GMA500 should work using any Ubuntu kernel without additional package or chenged settings.

'Unable to read from /var/log/Xorg.0.log' is very unusual.
Does the file exist? Can you read it from a shell prompt using 'cat' or 'less'?
Can you read other log files in /var/log?

I'm not sure what to do with cat or less. Typing cat in console it just sits there. Less comes back as missing file name.
When I did cd /var/log a lot is displayed but nothing about Xorg. Alphabetically, wtmp.1 is the last entry

> **Bashing-om said:**
> MibunoOokami; Welp;

That log file does not exit or is unpopulated ?
what returns:
```

la -al /var/log/Xorg.0.log

```

If and the stress is on IF - this is a kernel issue ... we can install a kernel .. just do not know how far back we should go . 

Do you recall using the linux-image-extra-3.13.0-67 kernel successfully ?
Won't take much to find out .[INDENT][INDENT]where there is a will there is a way.[/INDENT]
[/INDENT]


```
ls: cannot access /var/log/Xorg.0.log: No such file or directory
```

I can't say I noticed any problems prior to getting the message about /root being full, so I'm guessing the kernels have all worked fine. I just let software updater do all the work without me paying too much attention. I understand now, that's probably not the best idea.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Hummm ...

Strange there is no Xorg file ..

let's re-install a kernel:
```

sudo apt-get update && sudo apt-get install linux-image-3.13.0-67-generic linux-headers-3.13.0-67-generic linux-headers-3.13.0-67 linux-image-extra-3.13.0-67-generic

sudo update-grub

```
and see what we can do.
Reboot:
```

sudo reboot now

```

Booting back to the grub boot menu, now do you have the option to boot the -67 kernel ?
what results when attempting to boot that -67 kernel ?

[INDENT][INDENT]if at 1st you do not succeed 
[INDENT][INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **Bashing-om said:**
> MibunoOokami; Hummm ...

Strange there is no Xorg file ..

let's re-install a kernel:
```

sudo apt-get update && sudo apt-get install linux-image-3.13.0-67-generic linux-headers-3.13.0-67-generic linux-headers-3.13.0-67 linux-image-extra-3.13.0-67-generic

sudo update-grub

```
and see what we can do.
Reboot:
```

sudo reboot now

```

Booting back to the grub boot menu, now do you have the option to boot the -67 kernel ?
what results when attempting to boot that -67 kernel ?
[INDENT][INDENT]if at 1st you do not succeed [INDENT][INDENT][INDENT][INDENT]try something else
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Hi Bashing, it looked like it was installing fine but after reboot there was no kernel option at the grub boot menu and it's gone back to the exact same black screen as though nothing has changed.

Ironically, I was contemplating saving the terminal after that purge earlier but decided against it and rebooted. In retrospect, had I done that, we probably could have viewed it in nano or something and got an idea of what happened. All I can do is LOL at the novelty of hindsight.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Hummm ...

curious and curiouser ...

let's look and see that the kernel did install:
```

dpkg -l | grep linux-

```

and what is set now for booting ?
```

ls -al /vmlinuz*
ls -al /initrd.img*

```

[INDENT][INDENT]'cause
[INDENT][INDENT][INDENT]that last sure not what I expected
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
Can you tell me how to access this forum using console so I can copy and paste the output? I'm replying with my wife's computer. Edit: That's assuming I could reply here and enter the commands at the same time by swapping widows.

```
ls -al /vmlinuz*
``` Says, 
```
1rwxrwxrwx 1 root root 30 Feb 27 13:10 /vmlinuz -> boot/vmlinuz-3.13.0-67-generic
1rwxrwxrwx 1 root root 30 Feb 23 17:33 /vmlinuz.old -> boot/vmlinuz-3.13.0-79-generic
```

```
ls -al /initrd.img*
``` Says
```
1rwxrwxrwx 1 root root 33 Feb 27 13:10 /initrd.img -> boot/initrd.img-3.13.0-67-generic
1rwxrwxrwx 1 root root 33 Feb 23 17:33 /initrd.img.old -> boot/initrd.img-3.13.0-79-generic
```

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Sure.

On the broken system run:
```

sudo apt install pastebinit
dpkg -l | grep linux- | pastebinit
ls -al /vmlinuz* | pastebinit
ls -al /initrd.img* | pastebinit

```
the results are URLs back in terminal; pass those links back here to the thread and we can access the files that pastebinit generated. Sure saves a lot of typing .

[INDENT][INDENT]'buntu
[INDENT][INDENT]if it is hard, you are doing it wrong
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
Ggrrrrrrrr........... 

My keyboard layout is not English and I've just discovered I don't have that vertical dash. Without a mouse, is there any other way to copy and paste it. It's still in console/terminal from when I copied it yesterday. Alternatively if there's a way in console to change my keyboard's layout to English then I will have that dash. 

I do apologise that this is taking up so much of your time. Please know I do appreciate it and I am doing my best.


EDIT: I'm angry with myself because it seems every single time I need help with something and need to use terminal, some how I manage to screw it up. And of course not using the English layout doesn't help in times like this.

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Hey ...

working on getting the terminal input ... I have found the keycode - 05C0 - 
now if I can just figure out the escape sequence to get it into that terminal .

be back soonest I know .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
Sweet,  I just Googled how to change keyboard layout in terminal and have done it. The pastebinit urls are [http://paste.ubuntu.com/15211689](http://paste.ubuntu.com/15211689)
[http://paste.ubuntu.com/15211704](http://paste.ubuntu.com/15211704)
[http://paste.ubuntu.com/15211710](http://paste.ubuntu.com/15211710)

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Sheeshhh ...

Now I do not know what to think ,,, as per those last outputs, the kernel is installed,,, and the -67 version is set as the default boot.

Getting the same result booting either the -79 or the -67 version indicates to me this is not a kernel issue. We need to look elsewhere for the fault. Got no log file ... ouch ! and something in that non-event reeks . You are able to boot to a console and the system at that level is functional; so we are looking at a fault within the X layer.

Is this system using unity as the desktop environment ? How about we boot to terminal (TTY1) and try and start the GUI from terminal .  Maybe in terminal we can get some information.

Reboot to grub, and with that -67 kernel selected to boot pres the 'e' key for edit mode -> boot parameters screen;
arrow down to the line starting with linux and arrow across to quiet splash,
Replace "quiet splash" with the term 'text' - with out the quotes -
key combo ctl+x to continue the boot process to TTY1 ...
log in here with your credentials.

what results now when attempting to start the GUI with terminal command :
```

sudo service lightdm start

```
If it fails to start, can you catch any of the errors the system reports back in terminal ?

Presently I just do not have a better idea of what to do than start in terminal and go looking .

[INDENT][INDENT][INDENT]how do you spell bad day
 [/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
> **Bashing-om said:**
> MibunoOokami; Sheeshhh ...

Now I do not know what to think ,,, as per those last outputs, the kernel is installed,,, and the -67 version is set as the default boot.
<snip>
what results now when attempting to start the GUI with terminal command :
```

sudo service lightdm start

```
If it fails to start, can you catch any of the errors the system reports back in terminal ?

At first it said ```
start: Job failed to start
``` I didn't see any errors so repeated the command, again no error messages, the third time however, it said ```
lightdm start/running
```
Although nothing else has changed, terminal is awaiting further commands.

> **Bashing-om said:**
>  [INDENT][INDENT][INDENT]how do you spell bad day
 [/INDENT]
[/INDENT]
[/INDENT]


MibuNoOokami is how I'd spell it ;)

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; Yikes !

> 
lightdm start/running
Although nothing else has changed, terminal is awaiting further commands.


Should have switched to the GUI ! ...

As the terminal is setting there .. what results with key combo ctl+alt+F7 ... which is the terminal that the GUI is running in - if all were right.

and as we get no other info ... we got any thing in :
```

pastebinit .xsession-errors

```
where this is a hidden file in your /home directory .

Keep in mind .... doing these puzzles, for me, sure beats doing jig saw puzzles ! What a stretch of the mind these things can be.

[INDENT][INDENT]never can tell
[INDENT][INDENT][INDENT]what I might learn today
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
Ctrl + alt + f7 goes to the same black screen except the white dash is flashing. 

Here's the output you requested.
```
 http://paste.ubuntu.com/15212448/
```

---

### Post by Bashing-om on 2016-02-26
MibunoOokami; yuk ..

> 
init: gnome-session (Unity) main process (1936) killed by TERM signal

not much help there either.

My brain is turning mushy. Let's sleep on this, and I cogitate and then see what I can come up with .
Got to be a way we can poke at this and find out what the graphic's driver is doing .

Take a pause for the cause;
[INDENT][INDENT]but, like a dog with a bone
[INDENT][INDENT][INDENT][INDENT]no quit in our nature
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-26
No problem, catch you tomorrow. Thanks for your help thus far

---

### Post by vasa1 on 2016-02-27
Why is this tagged [SOLVED]?

You can follow the same procedure to reverse it. That's right at the bottom here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by MibunoOokami on 2016-02-27
> **vasa1 said:**
> Why is this tagged [SOLVED]?

You can follow the same procedure to reverse it. That's right at the bottom here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Because it was solved at one point and then I forgot to change it to unsolved

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Morning ...

Back on this,,, while I am look'n and a think'n ... what is the driver doing ?
what returns:
```

lsmod | grep gma

```
Should be similar:
```

gma500_gfx            131893  2 
i2c_algo_bit            4615  1 gma500_gfx
drm_kms_helper         29203  1 gma500_gfx
drm                   170883  2 drm_kms_helper,gma500_gfx
i2c_core               16653  5 drm,drm_kms_helper,i2c_algo_bit,gma500_gfx,videodev

```

More to come as 
[INDENT][INDENT][INDENT]I seek and find
[/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> MibunoOokami; Morning ...

Back on this,,, while I am look'n and a think'n ... what is the driver doing ?
what returns:
```

lsmod | grep gma

```
Should be similar:
```

gma500_gfx            131893  2 
i2c_algo_bit            4615  1 gma500_gfx
drm_kms_helper         29203  1 gma500_gfx
drm                   170883  2 drm_kms_helper,gma500_gfx
i2c_core               16653  5 drm,drm_kms_helper,i2c_algo_bit,gma500_gfx,videodev

```

More to come as [INDENT][INDENT][INDENT]I seek and find
[/INDENT]
[/INDENT]
[/INDENT]

 
Good morning Bashing-om,

The [output]("http://paste.ubuntu.com/15216287") looks a little similar to me.

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Welp ....

That lsmod output indicates there is no driver problem . That leads to questioning a desktop config issue in your user account .
What results when you log in from the quest account at the login screen ?
Just do not have enough info to this time to point a finger at the fault .

[INDENT][INDENT]poke at it
[INDENT][INDENT][INDENT]see where it bites
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> 
What results when you log in from the quest account at the login screen ?


It flashes past the login screen too fast for me to select a user account. Sometimes it doesn't even flash, goes straight from grub screen (where you choose Ubuntu or Windoze) to black screen with non flashing dash, I hope that makes sense?

Perhaps we should revisit the command ```
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
``` from [post 16]("http://ubuntuforums.org/showthread.php?t=2314805&p=13446422#post13446422")? Since this problem only occurred after running that command and rebooting, maybe it inadvertently did something it shouldn't have?

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Well ..

the 'dpkg' command only removes those package files that the package manager has marked as 'rc' ( removed but config files remain) .. Though possible it is unlikely for the package manager to get carried away .. 
Will not hurt to take a look at what was done:
```

cat /var/log/dpkg.log
cat /var/log/dpkg.log.1

```
where the timestamps will reflect when the operations took place.

Agreed, there is a reason
[INDENT][INDENT][INDENT]find the cause
[/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **MibunoOokami said:**
> Unable to read from /var/log/Xorg.0.log

It's probably not the same thing, but under /var/log/lightdm there is a file called x-0.log. In that file there is only a short line of text which says [code]X: cannot stat /etc/X11/X (No such file or directory), aborting. I figured I'd post that here just in case it's the same Xorg file with just a different name. Thanks

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> MibunoOokami; Well ..

the 'dpkg' command only removes those package files that the package manager has marked as 'rc' ( removed but config files remain) .. Though possible it is unlikely for the package manager to get carried away .. 
Will not hurt to take a look at what was done:
```

cat /var/log/dpkg.log
cat /var/log/dpkg.log.1

```
where the timestamps will reflect when the operations took place.

Agreed, there is a reason[INDENT][INDENT][INDENT]find the cause
[/INDENT]
[/INDENT]
[/INDENT]


That was one long list. This is everything from yesterday, I copied and pasted from pastebinit.

```
2016-02-27 07:56:47 startup packages purge
2016-02-27 07:56:47 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 remove account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2 <none>
2016-02-27 07:56:59 purge account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2 <none>
2016-02-27 07:56:59 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 status config-files account-plugin-windows-live:all 0.11+14.04.20140409.1-0ubuntu2
2016-02-27 07:56:59 status not-installed account-plugin-windows-live:all <none>
2016-02-27 07:56:59 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:56:59 remove appmenu-gtk:i386 0.3.92-0ubuntu1.1 <none>
2016-02-27 07:56:59 purge appmenu-gtk:i386 0.3.92-0ubuntu1.1 <none>
2016-02-27 07:56:59 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:56:59 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:56:59 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:56:59 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status config-files appmenu-gtk:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status not-installed appmenu-gtk:i386 <none>
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 remove appmenu-gtk3:i386 0.3.92-0ubuntu1.1 <none>
2016-02-27 07:57:00 purge appmenu-gtk3:i386 0.3.92-0ubuntu1.1 <none>
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status config-files appmenu-gtk3:i386 0.3.92-0ubuntu1.1
2016-02-27 07:57:00 status not-installed appmenu-gtk3:i386 <none>
2016-02-27 07:57:00 status config-files bubbros:all 1.6-2
2016-02-27 07:57:00 remove bubbros:all 1.6-2 <none>
2016-02-27 07:57:00 purge bubbros:all 1.6-2 <none>
2016-02-27 07:57:00 status config-files bubbros:all 1.6-2
2016-02-27 07:57:00 status config-files bubbros:all 1.6-2
2016-02-27 07:57:00 status config-files bubbros:all 1.6-2
2016-02-27 07:57:01 status config-files bubbros:all 1.6-2
2016-02-27 07:57:01 status config-files bubbros:all 1.6-2
2016-02-27 07:57:01 status not-installed bubbros:all <none>
2016-02-27 07:57:01 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:01 remove checkbox:all 0.17.6-0ubuntu6 <none>
2016-02-27 07:57:01 purge checkbox:all 0.17.6-0ubuntu6 <none>
2016-02-27 07:57:01 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:01 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:01 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:04 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:05 status config-files checkbox:all 0.17.6-0ubuntu6
2016-02-27 07:57:05 status not-installed checkbox:all <none>
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 remove consolekit:i386 0.4.5-3.1ubuntu2 <none>
2016-02-27 07:57:05 purge consolekit:i386 0.4.5-3.1ubuntu2 <none>
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 status config-files consolekit:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:05 status not-installed consolekit:i386 <none>
2016-02-27 07:57:06 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:06 remove fonts-wqy-microhei:all 0.2.0-beta-2 <none>
2016-02-27 07:57:06 purge fonts-wqy-microhei:all 0.2.0-beta-2 <none>
2016-02-27 07:57:06 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:06 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:06 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:06 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:07 status config-files fonts-wqy-microhei:all 0.2.0-beta-2
2016-02-27 07:57:07 status not-installed fonts-wqy-microhei:all <none>
2016-02-27 07:57:07 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:07 remove foomatic-filters:i386 4.0.16-0ubuntu0.2 <none>
2016-02-27 07:57:07 purge foomatic-filters:i386 4.0.16-0ubuntu0.2 <none>
2016-02-27 07:57:07 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:07 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:07 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:09 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:09 status config-files foomatic-filters:i386 4.0.16-0ubuntu0.2
2016-02-27 07:57:09 status not-installed foomatic-filters:i386 <none>
2016-02-27 07:57:09 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:09 remove frozen-bubble:i386 2.2.0-2ubuntu3 <none>
2016-02-27 07:57:09 purge frozen-bubble:i386 2.2.0-2ubuntu3 <none>
2016-02-27 07:57:09 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:09 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:10 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:10 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:10 status config-files frozen-bubble:i386 2.2.0-2ubuntu3
2016-02-27 07:57:10 status not-installed frozen-bubble:i386 <none>
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 remove gpac:i386 0.4.5+svn3462~dfsg0-1 <none>
2016-02-27 07:57:10 purge gpac:i386 0.4.5+svn3462~dfsg0-1 <none>
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 status config-files gpac:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:10 status not-installed gpac:i386 <none>
2016-02-27 07:57:10 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 remove gs-cjk-resource:all 1.20100103-3 <none>
2016-02-27 07:57:11 purge gs-cjk-resource:all 1.20100103-3 <none>
2016-02-27 07:57:11 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 status config-files gs-cjk-resource:all 1.20100103-3
2016-02-27 07:57:11 status not-installed gs-cjk-resource:all <none>
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:11 remove guile-1.8-libs:i386 1.8.8+1-6ubuntu2 <none>
2016-02-27 07:57:11 purge guile-1.8-libs:i386 1.8.8+1-6ubuntu2 <none>
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:11 status config-files guile-1.8-libs:i386 1.8.8+1-6ubuntu2
2016-02-27 07:57:12 status not-installed guile-1.8-libs:i386 <none>
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 remove gwibber:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:57:12 purge gwibber:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 status config-files gwibber:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:12 status not-installed gwibber:i386 <none>
2016-02-27 07:57:12 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:12 remove hddtemp:i386 0.3-beta15-52 <none>
2016-02-27 07:57:12 purge hddtemp:i386 0.3-beta15-52 <none>
2016-02-27 07:57:12 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:12 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:12 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:14 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:14 status config-files hddtemp:i386 0.3-beta15-52
2016-02-27 07:57:14 status not-installed hddtemp:i386 <none>
2016-02-27 07:57:14 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:14 remove im-switch:all 1.20ubuntu5.2 <none>
2016-02-27 07:57:14 purge im-switch:all 1.20ubuntu5.2 <none>
2016-02-27 07:57:14 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:14 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:14 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:14 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:15 status config-files im-switch:all 1.20ubuntu5.2
2016-02-27 07:57:15 status not-installed im-switch:all <none>
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 remove jockey-common:all 0.9.7-0ubuntu7.11 <none>
2016-02-27 07:57:15 purge jockey-common:all 0.9.7-0ubuntu7.11 <none>
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 status config-files jockey-common:all 0.9.7-0ubuntu7.11
2016-02-27 07:57:15 status not-installed jockey-common:all <none>
2016-02-27 07:57:15 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:15 remove jockey-gtk:all 0.9.7-0ubuntu7.10 <none>
2016-02-27 07:57:15 purge jockey-gtk:all 0.9.7-0ubuntu7.10 <none>
2016-02-27 07:57:15 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:15 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:16 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:16 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:16 status config-files jockey-gtk:all 0.9.7-0ubuntu7.10
2016-02-27 07:57:16 status not-installed jockey-gtk:all <none>
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 remove libao-common:all 1.1.0-1ubuntu2 <none>
2016-02-27 07:57:16 purge libao-common:all 1.1.0-1ubuntu2 <none>
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 status config-files libao-common:all 1.1.0-1ubuntu2
2016-02-27 07:57:16 status not-installed libao-common:all <none>
2016-02-27 07:57:16 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 remove libao4:i386 1.1.0-1ubuntu2 <none>
2016-02-27 07:57:17 purge libao4:i386 1.1.0-1ubuntu2 <none>
2016-02-27 07:57:17 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 status config-files libao4:i386 1.1.0-1ubuntu2
2016-02-27 07:57:17 status not-installed libao4:i386 <none>
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:17 remove libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17 <none>
2016-02-27 07:57:17 purge libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17 <none>
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:17 status config-files libapt-inst1.4:i386 0.8.16~exp12ubuntu10.17
2016-02-27 07:57:18 status not-installed libapt-inst1.4:i386 <none>
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 remove libarchive12:i386 3.0.3-6ubuntu1 <none>
2016-02-27 07:57:18 purge libarchive12:i386 3.0.3-6ubuntu1 <none>
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 status config-files libarchive12:i386 3.0.3-6ubuntu1
2016-02-27 07:57:18 status not-installed libarchive12:i386 <none>
2016-02-27 07:57:18 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:18 remove libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1 <none>
2016-02-27 07:57:18 purge libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1 <none>
2016-02-27 07:57:18 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:18 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:18 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:19 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:19 status config-files libavahi-ui-gtk3-0:i386 0.6.31-4ubuntu1
2016-02-27 07:57:19 status not-installed libavahi-ui-gtk3-0:i386 <none>
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 remove libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1 <none>
2016-02-27 07:57:19 purge libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1 <none>
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 status config-files libavcodec-extra-53:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:19 status not-installed libavcodec-extra-53:i386 <none>
2016-02-27 07:57:19 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:19 remove libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:19 purge libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:19 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:20 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:20 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:20 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:20 status config-files libavcodec53:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:20 status not-installed libavcodec53:i386 <none>
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 remove libavcodec54:i386 6:9.18-0ubuntu0.14.04.1 <none>
2016-02-27 07:57:20 purge libavcodec54:i386 6:9.18-0ubuntu0.14.04.1 <none>
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 status config-files libavcodec54:i386 6:9.18-0ubuntu0.14.04.1
2016-02-27 07:57:20 status not-installed libavcodec54:i386 <none>
2016-02-27 07:57:20 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 remove libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:21 purge libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:21 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavfilter2:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status not-installed libavfilter2:i386 <none>
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 remove libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:21 purge libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:21 status config-files libavformat53:i386 4:0.8.15-0ubuntu0.12.04.1
2016-02-27 07:57:22 status not-installed libavformat53:i386 <none>
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 remove libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1 <none>
2016-02-27 07:57:22 purge libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1 <none>
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil-extra-51:i386 4:0.8.15ubuntu0.12.04.1
2016-02-27 07:57:22 status not-installed libavutil-extra-51:i386 <none>
2016-02-27 07:57:22 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:22 remove libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:22 purge libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1 <none>
2016-02-27 07:57:22 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:22 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:23 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:23 status config-files libavutil51:i386 4:0.8.10-0ubuntu0.12.04.1
2016-02-27 07:57:23 status not-installed libavutil51:i386 <none>
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 remove libbabl-0.0-0:i386 0.0.22-1.1 <none>
2016-02-27 07:57:23 purge libbabl-0.0-0:i386 0.0.22-1.1 <none>
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 status config-files libbabl-0.0-0:i386 0.0.22-1.1
2016-02-27 07:57:23 status not-installed libbabl-0.0-0:i386 <none>
2016-02-27 07:57:23 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:23 remove libbamf0:i386 0.2.126-0ubuntu1 <none>
2016-02-27 07:57:23 purge libbamf0:i386 0.2.126-0ubuntu1 <none>
2016-02-27 07:57:23 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:23 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status not-installed libbamf0:i386 <none>
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 remove libbamf3-0:i386 0.2.126-0ubuntu1 <none>
2016-02-27 07:57:24 purge libbamf3-0:i386 0.2.126-0ubuntu1 <none>
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status config-files libbamf3-0:i386 0.2.126-0ubuntu1
2016-02-27 07:57:24 status not-installed libbamf3-0:i386 <none>
2016-02-27 07:57:24 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 remove libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:57:25 purge libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:57:25 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 status config-files libbind9-80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:25 status not-installed libbind9-80:i386 <none>
2016-02-27 07:57:25 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:25 remove libblas3gf:i386 1.2.20110419-2ubuntu1 <none>
2016-02-27 07:57:25 purge libblas3gf:i386 1.2.20110419-2ubuntu1 <none>
2016-02-27 07:57:25 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:25 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:25 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:25 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:26 status config-files libblas3gf:i386 1.2.20110419-2ubuntu1
2016-02-27 07:57:26 status not-installed libblas3gf:i386 <none>
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 remove libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:26 purge libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-filesystem1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status not-installed libboost-filesystem1.46.1:i386 <none>
2016-02-27 07:57:26 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 remove libboost-regex1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:26 purge libboost-regex1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:26 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:26 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-regex1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status not-installed libboost-regex1.46.1:i386 <none>
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 remove libboost-serialization1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:27 purge libboost-serialization1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:27 status config-files libboost-serialization1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status not-installed libboost-serialization1.46.1:i386 <none>
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 remove libboost-system1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:28 purge libboost-system1.46.1:i386 1.46.1-7ubuntu3 <none>
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status config-files libboost-system1.46.1:i386 1.46.1-7ubuntu3
2016-02-27 07:57:28 status not-installed libboost-system1.46.1:i386 <none>
2016-02-27 07:57:28 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:28 remove libbrlapi0.5:i386 4.3-1ubuntu5 <none>
2016-02-27 07:57:28 purge libbrlapi0.5:i386 4.3-1ubuntu5 <none>
2016-02-27 07:57:28 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:28 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:28 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:28 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:29 status config-files libbrlapi0.5:i386 4.3-1ubuntu5
2016-02-27 07:57:29 status not-installed libbrlapi0.5:i386 <none>
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 remove libcamel-1.2-29:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:29 purge libcamel-1.2-29:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 status config-files libcamel-1.2-29:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:29 status not-installed libcamel-1.2-29:i386 <none>
2016-02-27 07:57:29 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:29 remove libcelt0-0:i386 0.7.1-1 <none>
2016-02-27 07:57:29 purge libcelt0-0:i386 0.7.1-1 <none>
2016-02-27 07:57:29 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:29 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:30 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:30 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:30 status config-files libcelt0-0:i386 0.7.1-1
2016-02-27 07:57:30 status not-installed libcelt0-0:i386 <none>
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 remove libck-connector0:i386 0.4.5-3.1ubuntu2 <none>
2016-02-27 07:57:30 purge libck-connector0:i386 0.4.5-3.1ubuntu2 <none>
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 status config-files libck-connector0:i386 0.4.5-3.1ubuntu2
2016-02-27 07:57:30 status not-installed libck-connector0:i386 <none>
2016-02-27 07:57:30 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:30 remove libcmis-0.2-0:i386 0.1.0-1 <none>
2016-02-27 07:57:30 purge libcmis-0.2-0:i386 0.1.0-1 <none>
2016-02-27 07:57:30 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:31 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:31 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:31 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:31 status config-files libcmis-0.2-0:i386 0.1.0-1
2016-02-27 07:57:31 status not-installed libcmis-0.2-0:i386 <none>
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 remove libcupsdriver1:i386 1.5.3-0ubuntu8.4 <none>
2016-02-27 07:57:31 purge libcupsdriver1:i386 1.5.3-0ubuntu8.4 <none>
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 status config-files libcupsdriver1:i386 1.5.3-0ubuntu8.4
2016-02-27 07:57:31 status not-installed libcupsdriver1:i386 <none>
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 remove libcurl3-nss:i386 7.35.0-1ubuntu2 <none>
2016-02-27 07:57:32 purge libcurl3-nss:i386 7.35.0-1ubuntu2 <none>
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 status config-files libcurl3-nss:i386 7.35.0-1ubuntu2
2016-02-27 07:57:32 status not-installed libcurl3-nss:i386 <none>
2016-02-27 07:57:32 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:32 remove libdb5.1:i386 5.1.29-7ubuntu1 <none>
2016-02-27 07:57:32 purge libdb5.1:i386 5.1.29-7ubuntu1 <none>
2016-02-27 07:57:32 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:32 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:33 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:33 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:33 status config-files libdb5.1:i386 5.1.29-7ubuntu1
2016-02-27 07:57:33 status not-installed libdb5.1:i386 <none>
2016-02-27 07:57:33 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:33 remove libdconf-dbus-1-0:i386 0.20.0-1 <none>
2016-02-27 07:57:33 purge libdconf-dbus-1-0:i386 0.20.0-1 <none>
2016-02-27 07:57:33 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:33 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:33 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:33 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:34 status config-files libdconf-dbus-1-0:i386 0.20.0-1
2016-02-27 07:57:34 status not-installed libdconf-dbus-1-0:i386 <none>
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 remove libdconf-qt0:i386 0.0.0.110722-0ubuntu4 <none>
2016-02-27 07:57:34 purge libdconf-qt0:i386 0.0.0.110722-0ubuntu4 <none>
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 status config-files libdconf-qt0:i386 0.0.0.110722-0ubuntu4
2016-02-27 07:57:34 status not-installed libdconf-qt0:i386 <none>
2016-02-27 07:57:34 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:34 remove libdconf0:i386 0.12.0-0ubuntu1.1 <none>
2016-02-27 07:57:34 purge libdconf0:i386 0.12.0-0ubuntu1.1 <none>
2016-02-27 07:57:34 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:34 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:35 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:35 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:35 status config-files libdconf0:i386 0.12.0-0ubuntu1.1
2016-02-27 07:57:35 status not-installed libdconf0:i386 <none>
2016-02-27 07:57:35 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:35 remove libdirac-decoder0:i386 1.0.2-4build1 <none>
2016-02-27 07:57:35 purge libdirac-decoder0:i386 1.0.2-4build1 <none>
2016-02-27 07:57:35 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:35 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:36 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:36 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:36 status config-files libdirac-decoder0:i386 1.0.2-4build1
2016-02-27 07:57:36 status not-installed libdirac-decoder0:i386 <none>
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 remove libdiscid0:i386 0.6.1-2 <none>
2016-02-27 07:57:36 purge libdiscid0:i386 0.6.1-2 <none>
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 status config-files libdiscid0:i386 0.6.1-2
2016-02-27 07:57:36 status not-installed libdiscid0:i386 <none>
2016-02-27 07:57:36 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:36 remove libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:57:36 purge libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:57:36 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:37 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:37 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:37 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:37 status config-files libdns81:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:57:37 status not-installed libdns81:i386 <none>
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 remove libdotconf1.0:i386 1.0.13-3 <none>
2016-02-27 07:57:37 purge libdotconf1.0:i386 1.0.13-3 <none>
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 status config-files libdotconf1.0:i386 1.0.13-3
2016-02-27 07:57:37 status not-installed libdotconf1.0:i386 <none>
2016-02-27 07:57:37 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 remove libdrm-nouveau1a:i386 2.4.52-1~precise1 <none>
2016-02-27 07:57:38 purge libdrm-nouveau1a:i386 2.4.52-1~precise1 <none>
2016-02-27 07:57:38 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 status config-files libdrm-nouveau1a:i386 2.4.52-1~precise1
2016-02-27 07:57:38 status not-installed libdrm-nouveau1a:i386 <none>
2016-02-27 07:57:38 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:38 remove libdvbpsi7:i386 0.2.2-1 <none>
2016-02-27 07:57:38 purge libdvbpsi7:i386 0.2.2-1 <none>
2016-02-27 07:57:38 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:38 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:38 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:38 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:39 status config-files libdvbpsi7:i386 0.2.2-1
2016-02-27 07:57:39 status not-installed libdvbpsi7:i386 <none>
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 remove libebackend-1.2-1:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:39 purge libebackend-1.2-1:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 status config-files libebackend-1.2-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:39 status not-installed libebackend-1.2-1:i386 <none>
2016-02-27 07:57:39 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:39 remove libebml3:i386 1.2.2-2 <none>
2016-02-27 07:57:39 purge libebml3:i386 1.2.2-2 <none>
2016-02-27 07:57:39 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:39 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:40 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:40 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:40 status config-files libebml3:i386 1.2.2-2
2016-02-27 07:57:40 status not-installed libebml3:i386 <none>
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 remove libebook-1.2-12:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:40 purge libebook-1.2-12:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 status config-files libebook-1.2-12:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:40 status not-installed libebook-1.2-12:i386 <none>
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 remove libecal-1.2-10:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:41 purge libecal-1.2-10:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libecal-1.2-10:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status not-installed libecal-1.2-10:i386 <none>
2016-02-27 07:57:41 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 remove libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:41 purge libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:41 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:41 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedata-book-1.2-11:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status not-installed libedata-book-1.2-11:i386 <none>
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 remove libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:42 purge libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedata-cal-1.2-13:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status not-installed libedata-cal-1.2-13:i386 <none>
2016-02-27 07:57:42 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 remove libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:42 purge libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:42 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:42 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserver-1.2-15:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status not-installed libedataserver-1.2-15:i386 <none>
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 remove libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:43 purge libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1 <none>
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status config-files libedataserverui-3.0-1:i386 3.2.3-0ubuntu7.1
2016-02-27 07:57:43 status not-installed libedataserverui-3.0-1:i386 <none>
2016-02-27 07:57:43 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 remove libevince3-3:i386 3.4.0-0ubuntu1.7 <none>
2016-02-27 07:57:44 purge libevince3-3:i386 3.4.0-0ubuntu1.7 <none>
2016-02-27 07:57:44 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 status config-files libevince3-3:i386 3.4.0-0ubuntu1.7
2016-02-27 07:57:44 status not-installed libevince3-3:i386 <none>
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 remove libexiv2-11:i386 0.22-2 <none>
2016-02-27 07:57:44 purge libexiv2-11:i386 0.22-2 <none>
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 status config-files libexiv2-11:i386 0.22-2
2016-02-27 07:57:44 status not-installed libexiv2-11:i386 <none>
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 remove libexttextcat0:i386 3.2.0-1ubuntu1 <none>
2016-02-27 07:57:45 purge libexttextcat0:i386 3.2.0-1ubuntu1 <none>
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 status config-files libexttextcat0:i386 3.2.0-1ubuntu1
2016-02-27 07:57:45 status not-installed libexttextcat0:i386 <none>
2016-02-27 07:57:45 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:45 remove libfftw3-long3:i386 3.3.3-7ubuntu3 <none>
2016-02-27 07:57:45 purge libfftw3-long3:i386 3.3.3-7ubuntu3 <none>
2016-02-27 07:57:45 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:45 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:45 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:45 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:46 status config-files libfftw3-long3:i386 3.3.3-7ubuntu3
2016-02-27 07:57:46 status not-installed libfftw3-long3:i386 <none>
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 remove libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2 <none>
2016-02-27 07:57:46 purge libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2 <none>
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 status config-files libgd2-xpm:i386 2.0.36~rc1~dfsg-6ubuntu2
2016-02-27 07:57:46 status not-installed libgd2-xpm:i386 <none>
2016-02-27 07:57:46 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:46 remove libgdu-gtk0:i386 3.0.2-2ubuntu7 <none>
2016-02-27 07:57:46 purge libgdu-gtk0:i386 3.0.2-2ubuntu7 <none>
2016-02-27 07:57:46 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:46 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu-gtk0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status not-installed libgdu-gtk0:i386 <none>
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 remove libgdu0:i386 3.0.2-2ubuntu7 <none>
2016-02-27 07:57:47 purge libgdu0:i386 3.0.2-2ubuntu7 <none>
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status config-files libgdu0:i386 3.0.2-2ubuntu7
2016-02-27 07:57:47 status not-installed libgdu0:i386 <none>
2016-02-27 07:57:47 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 remove libgegl-0.0-0:i386 0.0.22-2ubuntu3 <none>
2016-02-27 07:57:48 purge libgegl-0.0-0:i386 0.0.22-2ubuntu3 <none>
2016-02-27 07:57:48 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 status config-files libgegl-0.0-0:i386 0.0.22-2ubuntu3
2016-02-27 07:57:48 status not-installed libgegl-0.0-0:i386 <none>
2016-02-27 07:57:48 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:48 remove libgexiv2-1:i386 0.4.1-1build1 <none>
2016-02-27 07:57:48 purge libgexiv2-1:i386 0.4.1-1build1 <none>
2016-02-27 07:57:48 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:48 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:48 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:48 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:49 status config-files libgexiv2-1:i386 0.4.1-1build1
2016-02-27 07:57:49 status not-installed libgexiv2-1:i386 <none>
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 remove libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:49 purge libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:49 status not-installed libgl1-mesa-dri-lts-raring:i386 <none>
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:49 remove libgl1-mesa-dri-lts-trusty:i386 3:6 <none>
2016-02-27 07:57:49 purge libgl1-mesa-dri-lts-trusty:i386 3:6 <none>
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:49 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:50 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:50 status config-files libgl1-mesa-dri-lts-trusty:i386 3:6
2016-02-27 07:57:50 status not-installed libgl1-mesa-dri-lts-trusty:i386 <none>
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 remove libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:50 purge libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 status config-files libgl1-mesa-glx-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 status not-installed libgl1-mesa-glx-lts-raring:i386 <none>
2016-02-27 07:57:50 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:50 remove libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:50 purge libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:57:50 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:51 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:51 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:51 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:51 status config-files libglapi-mesa-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:57:51 status not-installed libglapi-mesa-lts-raring:i386 <none>
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 remove libglew1.6:i386 1.6.0-4 <none>
2016-02-27 07:57:51 purge libglew1.6:i386 1.6.0-4 <none>
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 status config-files libglew1.6:i386 1.6.0-4
2016-02-27 07:57:51 status not-installed libglew1.6:i386 <none>
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 remove libglewmx1.6:i386 1.6.0-4 <none>
2016-02-27 07:57:52 purge libglewmx1.6:i386 1.6.0-4 <none>
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 status config-files libglewmx1.6:i386 1.6.0-4
2016-02-27 07:57:52 status not-installed libglewmx1.6:i386 <none>
2016-02-27 07:57:52 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:52 remove libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1 <none>
2016-02-27 07:57:52 purge libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1 <none>
2016-02-27 07:57:52 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:52 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:52 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:52 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:53 status config-files libgnome-bluetooth8:i386 3.2.2-0ubuntu5.1
2016-02-27 07:57:53 status not-installed libgnome-bluetooth8:i386 <none>
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 remove libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2 <none>
2016-02-27 07:57:53 purge libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2 <none>
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 status config-files libgnome-desktop-3-2:i386 3.4.2-0ubuntu0.2
2016-02-27 07:57:53 status not-installed libgnome-desktop-3-2:i386 <none>
2016-02-27 07:57:53 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:53 remove libgnome-menu2:i386 3.0.1-0ubuntu9 <none>
2016-02-27 07:57:53 purge libgnome-menu2:i386 3.0.1-0ubuntu9 <none>
2016-02-27 07:57:53 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:53 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:54 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:54 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:54 status config-files libgnome-menu2:i386 3.0.1-0ubuntu9
2016-02-27 07:57:54 status not-installed libgnome-menu2:i386 <none>
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 remove libgnomekbd7:i386 3.4.0.2-1ubuntu0.1 <none>
2016-02-27 07:57:54 purge libgnomekbd7:i386 3.4.0.2-1ubuntu0.1 <none>
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 status config-files libgnomekbd7:i386 3.4.0.2-1ubuntu0.1
2016-02-27 07:57:54 status not-installed libgnomekbd7:i386 <none>
2016-02-27 07:57:54 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:54 remove libgoa-1.0-0:i386 3.4.0-0ubuntu1.1 <none>
2016-02-27 07:57:54 purge libgoa-1.0-0:i386 3.4.0-0ubuntu1.1 <none>
2016-02-27 07:57:54 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:55 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:55 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:55 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:55 status config-files libgoa-1.0-0:i386 3.4.0-0ubuntu1.1
2016-02-27 07:57:55 status not-installed libgoa-1.0-0:i386 <none>
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 remove libgpac1:i386 0.4.5+svn3462~dfsg0-1 <none>
2016-02-27 07:57:55 purge libgpac1:i386 0.4.5+svn3462~dfsg0-1 <none>
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 status config-files libgpac1:i386 0.4.5+svn3462~dfsg0-1
2016-02-27 07:57:55 status not-installed libgpac1:i386 <none>
2016-02-27 07:57:55 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 remove libgphoto2-2:i386 2.4.13-1ubuntu1.2 <none>
2016-02-27 07:57:56 purge libgphoto2-2:i386 2.4.13-1ubuntu1.2 <none>
2016-02-27 07:57:56 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-2:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status not-installed libgphoto2-2:i386 <none>
2016-02-27 07:57:56 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 remove libgphoto2-port0:i386 2.4.13-1ubuntu1.2 <none>
2016-02-27 07:57:56 purge libgphoto2-port0:i386 2.4.13-1ubuntu1.2 <none>
2016-02-27 07:57:56 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:56 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:57 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:57 status config-files libgphoto2-port0:i386 2.4.13-1ubuntu1.2
2016-02-27 07:57:57 status not-installed libgphoto2-port0:i386 <none>
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 remove libgrail5:i386 3.0.6-0ubuntu0.12.04.01 <none>
2016-02-27 07:57:57 purge libgrail5:i386 3.0.6-0ubuntu0.12.04.01 <none>
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 status config-files libgrail5:i386 3.0.6-0ubuntu0.12.04.01
2016-02-27 07:57:57 status not-installed libgrail5:i386 <none>
2016-02-27 07:57:57 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:57 remove libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1 <none>
2016-02-27 07:57:57 purge libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1 <none>
2016-02-27 07:57:57 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:57 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:58 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:58 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:58 status config-files libgtksourceview-3.0-0:i386 3.4.2-0ubuntu1
2016-02-27 07:57:58 status not-installed libgtksourceview-3.0-0:i386 <none>
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 remove libgtkspell-3-0:i386 3.0.0~hg20110814-1 <none>
2016-02-27 07:57:58 purge libgtkspell-3-0:i386 3.0.0~hg20110814-1 <none>
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 status config-files libgtkspell-3-0:i386 3.0.0~hg20110814-1
2016-02-27 07:57:58 status not-installed libgtkspell-3-0:i386 <none>
2016-02-27 07:57:58 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 remove libgweather-3-0:i386 3.4.1-0ubuntu1 <none>
2016-02-27 07:57:59 purge libgweather-3-0:i386 3.4.1-0ubuntu1 <none>
2016-02-27 07:57:59 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 status config-files libgweather-3-0:i386 3.4.1-0ubuntu1
2016-02-27 07:57:59 status not-installed libgweather-3-0:i386 <none>
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 remove libgwibber-gtk2:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:57:59 purge libgwibber-gtk2:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 status config-files libgwibber-gtk2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:57:59 status not-installed libgwibber-gtk2:i386 <none>
2016-02-27 07:57:59 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 remove libgwibber2:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:58:00 purge libgwibber2:i386 3.4.2-0ubuntu2.3 <none>
2016-02-27 07:58:00 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 status config-files libgwibber2:i386 3.4.2-0ubuntu2.3
2016-02-27 07:58:00 status not-installed libgwibber2:i386 <none>
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:00 remove libibus-1.0-0:i386 1.4.1-3ubuntu1 <none>
2016-02-27 07:58:00 purge libibus-1.0-0:i386 1.4.1-3ubuntu1 <none>
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:00 status config-files libibus-1.0-0:i386 1.4.1-3ubuntu1
2016-02-27 07:58:01 status not-installed libibus-1.0-0:i386 <none>
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 remove libical0:i386 0.48-1ubuntu3 <none>
2016-02-27 07:58:01 purge libical0:i386 0.48-1ubuntu3 <none>
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 status config-files libical0:i386 0.48-1ubuntu3
2016-02-27 07:58:01 status not-installed libical0:i386 <none>
2016-02-27 07:58:01 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:01 remove libicu48:i386 4.8.1.1-3ubuntu0.1 <none>
2016-02-27 07:58:01 purge libicu48:i386 4.8.1.1-3ubuntu0.1 <none>
2016-02-27 07:58:01 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:01 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:02 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:02 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:02 status config-files libicu48:i386 4.8.1.1-3ubuntu0.1
2016-02-27 07:58:02 status not-installed libicu48:i386 <none>
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 remove libimobiledevice2:i386 1.1.1-4 <none>
2016-02-27 07:58:02 purge libimobiledevice2:i386 1.1.1-4 <none>
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 status config-files libimobiledevice2:i386 1.1.1-4
2016-02-27 07:58:02 status not-installed libimobiledevice2:i386 <none>
2016-02-27 07:58:02 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:02 remove libindicate-gtk3:i386 0.6.92-0ubuntu1 <none>
2016-02-27 07:58:02 purge libindicate-gtk3:i386 0.6.92-0ubuntu1 <none>
2016-02-27 07:58:02 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:03 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:03 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:03 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:03 status config-files libindicate-gtk3:i386 0.6.92-0ubuntu1
2016-02-27 07:58:03 status not-installed libindicate-gtk3:i386 <none>
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 remove libindicate5:i386 12.10.1-0ubuntu3 <none>
2016-02-27 07:58:03 purge libindicate5:i386 12.10.1-0ubuntu3 <none>
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 status config-files libindicate5:i386 12.10.1-0ubuntu3
2016-02-27 07:58:03 status not-installed libindicate5:i386 <none>
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 remove libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2 <none>
2016-02-27 07:58:04 purge libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2 <none>
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 status config-files libindicator-messages-status-provider1:i386 0.6.0-0ubuntu2
2016-02-27 07:58:04 status not-installed libindicator-messages-status-provider1:i386 <none>
2016-02-27 07:58:04 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:04 remove libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:04 purge libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:04 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisc83:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status not-installed libisc83:i386 <none>
2016-02-27 07:58:05 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 remove libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:05 purge libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:05 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:05 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccc80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status not-installed libisccc80:i386 <none>
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 remove libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:06 purge libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status config-files libisccfg82:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:06 status not-installed libisccfg82:i386 <none>
2016-02-27 07:58:06 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:06 remove libkpathsea5:i386 2009-11ubuntu2 <none>
2016-02-27 07:58:06 purge libkpathsea5:i386 2009-11ubuntu2 <none>
2016-02-27 07:58:06 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:06 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:07 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:07 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:07 status config-files libkpathsea5:i386 2009-11ubuntu2
2016-02-27 07:58:07 status not-installed libkpathsea5:i386 <none>
2016-02-27 07:58:07 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:07 remove liblapack3gf:i386 3.3.1-1 <none>
2016-02-27 07:58:07 purge liblapack3gf:i386 3.3.1-1 <none>
2016-02-27 07:58:07 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:07 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:07 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:08 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:09 status config-files liblapack3gf:i386 3.3.1-1
2016-02-27 07:58:09 status not-installed liblapack3gf:i386 <none>
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 remove liblaunchpad-integration-3.0-1:i386 0.1.56.1 <none>
2016-02-27 07:58:09 purge liblaunchpad-integration-3.0-1:i386 0.1.56.1 <none>
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 status config-files liblaunchpad-integration-3.0-1:i386 0.1.56.1
2016-02-27 07:58:09 status not-installed liblaunchpad-integration-3.0-1:i386 <none>
2016-02-27 07:58:09 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:09 remove libleptonica:i386 1.69-2 <none>
2016-02-27 07:58:09 purge libleptonica:i386 1.69-2 <none>
2016-02-27 07:58:09 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:09 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:09 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:10 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:10 status config-files libleptonica:i386 1.69-2
2016-02-27 07:58:10 status not-installed libleptonica:i386 <none>
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 remove libllvm3.2:i386 3.2-2ubuntu5~precise1 <none>
2016-02-27 07:58:10 purge libllvm3.2:i386 3.2-2ubuntu5~precise1 <none>
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 status config-files libllvm3.2:i386 3.2-2ubuntu5~precise1
2016-02-27 07:58:10 status not-installed libllvm3.2:i386 <none>
2016-02-27 07:58:10 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:10 remove liblua5.1-0:i386 5.1.5-5 <none>
2016-02-27 07:58:10 purge liblua5.1-0:i386 5.1.5-5 <none>
2016-02-27 07:58:10 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:10 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:11 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:11 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:11 status config-files liblua5.1-0:i386 5.1.5-5
2016-02-27 07:58:11 status not-installed liblua5.1-0:i386 <none>
2016-02-27 07:58:11 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:11 remove liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:11 purge liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8 <none>
2016-02-27 07:58:11 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:11 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:11 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:11 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:12 status config-files liblwres80:i386 1:9.8.1.dfsg.P1-4ubuntu0.8
2016-02-27 07:58:12 status not-installed liblwres80:i386 <none>
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 remove libmatroska5:i386 1.3.0-1 <none>
2016-02-27 07:58:12 purge libmatroska5:i386 1.3.0-1 <none>
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 status config-files libmatroska5:i386 1.3.0-1
2016-02-27 07:58:12 status not-installed libmatroska5:i386 <none>
2016-02-27 07:58:12 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:12 remove libmetacity-private0:i386 1:2.34.1-1ubuntu11 <none>
2016-02-27 07:58:12 purge libmetacity-private0:i386 1:2.34.1-1ubuntu11 <none>
2016-02-27 07:58:12 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:12 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:12 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:13 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:13 status config-files libmetacity-private0:i386 1:2.34.1-1ubuntu11
2016-02-27 07:58:13 status not-installed libmetacity-private0:i386 <none>
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 remove libmikmod2:i386 3.1.12-2 <none>
2016-02-27 07:58:13 purge libmikmod2:i386 3.1.12-2 <none>
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 status config-files libmikmod2:i386 3.1.12-2
2016-02-27 07:58:13 status not-installed libmikmod2:i386 <none>
2016-02-27 07:58:13 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 remove libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7 <none>
2016-02-27 07:58:14 purge libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7 <none>
2016-02-27 07:58:14 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 status config-files libmjpegtools-1.9:i386 1:1.9.0-0.5ubuntu7
2016-02-27 07:58:14 status not-installed libmjpegtools-1.9:i386 <none>
2016-02-27 07:58:14 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:14 remove libmng1:i386 1.0.10-3 <none>
2016-02-27 07:58:14 purge libmng1:i386 1.0.10-3 <none>
2016-02-27 07:58:14 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:14 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:14 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:14 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:15 status config-files libmng1:i386 1.0.10-3
2016-02-27 07:58:15 status not-installed libmng1:i386 <none>
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 remove libmpc2:i386 0.9-4 <none>
2016-02-27 07:58:15 purge libmpc2:i386 0.9-4 <none>
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 status config-files libmpc2:i386 0.9-4
2016-02-27 07:58:15 status not-installed libmpc2:i386 <none>
2016-02-27 07:58:15 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:15 remove libmpdec2:i386 2.4.0-6 <none>
2016-02-27 07:58:15 purge libmpdec2:i386 2.4.0-6 <none>
2016-02-27 07:58:15 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:15 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:15 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:16 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:16 status config-files libmpdec2:i386 2.4.0-6
2016-02-27 07:58:16 status not-installed libmpdec2:i386 <none>
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 remove libmusicbrainz3-6:i386 3.0.2-2.1 <none>
2016-02-27 07:58:16 purge libmusicbrainz3-6:i386 3.0.2-2.1 <none>
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 status config-files libmusicbrainz3-6:i386 3.0.2-2.1
2016-02-27 07:58:16 status not-installed libmusicbrainz3-6:i386 <none>
2016-02-27 07:58:16 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:16 remove libnux-2.0-0:i386 2.14.1-0ubuntu1 <none>
2016-02-27 07:58:16 purge libnux-2.0-0:i386 2.14.1-0ubuntu1 <none>
2016-02-27 07:58:16 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:16 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:17 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:17 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:17 status config-files libnux-2.0-0:i386 2.14.1-0ubuntu1
2016-02-27 07:58:17 status not-installed libnux-2.0-0:i386 <none>
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 remove liboggz2:i386 1.1.1-1 <none>
2016-02-27 07:58:17 purge liboggz2:i386 1.1.1-1 <none>
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 status config-files liboggz2:i386 1.1.1-1
2016-02-27 07:58:17 status not-installed liboggz2:i386 <none>
2016-02-27 07:58:17 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 remove libogmrip1:i386 0.13.6-0ubuntu4 <none>
2016-02-27 07:58:18 purge libogmrip1:i386 0.13.6-0ubuntu4 <none>
2016-02-27 07:58:18 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 status config-files libogmrip1:i386 0.13.6-0ubuntu4
2016-02-27 07:58:18 status not-installed libogmrip1:i386 <none>
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 remove libopenspc0:i386 0.3.99a-2 <none>
2016-02-27 07:58:18 purge libopenspc0:i386 0.3.99a-2 <none>
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 status config-files libopenspc0:i386 0.3.99a-2
2016-02-27 07:58:18 status not-installed libopenspc0:i386 <none>
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 remove liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1 <none>
2016-02-27 07:58:19 purge liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1 <none>
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status config-files liboverlay-scrollbar-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status not-installed liboverlay-scrollbar-0.2-0:i386 <none>
2016-02-27 07:58:19 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 remove liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1 <none>
2016-02-27 07:58:19 purge liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1 <none>
2016-02-27 07:58:19 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:19 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:20 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:20 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:20 status config-files liboverlay-scrollbar3-0.2-0:i386 0.2.16-0ubuntu1.1
2016-02-27 07:58:20 status not-installed liboverlay-scrollbar3-0.2-0:i386 <none>
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 remove libpackagekit-glib2-14:i386 0.7.2-4ubuntu3 <none>
2016-02-27 07:58:20 purge libpackagekit-glib2-14:i386 0.7.2-4ubuntu3 <none>
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 status config-files libpackagekit-glib2-14:i386 0.7.2-4ubuntu3
2016-02-27 07:58:20 status not-installed libpackagekit-glib2-14:i386 <none>
2016-02-27 07:58:20 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:20 remove libpoppler19:i386 0.18.4-1ubuntu3.1 <none>
2016-02-27 07:58:20 purge libpoppler19:i386 0.18.4-1ubuntu3.1 <none>
2016-02-27 07:58:20 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:21 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:21 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:21 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:21 status config-files libpoppler19:i386 0.18.4-1ubuntu3.1
2016-02-27 07:58:21 status not-installed libpoppler19:i386 <none>
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 remove libportmidi0:i386 1:200-0ubuntu1.12.04.2 <none>
2016-02-27 07:58:21 purge libportmidi0:i386 1:200-0ubuntu1.12.04.2 <none>
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 status config-files libportmidi0:i386 1:200-0ubuntu1.12.04.2
2016-02-27 07:58:21 status not-installed libportmidi0:i386 <none>
2016-02-27 07:58:21 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 remove libprotobuf7:i386 2.4.1-1ubuntu2 <none>
2016-02-27 07:58:22 purge libprotobuf7:i386 2.4.1-1ubuntu2 <none>
2016-02-27 07:58:22 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotobuf7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status not-installed libprotobuf7:i386 <none>
2016-02-27 07:58:22 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 remove libprotoc7:i386 2.4.1-1ubuntu2 <none>
2016-02-27 07:58:22 purge libprotoc7:i386 2.4.1-1ubuntu2 <none>
2016-02-27 07:58:22 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:22 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:23 status config-files libprotoc7:i386 2.4.1-1ubuntu2
2016-02-27 07:58:23 status not-installed libprotoc7:i386 <none>
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 remove libprotoc8:i386 2.5.0-9ubuntu1 <none>
2016-02-27 07:58:23 purge libprotoc8:i386 2.5.0-9ubuntu1 <none>
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 status config-files libprotoc8:i386 2.5.0-9ubuntu1
2016-02-27 07:58:23 status not-installed libprotoc8:i386 <none>
2016-02-27 07:58:23 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:23 remove libpth20:i386 2.0.7-19ubuntu1 <none>
2016-02-27 07:58:23 purge libpth20:i386 2.0.7-19ubuntu1 <none>
2016-02-27 07:58:23 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:23 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:23 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:24 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:24 status config-files libpth20:i386 2.0.7-19ubuntu1
2016-02-27 07:58:24 status not-installed libpth20:i386 <none>
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 remove libqtbamf1:i386 0.2.4-0ubuntu2 <none>
2016-02-27 07:58:24 purge libqtbamf1:i386 0.2.4-0ubuntu2 <none>
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 status config-files libqtbamf1:i386 0.2.4-0ubuntu2
2016-02-27 07:58:24 status not-installed libqtbamf1:i386 <none>
2016-02-27 07:58:24 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:24 remove libqtdee2:i386 0.2.4-0ubuntu1 <none>
2016-02-27 07:58:25 purge libqtdee2:i386 0.2.4-0ubuntu1 <none>
2016-02-27 07:58:25 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:25 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:25 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:25 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:25 status config-files libqtdee2:i386 0.2.4-0ubuntu1
2016-02-27 07:58:25 status not-installed libqtdee2:i386 <none>
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 remove libqtgconf1:i386 0.1-0ubuntu5 <none>
2016-02-27 07:58:25 purge libqtgconf1:i386 0.1-0ubuntu5 <none>
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 status config-files libqtgconf1:i386 0.1-0ubuntu5
2016-02-27 07:58:25 status not-installed libqtgconf1:i386 <none>
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 remove libquvi7:i386 0.4.1-1ubuntu3 <none>
2016-02-27 07:58:26 purge libquvi7:i386 0.4.1-1ubuntu3 <none>
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 status config-files libquvi7:i386 0.4.1-1ubuntu3
2016-02-27 07:58:26 status not-installed libquvi7:i386 <none>
2016-02-27 07:58:26 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:26 remove libraw5:i386 0.14.4-0ubuntu2.2 <none>
2016-02-27 07:58:26 purge libraw5:i386 0.14.4-0ubuntu2.2 <none>
2016-02-27 07:58:26 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:26 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:26 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:26 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:27 status config-files libraw5:i386 0.14.4-0ubuntu2.2
2016-02-27 07:58:27 status not-installed libraw5:i386 <none>
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 remove librhythmbox-core5:i386 2.96-0ubuntu4.3 <none>
2016-02-27 07:58:27 purge librhythmbox-core5:i386 2.96-0ubuntu4.3 <none>
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 status config-files librhythmbox-core5:i386 2.96-0ubuntu4.3
2016-02-27 07:58:27 status not-installed librhythmbox-core5:i386 <none>
2016-02-27 07:58:27 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:27 remove libsdl-gfx1.2-4:i386 2.0.23-1 <none>
2016-02-27 07:58:27 purge libsdl-gfx1.2-4:i386 2.0.23-1 <none>
2016-02-27 07:58:27 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:27 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:28 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:28 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:28 status config-files libsdl-gfx1.2-4:i386 2.0.23-1
2016-02-27 07:58:28 status not-installed libsdl-gfx1.2-4:i386 <none>
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 remove libsdl-mixer1.2:i386 1.2.11-7 <none>
2016-02-27 07:58:28 purge libsdl-mixer1.2:i386 1.2.11-7 <none>
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 status config-files libsdl-mixer1.2:i386 1.2.11-7
2016-02-27 07:58:28 status not-installed libsdl-mixer1.2:i386 <none>
2016-02-27 07:58:28 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 remove libsdl-net1.2:i386 1.2.7-5 <none>
2016-02-27 07:58:29 purge libsdl-net1.2:i386 1.2.7-5 <none>
2016-02-27 07:58:29 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 status config-files libsdl-net1.2:i386 1.2.7-5
2016-02-27 07:58:29 status not-installed libsdl-net1.2:i386 <none>
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:29 remove libsdl-pango1:i386 0.1.2-4 <none>
2016-02-27 07:58:29 purge libsdl-pango1:i386 0.1.2-4 <none>
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:29 status config-files libsdl-pango1:i386 0.1.2-4
2016-02-27 07:58:30 status not-installed libsdl-pango1:i386 <none>
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 remove libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1 <none>
2016-02-27 07:58:30 purge libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1 <none>
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 status config-files libsdl-ttf2.0-0:i386 2.0.9-1.1ubuntu1
2016-02-27 07:58:30 status not-installed libsdl-ttf2.0-0:i386 <none>
2016-02-27 07:58:30 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:30 remove libslp1:i386 1.2.1-9 <none>
2016-02-27 07:58:30 purge libslp1:i386 1.2.1-9 <none>
2016-02-27 07:58:30 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:30 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:30 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:31 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:31 status config-files libslp1:i386 1.2.1-9
2016-02-27 07:58:31 status not-installed libslp1:i386 <none>
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 remove libsmpeg0:i386 0.4.5+cvs20030824-4 <none>
2016-02-27 07:58:31 purge libsmpeg0:i386 0.4.5+cvs20030824-4 <none>
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 status config-files libsmpeg0:i386 0.4.5+cvs20030824-4
2016-02-27 07:58:31 status not-installed libsmpeg0:i386 <none>
2016-02-27 07:58:31 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:31 remove libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2 <none>
2016-02-27 07:58:31 purge libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2 <none>
2016-02-27 07:58:31 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:31 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:32 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:32 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:32 status config-files libsnmp15:i386 5.4.3~dfsg-2.4ubuntu1.2
2016-02-27 07:58:32 status not-installed libsnmp15:i386 <none>
2016-02-27 07:58:32 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:32 remove libstlport4.6ldbl:i386 4.6.2-7 <none>
2016-02-27 07:58:32 purge libstlport4.6ldbl:i386 4.6.2-7 <none>
2016-02-27 07:58:32 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:32 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:32 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:33 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:33 status config-files libstlport4.6ldbl:i386 4.6.2-7
2016-02-27 07:58:33 status not-installed libstlport4.6ldbl:i386 <none>
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 remove libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:58:33 purge libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 status config-files libsyncdaemon-1.0-1:i386 3.0.2-0ubuntu2.2
2016-02-27 07:58:33 status not-installed libsyncdaemon-1.0-1:i386 <none>
2016-02-27 07:58:33 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:33 remove libsysfs2:i386 2.1.0+repack-3ubuntu1 <none>
2016-02-27 07:58:33 purge libsysfs2:i386 2.1.0+repack-3ubuntu1 <none>
2016-02-27 07:58:33 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:34 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:34 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:34 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:34 status config-files libsysfs2:i386 2.1.0+repack-3ubuntu1
2016-02-27 07:58:34 status not-installed libsysfs2:i386 <none>
2016-02-27 07:58:34 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:34 remove libtasn1-3:i386 2.10-1ubuntu1.2 <none>
2016-02-27 07:58:34 purge libtasn1-3:i386 2.10-1ubuntu1.2 <none>
2016-02-27 07:58:34 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:34 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:34 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:34 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:35 status config-files libtasn1-3:i386 2.10-1ubuntu1.2
2016-02-27 07:58:35 status not-installed libtasn1-3:i386 <none>
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 remove libtelepathy-farstream2:i386 0.4.0-0ubuntu1 <none>
2016-02-27 07:58:35 purge libtelepathy-farstream2:i386 0.4.0-0ubuntu1 <none>
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status config-files libtelepathy-farstream2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status not-installed libtelepathy-farstream2:i386 <none>
2016-02-27 07:58:35 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 remove libtelepathy-logger2:i386 0.4.0-0ubuntu1 <none>
2016-02-27 07:58:35 purge libtelepathy-logger2:i386 0.4.0-0ubuntu1 <none>
2016-02-27 07:58:35 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:35 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:36 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:36 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:36 status config-files libtelepathy-logger2:i386 0.4.0-0ubuntu1
2016-02-27 07:58:36 status not-installed libtelepathy-logger2:i386 <none>
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 remove libtesseract3:i386 3.02.01-2 <none>
2016-02-27 07:58:36 purge libtesseract3:i386 3.02.01-2 <none>
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 status config-files libtesseract3:i386 3.02.01-2
2016-02-27 07:58:36 status not-installed libtesseract3:i386 <none>
2016-02-27 07:58:36 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:36 remove libtiff4:i386 3.9.5-2ubuntu1.6 <none>
2016-02-27 07:58:36 purge libtiff4:i386 3.9.5-2ubuntu1.6 <none>
2016-02-27 07:58:36 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:37 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:37 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:37 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:37 status config-files libtiff4:i386 3.9.5-2ubuntu1.6
2016-02-27 07:58:37 status not-installed libtiff4:i386 <none>
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 remove libtotem-plparser17:i386 3.4.1-1 <none>
2016-02-27 07:58:37 purge libtotem-plparser17:i386 3.4.1-1 <none>
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 status config-files libtotem-plparser17:i386 3.4.1-1
2016-02-27 07:58:37 status not-installed libtotem-plparser17:i386 <none>
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 remove libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1 <none>
2016-02-27 07:58:38 purge libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1 <none>
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 status config-files libubuntuoneui-3.0-1:i386 3.0.1-0ubuntu1
2016-02-27 07:58:38 status not-installed libubuntuoneui-3.0-1:i386 <none>
2016-02-27 07:58:38 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:38 remove libudev0:i386 175-0ubuntu9.5 <none>
2016-02-27 07:58:38 purge libudev0:i386 175-0ubuntu9.5 <none>
2016-02-27 07:58:38 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:38 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:38 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:38 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:39 status config-files libudev0:i386 175-0ubuntu9.5
2016-02-27 07:58:39 status not-installed libudev0:i386 <none>
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 remove libunique-3.0-0:i386 3.0.2-2ubuntu1 <none>
2016-02-27 07:58:39 purge libunique-3.0-0:i386 3.0.2-2ubuntu1 <none>
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 status config-files libunique-3.0-0:i386 3.0.2-2ubuntu1
2016-02-27 07:58:39 status not-installed libunique-3.0-0:i386 <none>
2016-02-27 07:58:39 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:39 remove libunity-core-5.0-5:i386 5.20.0-0ubuntu3 <none>
2016-02-27 07:58:39 purge libunity-core-5.0-5:i386 5.20.0-0ubuntu3 <none>
2016-02-27 07:58:39 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:39 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:40 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:40 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:40 status config-files libunity-core-5.0-5:i386 5.20.0-0ubuntu3
2016-02-27 07:58:40 status not-installed libunity-core-5.0-5:i386 <none>
2016-02-27 07:58:40 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:40 remove libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1 <none>
2016-02-27 07:58:40 purge libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1 <none>
2016-02-27 07:58:40 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:40 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:40 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:41 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:41 status config-files libupnp3:i386 1:1.6.6-5.1ubuntu0.12.04.1
2016-02-27 07:58:41 status not-installed libupnp3:i386 <none>
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 remove libupstart1:i386 1.12.1-0ubuntu4.2 <none>
2016-02-27 07:58:41 purge libupstart1:i386 1.12.1-0ubuntu4.2 <none>
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 status config-files libupstart1:i386 1.12.1-0ubuntu4.2
2016-02-27 07:58:41 status not-installed libupstart1:i386 <none>
2016-02-27 07:58:41 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:41 remove libusbmuxd1:i386 1.0.7-2ubuntu0.1 <none>
2016-02-27 07:58:41 purge libusbmuxd1:i386 1.0.7-2ubuntu0.1 <none>
2016-02-27 07:58:41 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:41 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:42 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:42 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:42 status config-files libusbmuxd1:i386 1.0.7-2ubuntu0.1
2016-02-27 07:58:42 status not-installed libusbmuxd1:i386 <none>
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 remove libvlccore5:i386 2.0.8-0ubuntu0.12.04.1 <none>
2016-02-27 07:58:42 purge libvlccore5:i386 2.0.8-0ubuntu0.12.04.1 <none>
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 status config-files libvlccore5:i386 2.0.8-0ubuntu0.12.04.1
2016-02-27 07:58:42 status not-installed libvlccore5:i386 <none>
2016-02-27 07:58:42 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 remove libvte9:i386 1:0.28.2-5ubuntu1 <none>
2016-02-27 07:58:43 purge libvte9:i386 1:0.28.2-5ubuntu1 <none>
2016-02-27 07:58:43 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 status config-files libvte9:i386 1:0.28.2-5ubuntu1
2016-02-27 07:58:43 status not-installed libvte9:i386 <none>
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:43 remove libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:43 purge libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:43 status config-files libwayland-ltst-client0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status not-installed libwayland-ltst-client0:i386 <none>
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 remove libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:44 purge libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status config-files libwayland-ltst-server0:i386 1.4.0-1ubuntu1~precise1
2016-02-27 07:58:44 status not-installed libwayland-ltst-server0:i386 <none>
2016-02-27 07:58:44 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:44 remove libwebp2:i386 0.1.3-2.1ubuntu1 <none>
2016-02-27 07:58:44 purge libwebp2:i386 0.1.3-2.1ubuntu1 <none>
2016-02-27 07:58:44 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:44 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:44 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:45 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:45 status config-files libwebp2:i386 0.1.3-2.1ubuntu1
2016-02-27 07:58:45 status not-installed libwebp2:i386 <none>
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 remove libx264-120:i386 2:0.120.2151+gita3f4407-2 <none>
2016-02-27 07:58:45 purge libx264-120:i386 2:0.120.2151+gita3f4407-2 <none>
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 status config-files libx264-120:i386 2:0.120.2151+gita3f4407-2
2016-02-27 07:58:45 status not-installed libx264-120:i386 <none>
2016-02-27 07:58:45 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:45 remove libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:58:45 purge libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1 <none>
2016-02-27 07:58:45 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:45 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:46 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:46 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:46 status config-files libxatracker1-lts-raring:i386 9.1.7-1ubuntu2~precise1
2016-02-27 07:58:46 status not-installed libxatracker1-lts-raring:i386 <none>
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 remove libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:46 purge libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1 <none>
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 status config-files libxrandr-ltsr2:i386 2:1.4.0-1ubuntu1~precise1
2016-02-27 07:58:46 status not-installed libxrandr-ltsr2:i386 <none>
2016-02-27 07:58:46 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 remove libxrandr-ltst2:i386 2:1.4.2-1~precise1 <none>
2016-02-27 07:58:47 purge libxrandr-ltst2:i386 2:1.4.2-1~precise1 <none>
2016-02-27 07:58:47 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 status config-files libxrandr-ltst2:i386 2:1.4.2-1~precise1
2016-02-27 07:58:47 status not-installed libxrandr-ltst2:i386 <none>
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:47 remove libyajl1:i386 1.0.12-2 <none>
2016-02-27 07:58:47 purge libyajl1:i386 1.0.12-2 <none>
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:47 status config-files libyajl1:i386 1.0.12-2
2016-02-27 07:58:48 status not-installed libyajl1:i386 <none>
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 remove linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1 <none>
2016-02-27 07:58:48 purge linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1 <none>
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 status config-files linux-image-3.8.0-29-generic:i386 3.8.0-29.42~precise1
2016-02-27 07:58:48 status not-installed linux-image-3.8.0-29-generic:i386 <none>
2016-02-27 07:58:48 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:48 remove linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1 <none>
2016-02-27 07:58:48 purge linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1 <none>
2016-02-27 07:58:48 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:48 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-34-generic:i386 3.8.0-34.49~precise1
2016-02-27 07:58:49 status not-installed linux-image-3.8.0-34-generic:i386 <none>
2016-02-27 07:58:49 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:49 remove linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1 <none>
2016-02-27 07:58:49 purge linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1 <none>
2016-02-27 07:58:49 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:49 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:50 status config-files linux-image-3.8.0-35-generic:i386 3.8.0-35.52~precise1
2016-02-27 07:58:50 status not-installed linux-image-3.8.0-35-generic:i386 <none>
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 remove linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1 <none>
2016-02-27 07:58:50 purge linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1 <none>
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 status config-files linux-image-3.8.0-36-generic:i386 3.8.0-36.52~precise1
2016-02-27 07:58:50 status not-installed linux-image-3.8.0-36-generic:i386 <none>
2016-02-27 07:58:50 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 remove linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1 <none>
2016-02-27 07:58:51 purge linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1 <none>
2016-02-27 07:58:51 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-37-generic:i386 3.8.0-37.53~precise1
2016-02-27 07:58:51 status not-installed linux-image-3.8.0-37-generic:i386 <none>
2016-02-27 07:58:51 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:51 remove linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1 <none>
2016-02-27 07:58:51 purge linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1 <none>
2016-02-27 07:58:51 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:51 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-38-generic:i386 3.8.0-38.56~precise1
2016-02-27 07:58:52 status not-installed linux-image-3.8.0-38-generic:i386 <none>
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 remove linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1 <none>
2016-02-27 07:58:52 purge linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1 <none>
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 status config-files linux-image-3.8.0-39-generic:i386 3.8.0-39.58~precise1
2016-02-27 07:58:52 status not-installed linux-image-3.8.0-39-generic:i386 <none>
2016-02-27 07:58:52 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 remove linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1 <none>
2016-02-27 07:58:53 purge linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1 <none>
2016-02-27 07:58:53 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-41-generic:i386 3.8.0-41.60~precise1
2016-02-27 07:58:53 status not-installed linux-image-3.8.0-41-generic:i386 <none>
2016-02-27 07:58:53 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:53 remove linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1 <none>
2016-02-27 07:58:53 purge linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1 <none>
2016-02-27 07:58:53 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:53 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:54 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:54 status config-files linux-image-3.8.0-42-generic:i386 3.8.0-42.63~precise1
2016-02-27 07:58:54 status not-installed linux-image-3.8.0-42-generic:i386 <none>
2016-02-27 07:58:54 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:54 remove linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1 <none>
2016-02-27 07:58:54 purge linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1 <none>
2016-02-27 07:58:54 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:54 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:54 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:55 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:55 status config-files linux-image-3.8.0-44-generic:i386 3.8.0-44.66~precise1
2016-02-27 07:58:55 status not-installed linux-image-3.8.0-44-generic:i386 <none>
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 remove linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60 <none>
2016-02-27 07:58:55 purge linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60 <none>
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-34-generic:i386 3.13.0-34.60
2016-02-27 07:58:55 status not-installed linux-image-extra-3.13.0-34-generic:i386 <none>
2016-02-27 07:58:55 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 remove linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74 <none>
2016-02-27 07:58:56 purge linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74 <none>
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-45-generic:i386 3.13.0-45.74
2016-02-27 07:58:56 status not-installed linux-image-extra-3.13.0-45-generic:i386 <none>
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:56 remove linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106 <none>
2016-02-27 07:58:56 purge linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106 <none>
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:56 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-65-generic:i386 3.13.0-65.106
2016-02-27 07:58:57 status not-installed linux-image-extra-3.13.0-65-generic:i386 <none>
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 remove linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108 <none>
2016-02-27 07:58:57 purge linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108 <none>
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-66-generic:i386 3.13.0-66.108
2016-02-27 07:58:57 status not-installed linux-image-extra-3.13.0-66-generic:i386 <none>
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:57 remove linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110 <none>
2016-02-27 07:58:57 purge linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110 <none>
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:57 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:58 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:58 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:58 status config-files linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 07:58:58 status not-installed linux-image-extra-3.13.0-67-generic:i386 <none>
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 remove mahjongg:i386 1:3.4.1-0ubuntu2.2 <none>
2016-02-27 07:58:58 purge mahjongg:i386 1:3.4.1-0ubuntu2.2 <none>
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 status config-files mahjongg:i386 1:3.4.1-0ubuntu2.2
2016-02-27 07:58:58 status not-installed mahjongg:i386 <none>
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 remove nvidia-common:i386 1:0.2.91.11 <none>
2016-02-27 07:58:59 purge nvidia-common:i386 1:0.2.91.11 <none>
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 status config-files nvidia-common:i386 1:0.2.91.11
2016-02-27 07:58:59 status not-installed nvidia-common:i386 <none>
2016-02-27 07:58:59 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:58:59 remove oggz-tools:i386 1.1.1-1 <none>
2016-02-27 07:58:59 purge oggz-tools:i386 1.1.1-1 <none>
2016-02-27 07:58:59 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:58:59 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:58:59 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:58:59 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:59:00 status config-files oggz-tools:i386 1.1.1-1
2016-02-27 07:59:00 status not-installed oggz-tools:i386 <none>
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 remove oss-compat:all 1 <none>
2016-02-27 07:59:00 purge oss-compat:all 1 <none>
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 status config-files oss-compat:all 1
2016-02-27 07:59:00 status not-installed oss-compat:all <none>
2016-02-27 07:59:00 status config-files pangzero:all 1.3-2
2016-02-27 07:59:00 remove pangzero:all 1.3-2 <none>
2016-02-27 07:59:00 purge pangzero:all 1.3-2 <none>
2016-02-27 07:59:00 status config-files pangzero:all 1.3-2
2016-02-27 07:59:01 status config-files pangzero:all 1.3-2
2016-02-27 07:59:01 status config-files pangzero:all 1.3-2
2016-02-27 07:59:01 status config-files pangzero:all 1.3-2
2016-02-27 07:59:01 status config-files pangzero:all 1.3-2
2016-02-27 07:59:01 status not-installed pangzero:all <none>
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 remove python-apport:all 2.14.1-0ubuntu3.3 <none>
2016-02-27 07:59:01 purge python-apport:all 2.14.1-0ubuntu3.3 <none>
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 status config-files python-apport:all 2.14.1-0ubuntu3.3
2016-02-27 07:59:01 status not-installed python-apport:all <none>
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 remove python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9 <none>
2016-02-27 07:59:02 purge python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9 <none>
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 status config-files python-aptdaemon.pkcompat:all 0.43+bzr805-0ubuntu9
2016-02-27 07:59:02 status not-installed python-aptdaemon.pkcompat:all <none>
2016-02-27 07:59:02 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:02 remove python-support:all 1.0.14ubuntu2 <none>
2016-02-27 07:59:02 purge python-support:all 1.0.14ubuntu2 <none>
2016-02-27 07:59:02 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:02 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:02 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:02 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:03 status config-files python-support:all 1.0.14ubuntu2
2016-02-27 07:59:03 status not-installed python-support:all <none>
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 remove python-ubuntuone-client:all 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:59:03 purge python-ubuntuone-client:all 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 status config-files python-ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:03 status not-installed python-ubuntuone-client:all <none>
2016-02-27 07:59:03 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:03 remove python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1 <none>
2016-02-27 07:59:03 purge python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1 <none>
2016-02-27 07:59:03 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:03 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:04 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:04 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:04 status config-files python-ubuntuone-storageprotocol:all 3.0.2-0ubuntu1
2016-02-27 07:59:04 status not-installed python-ubuntuone-storageprotocol:all <none>
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 remove ubuntuone-client:all 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:59:04 purge ubuntuone-client:all 3.0.2-0ubuntu2.2 <none>
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 status config-files ubuntuone-client:all 3.0.2-0ubuntu2.2
2016-02-27 07:59:04 status not-installed ubuntuone-client:all <none>
2016-02-27 07:59:04 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:04 remove unity-common:all 5.20.0-0ubuntu3 <none>
2016-02-27 07:59:04 purge unity-common:all 5.20.0-0ubuntu3 <none>
2016-02-27 07:59:04 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:05 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:05 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:05 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:05 status config-files unity-common:all 5.20.0-0ubuntu3
2016-02-27 07:59:05 status not-installed unity-common:all <none>
2016-02-27 07:59:05 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:05 remove vorbis-tools:i386 1.4.0-1ubuntu2 <none>
2016-02-27 07:59:05 purge vorbis-tools:i386 1.4.0-1ubuntu2 <none>
2016-02-27 07:59:05 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:05 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:05 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:06 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:06 status config-files vorbis-tools:i386 1.4.0-1ubuntu2
2016-02-27 07:59:06 status not-installed vorbis-tools:i386 <none>
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 remove x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1 <none>
2016-02-27 07:59:06 purge x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1 <none>
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 status config-files x11-xserver-utils-lts-raring:i386 7.7~3ubuntu2~precise1
2016-02-27 07:59:06 status not-installed x11-xserver-utils-lts-raring:i386 <none>
2016-02-27 07:59:06 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 remove xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3 <none>
2016-02-27 07:59:07 purge xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3 <none>
2016-02-27 07:59:07 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-common-lts-raring:all 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status not-installed xserver-common-lts-raring:all <none>
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 remove xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3 <none>
2016-02-27 07:59:07 purge xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3 <none>
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status config-files xserver-xorg-core-lts-raring:i386 2:1.13.3-0ubuntu6~precise3
2016-02-27 07:59:07 status not-installed xserver-xorg-core-lts-raring:i386 <none>
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 remove xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1 <none>
2016-02-27 07:59:08 purge xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1 <none>
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-lts-raring:i386 1:7.7+1ubuntu4~precise1
2016-02-27 07:59:08 status not-installed xserver-xorg-lts-raring:i386 <none>
2016-02-27 07:59:08 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:08 remove xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1 <none>
2016-02-27 07:59:08 purge xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1 <none>
2016-02-27 07:59:08 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:08 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-intel-lts-raring:i386 2:2.21.6-0ubuntu4.3~precise1
2016-02-27 07:59:09 status not-installed xserver-xorg-video-intel-lts-raring:i386 <none>
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 remove xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1 <none>
2016-02-27 07:59:09 purge xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1 <none>
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-openchrome-lts-raring:i386 1:0.3.1-0ubuntu1~precise1
2016-02-27 07:59:09 status not-installed xserver-xorg-video-openchrome-lts-raring:i386 <none>
2016-02-27 07:59:09 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:09 remove xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1 <none>
2016-02-27 07:59:09 purge xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1 <none>
2016-02-27 07:59:09 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:09 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-raring:i386 1:12.0.2+git.e5ac80d8-0ubuntu1~precise1
2016-02-27 07:59:10 status not-installed xserver-xorg-video-vmware-lts-raring:i386 <none>
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 remove xserver-xorg-video-vmware-lts-trusty:i386 3:6 <none>
2016-02-27 07:59:10 purge xserver-xorg-video-vmware-lts-trusty:i386 3:6 <none>
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 status config-files xserver-xorg-video-vmware-lts-trusty:i386 3:6
2016-02-27 07:59:10 status not-installed xserver-xorg-video-vmware-lts-trusty:i386 <none>
2016-02-27 13:09:49 startup archives unpack
2016-02-27 13:09:58 install linux-image-3.13.0-67-generic:i386 <none> 3.13.0-67.110
2016-02-27 13:09:58 status half-installed linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:06 status unpacked linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:06 status unpacked linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:06 install linux-headers-3.13.0-67:all <none> 3.13.0-67.110
2016-02-27 13:10:06 status half-installed linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:10:19 status unpacked linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:10:19 status unpacked linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:10:19 install linux-image-extra-3.13.0-67-generic:i386 <none> 3.13.0-67.110
2016-02-27 13:10:19 status half-installed linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:42 status unpacked linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:42 status unpacked linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:43 startup packages configure
2016-02-27 13:10:43 configure linux-image-3.13.0-67-generic:i386 3.13.0-67.110 <none>
2016-02-27 13:10:43 status unpacked linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:10:43 status half-configured linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:11:44 status installed linux-image-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:11:45 configure linux-headers-3.13.0-67:all 3.13.0-67.110 <none>
2016-02-27 13:11:45 status unpacked linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:11:45 status half-configured linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:11:45 status installed linux-headers-3.13.0-67:all 3.13.0-67.110
2016-02-27 13:11:45 configure linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110 <none>
2016-02-27 13:11:45 status unpacked linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:11:45 status half-configured linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 13:12:42 status installed linux-image-extra-3.13.0-67-generic:i386 3.13.0-67.110
2016-02-27 14:49:56 status triggers-pending initramfs-tools:all 0.103ubuntu4.2
2016-02-27 14:49:56 startup packages configure
2016-02-27 14:49:56 trigproc initramfs-tools:all 0.103ubuntu4.2 <none>
2016-02-27 14:49:56 status half-configured initramfs-tools:all 0.103ubuntu4.2
2016-02-27 14:50:30 status installed initramfs-tools:all 0.103ubuntu4.2

```

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Hey !

now that :
> 
x-0.log. In that file there is only a short line of text which says ```
X: cannot stat /etc/X11/X (No such file or directory), aborting.

May very well be meaningful !

What returns:
[code]
ls -al /etc/X11/X

```
should be a symbolic link to Xorg to start the X layer .

Look'n at your posted log files,,, be back soonest.

[INDENT][INDENT]strange things can happen
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> 
What returns:
```

ls -al /etc/X11/X

```
should be a symbolic link to Xorg to start the X layer .


```
ls -al /etc/X11/X
``` Returns:
```
ls: cannot access /etc/X11/X: No such file or directory
```

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Hey !

Now we are cooking with Crisco !

Next in line ... does the targeted system file exist ?
```

ls -al /usr/bin/Xorg

```

I do expect it to be:
> 
sysop@1404mini:~$ ls -al /media/sysop/ubie14.04std/etc/X11/ >> lrwxrwxrwx   1 root root    13 May 25  2014 X -> /usr/bin/Xorg

sysop@1404mini:~$ ls -al /media/sysop/ubie14.04std/usr/bin/Xorg
-rwxr-xr-x 1 root root 2335872 Feb 12  2015 /media/sysop/ubie14.04std/usr/bin/Xorg
sysop@1404mini:~$ 

where I am look'n at a 14.04 standard install on my system.

And in reference to the log files ... a whole bunch of 32 bit stuff removed ... what processor are you running ?
show me:
```

uname -a

```
as I hold my 32 bit thoughts in check.

[INDENT][INDENT]progress made, sometimes
[INDENT][INDENT][INDENT]in leaps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> MibunoOokami; Hey !

Now we are cooking with Crisco !



Mmm Crisco (drool)

> **Bashing-om said:**
> 
Next in line ... does the targeted system file exist ?
```

ls -al /usr/bin/Xorg

```

I do expect it to be:```
sysop@1404mini:~$ ls -al /media/sysop/ubie14.04std/etc/X11/ >>  lrwxrwxrwx   1 root root    13 May 25  2014 X -> /usr/bin/Xorg

sysop@1404mini:~$ ls -al /media/sysop/ubie14.04std/usr/bin/Xorg
-rwxr-xr-x 1 root root 2335872 Feb 12  2015 /media/sysop/ubie14.04std/usr/bin/Xorg
sysop@1404mini:~$
```

where I am look'n at a 14.04 standard install on my system.


Hi Bashing-om,

The targeted system [file]("http://paste.ubuntu.com/15220844") does exist... at least in part

> **Bashing-om said:**
> 
And in reference to the log files ... a whole bunch of 32 bit stuff removed ... what processor are you running ?
show me:
```

uname -a

```
as I hold my 32 bit thoughts in check.
[INDENT][INDENT]progress made, sometimes[INDENT][INDENT][INDENT]in leaps
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Well I must say, I'm pleased my efforts to try and help you have been successful rather than making things worse. 
Here's the [output]("http://paste.ubuntu.com/15220953") for ```
uname -a
``` I don't know if that identifies my processor which is Intel Atom. Computer in question is an HP Mini 110, 32bit, 2GB RAM and 320GB HDD.

---

### Post by Bashing-om on 2016-02-27
MibunoOokami ; Hummm ...

32 bit operating system for sure .. we put all those 32bit file removals back in our back pocket and as needed return to issues.

Our immediate problem of no " /etc/X11/X " file present .. and thus no linkage to a GUI .... 
Let's do this :
```

sudo touch /etc/X11/X
sudo chmod 777 /etc/X11/X

sudo ln -s /usr/bin/Xorg /etc/X11/X

```

check our work;
```

ls -al /etc/X11/X

```

insure it matches:
```

sysop@1404mini:~$ ls -al /etc/X11/X
lrwxrwxrwx 1 root root 13 May 19  2013 /etc/X11/X -> /usr/bin/Xorg
sysop@1404mini:~$

```

If all looks good and matches ... let's see what we have .....Reboot !
```

sudo reboot now

```

Tell me now that you get to the GUI ... AND that the file " /var/log/Xorg.0.log " is now created .

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> 
```

sudo ln -s /usr/bin/Xorg /etc/X11/X

```

Umm that code came back with ```
ln: failed to create a symbolic link '/etc/X11/X': File exists
``` So I proceeded to check our work

> **Bashing-om said:**
> check our work;
```

ls -al /etc/X11/X

```

insure it matches:
```

sysop@1404mini:~$ ls -al /etc/X11/X
lrwxrwxrwx 1 root root 13 May 19  2013 /etc/X11/X -> /usr/bin/Xorg
sysop@1404mini:~$

```


It doesn't look like it matches to me ```

-rwxrwxrwx 1 root root 0 Feb 28 10:50 /etc/X11/X
```

> **Bashing-om said:**
> 
If all looks good and matches ... let's see what we have .....Reboot !
```

sudo reboot now

```

Tell me now that you get to the GUI ... AND that the file " /var/log/Xorg.0.log " is now created .[INDENT][INDENT]good things can happen
[/INDENT]
[/INDENT]


  I'll wait for your response to that before I go ahead and reboot. Better safe than sorry. Edit: without rebooting I checked to see of that file was created but it wasn't.

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Ouch !

Excuse me, while I have a failure to understand . I guess that an empty file as a place holder is not going to work. I have my homework cut out for me to figure out how to populate that file properly.
That advisory " ln: failed to create a symbolic link '/etc/X11/X': File exists " makes me have to get in a learning mode.

No doubt about it, we got to have it.

[INDENT][INDENT][INDENT]figure out the how
[/INDENT][/INDENT][/INDENT]

-------------------------------
Edit: by the way .. sorry for the delay in responding ... I did something thoughtless and stupid ... overheated my box and crashed . Took a bit to cool down and check my file system before firing back up.

---

### Post by MibunoOokami on 2016-02-27
Is there anything I can do to help other than just enter commands and report what happened? Perhaps I could google something but I'm not sure what we were trying to do. 

Judging by you're comments, I get the impression you want to persevere and find out what has gone so terribly wrong and of course how to fix it. However, I'm mindful of the amount of time you're spending on this and wonder if perhaps I should just do a fresh install? ..... Unlike other times I've encountered problems, there is no rush (for me) to get this computer up and running again, I can get by with a few days of not having it working.... It would be good to have an answer for anyone else that may encounter this same problem in the future, so...

I'm just thinking out loud there ^^^

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Eremmmm ...

When all else fails " read the instructions":
From the manual (man ln).
> 
By  default,
       each  destination  (name  of  new link) should not already exist.

So excuse me ... once more - with feeling.
```

sudo rm /etc/X11/X
sudo ln -s /usr/bin/Xorg /etc/X11/X

```

Now check the permissions on the new(LY) created file :
```

ls -al /etc/X11/X

```
where we want to see :
> 
lrwxrwxrwx 1 root root

Which I can accept is the default value .

[INDENT][INDENT]I bet I do not forget again
[INDENT][INDENT][INDENT]repetition
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by MibunoOokami on 2016-02-27
> **Bashing-om said:**
> MibunoOokami; Eremmmm ...

When all else fails " read the instructions":
From the manual (man ln).

So excuse me ... once more - with feeling.
```

sudo rm /etc/X11/X
sudo ln -s /usr/bin/Xorg /etc/X11/X

```

Now check the permissions on the new(LY) created file :
```

ls -al /etc/X11/X

```
where we want to see :

Which I can accept is the default value .
[INDENT][INDENT]I bet I do not forget again[INDENT][INDENT][INDENT]repetition
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for your perseverance Bashing-om, at last we have some [success]("http://paste.ubuntu.com/15223235"). I have just rebooted and am at the login screen. I've logged in and for the moment, everything seems to be working.

I did start to search for what the "cannot create symbolic link" and found this [link]("http://askubuntu.com/questions/379647/failed-to-create-symbolic-link-usr-bin-utserver-file-exists/379649#379649") which I was about to ask what you thought. That's moot now because it suggests the exact same thing you just had me do, but I wanted to mention it to show I wasn't trying to let you do all the work.

Again, thank you for your help. I will now mark this thread as solved.

---

### Post by Bashing-om on 2016-02-27
MibunoOokami; Great ...

You do good work - as we wipe the sweat off .

Who would have thought it .. a lose of that little bitty symlink . Ha !

Glad we got it figured out .. and all is now well .

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

