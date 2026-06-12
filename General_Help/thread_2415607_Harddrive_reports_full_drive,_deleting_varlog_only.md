---
title: "Harddrive reports full drive, deleting /var/log only current solution"
date: 2019-03-28
forum: General Help
---

### Post by afrodeity on 2019-03-28
I have Ubuntu 14.04 installed on a 341.1GB partition.

The drive has been reporting that it is full with 0 bytes remaining.

Have tried finding the problem to no avail.

Can only rectify by deleting /var/log folder, which is not ideal.

It doesn't appear to be a normal log issue inflation issue, but something else?

Any tips or ideas?

---

### Post by Bashing-om on 2019-03-28
afrodeity; Hi !

Let's start by looking at the disk usage,
Post beck the outputs of terminal commands:
```

df -h
df -i
cf / # so we look from the top
sudo du -sx * | sort -n
cd # to revert to the /home directory as the Present Working Directory
dpkg -l |grep linux- ## as a quicky to isolate to boot full condition from old kernels,

```

from these see where we go next,

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by afrodeity on 2019-03-29
ok, here goes

> $ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           803M  9.9M  793M   2% /run
/dev/sda5       318G  221G   81G  74% /
tmpfs           4.0G   62M  3.9G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           4.0G     0  4.0G   0% /sys/fs/cgroup
/dev/sda1       140G  124G   17G  89% /media/Magenta
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           803M  116K  803M   1% /run/user/1000
tmpfs           803M     0  803M   0% /run/user/65534

> df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             192267     662   191605    1% /dev
tmpfs            204120     976   203144    1% /run
/dev/sda5      21159936 1833244 19326692    9% /
tmpfs            204120     107   204013    1% /dev/shm
tmpfs            204120       5   204115    1% /run/lock
tmpfs            204120      18   204102    1% /sys/fs/cgroup
/dev/sda1      17584648  316905 17267743    2% /media/Magenta
cgmfs            204120      14   204106    1% /run/cgmanager/fs
tmpfs            204120      51   204069    1% /run/user/1000
tmpfs            204120       4   204116    1% /run/user/65534



> sudo du -sx * | sort -n
du: cannot access 'proc/9066/task/9066/fd/4': No such file or directory
du: cannot access 'proc/9066/task/9066/fdinfo/4': No such file or directory
du: cannot access 'proc/9066/fd/4': No such file or directory
du: cannot access 'proc/9066/fdinfo/4': No such file or directory


> 
dpkg -l |grep linux-
ii  linux-base                                                  4.5ubuntu1~16.04.1                                       all          Linux image base package
ii  linux-firmware                                              1.157.21                                                 all          Firmware for Linux kernel drivers
ii  linux-generic                                               4.4.0.143.151                                            i386         Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-143                                     4.4.0-143.169                                            all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-143-generic                             4.4.0-143.169                                            i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       4.4.0.143.151                                            i386         Generic Linux kernel headers
ii  linux-image                                                 3.11.0.19.20                                             i386         Generic Linux kernel image.
ii  linux-image-4.4.0-143-generic                               4.4.0-143.169                                            i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-generic                                         4.4.0.143.151                                            i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         4.4.0-143.169                                            i386         Linux Kernel Headers for development
ii  linux-modules-4.4.0-143-generic                             4.4.0-143.169                                            i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-modules-extra-4.4.0-143-generic                       4.4.0-143.169                                            i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu5                                     all          base package for ALSA and OSS sound systems
ii  linux-source                                                4.4.0.143.151                                            all          Linux kernel source with Ubuntu patches
ii  linux-source-4.4.0                                          4.4.0-143.169                                            all          Linux kernel source for version 4.4.0 with Ubuntu patches
ii  syslinux-common                                             3:6.03+dfsg-11ubuntu1                                    all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu8                                     i386         Bootloader for Linux/i386 using MS-DOS floppies
rc  syslinux-themes-debian                                      12-4                                                     all          collection of boot loaders (theme metapackage)
rc  syslinux-themes-debian-wheezy                               12-4                                                     all          collection of boot loaders (debian-wheezy theme)

---

### Post by afrodeity on 2019-03-29
After about three hours uptime

> df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           803M  9.9M  793M   2% /run
/dev/sda5       318G  305G     0 100% /
tmpfs           4.0G   41M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           4.0G     0  4.0G   0% /sys/fs/cgroup
/dev/sda1       140G  124G   17G  89% /media/Magenta
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           803M  116K  803M   1% /run/user/1000

---

### Post by Bashing-om on 2019-03-29
afrodeity - Ouch

> **afrodeity said:**
> After about three hours uptime

try again :
```

cd /
sudo du -sx * | sort -n

```
and give it time to seek and complete :)

For comparison is my result:
```

sysop@x1804mini:/$ sudo du -sx * | sort -n
[sudo] password for sysop: 
du: cannot access 'proc/15471/task/15471/fd/4': No such file or directory
du: cannot access 'proc/15471/task/15471/fdinfo/4': No such file or directory
du: cannot access 'proc/15471/fd/3': No such file or directory
du: cannot access 'proc/15471/fdinfo/3': No such file or directory
0	dev
0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	lib64
4	opt
4	srv
8	media
8	mnt
8	snap
16	lost+found
64	tmp
80	root
1384	run
2344	core
5836	grub
7636	etc
11460	sbin
11708	bin
123940	boot
807132	lib
[color=green]955124	var[/color]
975364	home
2025364	usr
sysop@x1804mini:/$

```

where in your case I expect /var/ to be running amuck. In that case we need to look at the log file{s) and see what the system is screaming so about.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by afrodeity on 2019-03-30
took longer than expected :(
var is tres bloated ...

```

du: cannot access 'proc/936/task/936/fdinfo/16': No such file or directory
du: cannot access 'proc/936/fdinfo/18': No such file or directory
du: cannot access 'proc/23468/task/23468/fd/4': No such file or directory
du: cannot access 'proc/23468/task/23468/fdinfo/4': No such file or directory
du: cannot access 'proc/23468/fd/4': No such file or directory
du: cannot access 'proc/23468/fdinfo/4': No such file or directory
0	dev
0	initrd.img
0	proc
0	sys
0	vmlinuz
4	cdrom
4	mnt
4	srv
8	snap
52	media
56	tmp
144	~
10060	run
14148	sbin
14592	bin
50188	lost+found
96240	etc
113868	boot
292444	root
733304	lib
1005636	opt
21058176	usr
105459224	var
204139960	home

```

if I cd into /var and do du -h, I think we have the culprit:
```

100G	./log/cups

```

```


cd /var/log/cups

ls -al
total 84278444
drwxr-x--- 2 root lp            4096 Mar 30 07:46 .
drwxrwxr-x 6 root syslog        4096 Mar 30 07:46 ..
-rw-r----- 1 root adm              0 Mar 30 07:46 access_log
-rw-r----- 1 root adm    86300999825 Mar 30 14:01 error_log
-rw-r----- 1 root adm              0 Mar 30 07:46 page_log

```

```

tail error_log
W [30/Mar/2019:14:03:06 +0200] Notifier for subscription 333 (dbus://) went away, retrying!
E [30/Mar/2019:14:03:06 +0200] Directory \"/usr/lib/cups/notifier\" has insecure permissions (040755/uid=1000/gid=1000).

```

```

sudo chmod 755 /usr/lib/cups/notifier

```

---

### Post by Bashing-om on 2019-03-30
afrodeity; Well ...

At least the problem is identified, However, I do not see that you have a "good" solution.

For reference:
> 
sysop@x1804mini:~$ ls -al /usr/lib/cups/notifier
total 64
drwxr-xr-x  2 root root  4096 Mar 18 12:47 .
drwxr-xr-x 10 root root  4096 Apr  3  2018 ..
-rwxr-xr-x  1 root root 14328 Mar  3 05:28 dbus
-rwxr-xr-x  1 root root 18424 Mar  3 05:28 mailto
-rwxr-xr-x  1 root root 18424 Mar  3 05:28 rss

sysop@x1804mini:~$ ls -ld /usr/lib/cups/notifier
drwxr-xr-x 2 root root 4096 Mar 18 12:47 /usr/lib/cups/notifier
sysop@x1804mini:~$ 


where on my system root is the owner and group. It is not nice to change system files :(

[INDENT]a deeper dig in order ?
[/INDENT]

---

### Post by afrodeity on 2019-03-31
Yep, I didn't fix the problem with the right permissions and ownership, will take a look at your post, for now, here is another possible solution:

In cupsd.conf

disable logging
```

LogLevel none

```

UPDATE: okay, I see I had the wrong ownership for /usr/lib/cups/notifier and /usr/lib/cups 

:guitar:

---

### Post by Impavidus on 2019-03-31
Note that 14.04 only has a few weeks of support left. It's time to prepare for an upgrade.

---

