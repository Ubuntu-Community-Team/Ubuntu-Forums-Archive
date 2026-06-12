---
title: "cleaning up my &quot;home&quot; folder (is that my root partition?)"
date: 2015-11-30
forum: General Help
---

### Post by pjstock on 2015-11-30
I seem to have maxed out my base HDD. 
I know I am likely confusing physical storage with logical storage, but I am a little vague on partitions etc.

here's the deal.

I think I set up my Ubuntu with a 20Gb partition but I seem to have gobbled most of it up and am now down to about 850Mb free.

I try to push everything I can datawise over to a secondary 2Tb HDD but stuff seems to creep back into the base "root" (is that correct?) partition.

Running the Disk Analyzer thingee it seems that 5Gb of my 20 are used by Picasa. Now, I have redirected Picasa's default storage location to the 2Tb drive and so I am not sure what this 5gb comprises.

can anyone guide me or advise either through a cleanup or a better setup that would avoid this in the future?

Many thanks (again, as always)

Peter

---

### Post by Bashing-om on 2015-11-30
pjstock; Hi !

Maybe you are not in as bad of shape as you think. 
I think better from terminal - even a picture can not tell all always.
Post back - Between code tags - the outputs of terminal commands:
```

df -h
df -i

```
to relate the disk space .

Then to see the disk usage:
```

cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system.)

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And we see what 
[INDENT][INDENT][INDENT]tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-11-30
Unless we put /home on a separate partition then everything in /home is going to be added to the root ( / ) partition because it is in the root partition.

> I have redirected Picasa's default storage location to the 2Tb drive and so I am not sure what this 5gb comprises.

Files that were already in the Picasa folder before the redirection? Have to you Cut & Pasted them to the 2 TB drive?

Regards

---

### Post by Bucky Ball on 2015-12-01
Your best bet is to redirect ALL personal data files to the 2tb data partition. To do this, you could copy the folders in your /home directory / (which IS your root partition, /home is inside it), delete them from /home and then create symlinks in the /home directory to the directories you have copied, e.g. /Documents, /Music, etc., on the 2tb /Data partition (or whatever you have named it). Very easy, convenient and we can help. 

(This method has advantages for backups and if you install another Ubuntu on another partition, you can create symlinks there to the same data so both/all installs are accessing the same data. No redundancy or confusion.)

---

### Post by pjstock on 2015-12-01
many thanks
let's see if I can make these code tags work.

Here's step 1

```

peter@Peter-Desk:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        20G   18G  972M  95% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           398M  1.3M  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   69M  1.9G   4% /run/shm
none            100M   56K  100M   1% /run/user
/dev/sdd1       466G  193G  274G  42% /media/peter/New Volume
/dev/sdc1       1.9T  1.1T  808G  57% /media/peter/Seagate Expansion Drive
/dev/sdb1       196G   32G  164G  17% /media/peter/Internal 250GB
/dev/sda2        51G   41G   10G  81% /media/peter/5ABA2917BA28F0E5
/dev/sdb5        33G   27G  4.9G  85% /media/peter/40840a5b-68f1-48bd-86e6-12b36db49041
peter@Peter-Desk:~$ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda5        1299984 511034    788950   40% /
none              215924      2    215922    1% /sys/fs/cgroup
udev              211045    565    210480    1% /dev
tmpfs             215924    589    215335    1% /run
none              215924      3    215921    1% /run/lock
none              215924    115    215809    1% /run/shm
none              215924     35    215889    1% /run/user
/dev/sdd1      286556492  43540 286512952    1% /media/peter/New Volume
/dev/sdc1      212407577 654893 211752684    1% /media/peter/Seagate Expansion Drive
/dev/sdb1      171749032   2815 171746217    1% /media/peter/Internal 250GB
/dev/sda2       10704180 166672  10537508    2% /media/peter/5ABA2917BA28F0E5
/dev/sdb5        2203648 590298   1613350   27% /media/peter/40840a5b-68f1-48bd-86e6-12b36db49041
peter@Peter-Desk:~$ 

```

step two (sudo du -sx * | sort -n) seems to still be running.

I'm game for your help.
How do I start? what do I do?

Step 1. all the Non-hidden folders under my /home are already empty. I manually copied their contents off yesterday. 
even in the hidden folders, there are only 2 that have any significant amount of stuff in them (none have more than... 200mb and most less than 50mb or just a few kb)
.cache = 3.5gb
.google = 5.1gb

can I copy/clear those and redirect somehow? that would help enormously.

Step 2.

```
peter@Peter-Desk:~$ cd /
peter@Peter-Desk:/$ sudo du -sx * | sort -n
[sudo] password for peter: 
du: cannot access ‘proc/13823/task/13823/fd/4’: No such file or directory
du: cannot access ‘proc/13823/task/13823/fdinfo/4’: No such file or directory
du: cannot access ‘proc/13823/fd/4’: No such file or directory
du: cannot access ‘proc/13823/fdinfo/4’: No such file or directory
0	initrd.img
0	initrd.img.old
0	proc
0	sys
0	vmlinuz
0	vmlinuz.old
4	cdrom
4	dev
4	mnt
4	srv
8	media
16	lost+found
36	root
1292	run
4512	tmp
9472	bin
12000	sbin
12896	etc
293624	boot
407164	opt
1607180	lib
1814732	var
4371108	usr
9703632	home
peter@Peter-Desk:/$ 
```

Hmmm, drilling down the culprits in the .google folder seem to be in Picasa, under a folder titled "db3", a couple of files titled:
previews_0.db  (2.1Gb)
previews_1.db (1.2Gb)
bigthumbs.db (857Mb)
thumbs_0.db
thumbs_1.db

but it also seems that I was writing to them this morning.... so they are not just legacy files.

---

### Post by Bashing-om on 2015-12-01
pjstock; Hey ...

I see it as there are a lot of old kernels that can be removed to gain you a bit of breathing room ( /dev/sda5        20G   18G  972M  95% /).
As well, appears you have a lot of 3rd party software installed (  407164	opt is large ) . What applications do you have installed that are no longer of any value ?
And yeah, agreed, your /home is rather large, might do a lot of pruning there .
Let's take a look at installed kernels:
```

dpkg -l | grep linux-

```
With the intent to remove the old ones to gain that space back.

[INDENT]6 pounds of sugar
[INDENT][INDENT][INDENT]in a 5 pound sack
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pjstock on 2015-12-01
It's Greek to me alas.

```
peter@Peter-Desk:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.16                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                              3.16.0.53.44                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-30                               3.16.0-30.40~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic                       3.16.0-30.40~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-41                               3.16.0-41.57~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-generic                       3.16.0-41.57~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-43                               3.16.0-43.58~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-43-generic                       3.16.0-43.58~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-45                               3.16.0-45.60~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-45-generic                       3.16.0-45.60~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-48                               3.16.0-48.64~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-48-generic                       3.16.0-48.64~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-49                               3.16.0-49.65~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-49-generic                       3.16.0-49.65~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-50                               3.16.0-50.67~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-50-generic                       3.16.0-50.67~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-51                               3.16.0-51.69~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-51-generic                       3.16.0-51.69~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-52                               3.16.0-52.71~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-52-generic                       3.16.0-52.71~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-53                               3.16.0-53.72~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic                       3.16.0-53.72~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-utopic                      3.16.0.53.44                                        i386         Generic Linux kernel headers
ii  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-41-generic                         3.16.0-41.57~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-43-generic                         3.16.0-43.58~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-45-generic                         3.16.0-45.60~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-48-generic                         3.16.0-48.64~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-49-generic                         3.16.0-49.65~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-50-generic                         3.16.0-50.67~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-51-generic                         3.16.0-51.69~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-52-generic                         3.16.0-52.71~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-53-generic                         3.16.0-53.72~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-41-generic                   3.16.0-41.57~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-43-generic                   3.16.0-43.58~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-45-generic                   3.16.0-45.60~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-48-generic                   3.16.0-48.64~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-49-generic                   3.16.0-49.65~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-50-generic                   3.16.0-50.67~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-51-generic                   3.16.0-51.69~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-52-generic                   3.16.0-52.71~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic                   3.16.0-53.72~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.53.44                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-68.111                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
peter@Peter-Desk:~$ ^C
peter@Peter-Desk:~$ 

```

---

### Post by Bashing-om on 2015-12-01
pjstockl Uh Huh ...

LOTS of old kernels . Let's see if the package manager will work for us to remove them.
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt-get autoremove

```

Which, If the system is in shape, removes old kernels leaving the present booted kernel and one other as a backup.
In the event that a new kernel gets installed in the upgrade process ... reboot prior to autoremoving .

Else, well, we do it the manual way.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by pjstock on 2015-12-01
How do I get past this what looks like a confirmation screen?[ATTACH=CONFIG]265871[/ATTACH]

---

### Post by Bashing-om on 2015-12-01
pjstock; Try

use the space bar to page down, Tab to highlight "Ok", then Enter.
to manipulate the ttf-mscorefonts-installer's  EULA .

[INDENT][INDENT]this should help
[/INDENT][/INDENT]

---

### Post by pjstock on 2015-12-01
ahhah! thank you .
that should have been obvious.
now I'll continue on.
Peter

OK, done. I think.

How do I know if we gained space and cleaned up?

when I rerun that command (dpkg -l | grep linux-) I get this now.

```
peter@Peter-Desk:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.18                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                              3.16.0.55.46                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-41                               3.16.0-41.57~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-generic                       3.16.0-41.57~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-45                               3.16.0-45.60~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-45-generic                       3.16.0-45.60~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-48                               3.16.0-48.64~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-48-generic                       3.16.0-48.64~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-49                               3.16.0-49.65~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-49-generic                       3.16.0-49.65~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-50                               3.16.0-50.67~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-50-generic                       3.16.0-50.67~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-51                               3.16.0-51.69~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-51-generic                       3.16.0-51.69~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-52                               3.16.0-52.71~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-52-generic                       3.16.0-52.71~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-53                               3.16.0-53.72~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic                       3.16.0-53.72~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-55                               3.16.0-55.74~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-55-generic                       3.16.0-55.74~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-utopic                      3.16.0.55.46                                        i386         Generic Linux kernel headers
rc  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-41-generic                         3.16.0-41.57~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-3.16.0-43-generic                         3.16.0-43.58~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-45-generic                         3.16.0-45.60~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-48-generic                         3.16.0-48.64~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-49-generic                         3.16.0-49.65~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-50-generic                         3.16.0-50.67~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-51-generic                         3.16.0-51.69~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-52-generic                         3.16.0-52.71~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-53-generic                         3.16.0-53.72~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-55-generic                         3.16.0-55.74~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-41-generic                   3.16.0-41.57~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
rc  linux-image-extra-3.16.0-43-generic                   3.16.0-43.58~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-45-generic                   3.16.0-45.60~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-48-generic                   3.16.0-48.64~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-49-generic                   3.16.0-49.65~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-50-generic                   3.16.0-50.67~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-51-generic                   3.16.0-51.69~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-52-generic                   3.16.0-52.71~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic                   3.16.0-53.72~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-55-generic                   3.16.0-55.74~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.55.46                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-70.113                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
peter@Peter-Desk:~$ 

```

---

### Post by ptn107 on 2015-12-01
Save this list to a text file, call it kernels.txt or something:
```
linux-headers-3.16.0-41
linux-headers-3.16.0-41-generic
linux-headers-3.16.0-45
linux-headers-3.16.0-45-generic
linux-headers-3.16.0-48
linux-headers-3.16.0-48-generic
linux-headers-3.16.0-49
linux-headers-3.16.0-49-generic
linux-headers-3.16.0-50
linux-headers-3.16.0-50-generic
linux-headers-3.16.0-51
linux-headers-3.16.0-51-generic
linux-headers-3.16.0-52
linux-headers-3.16.0-52-generic
linux-image-3.16.0-30-generic
linux-image-3.16.0-41-generic
linux-image-3.16.0-43-generic
linux-image-3.16.0-45-generic
linux-image-3.16.0-48-generic
linux-image-3.16.0-49-generic
linux-image-3.16.0-50-generic
linux-image-3.16.0-51-generic
linux-image-3.16.0-52-generic
linux-image-extra-3.16.0-30-generic
linux-image-extra-3.16.0-41-generic
linux-image-extra-3.16.0-43-generic
linux-image-extra-3.16.0-45-generic
linux-image-extra-3.16.0-48-generic
linux-image-extra-3.16.0-49-generic
linux-image-extra-3.16.0-50-generic
linux-image-extra-3.16.0-51-generic
linux-image-extra-3.16.0-52-generic
```

and from the same folder just do:
```
for i in $(cat kernels.txt); do sudo apt-get purge $i; done
```

I've left out your two most recent kernels from the list. You should keep them anyway.

---

### Post by Bashing-om on 2015-12-01
ptn107; Nope ;

Did not take as we have an abnormality :
> 
rc  linux-image-3.16.0-43-generic
rc  linux-image-3.16.0-43-generic 
rc  linux-image-extra-3.16.0-43-generic 

where the 'rc' is for (R)emoved but (C)onfig files remain.

we see what results from the for loop .

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by pjstock on 2015-12-01
Getting there.
I now have 7.4Gb free!! Whee!

How can I know if I've done the best that is reasonable?

```
peter@Peter-Desk:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.18                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                              3.16.0.55.46                                        i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-53                               3.16.0-53.72~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-53-generic                       3.16.0-53.72~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-55                               3.16.0-55.74~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-55-generic                       3.16.0-55.74~14.04.1                                i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-utopic                      3.16.0.55.46                                        i386         Generic Linux kernel headers
ii  linux-image-3.16.0-53-generic                         3.16.0-53.72~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-55-generic                         3.16.0-55.74~14.04.1                                i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-53-generic                   3.16.0-53.72~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-55-generic                   3.16.0-55.74~14.04.1                                i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.55.46                                        i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                   3.13.0-70.113                                       i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
peter@Peter-Desk:~$ 

```

---

### Post by Bashing-om on 2015-12-01
pjstock; Yepper !

Looks good.
to complete system cleanup:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean

```

The rest is up to you to determine what application are of no value and/or establish symlinks to the applications data stores .

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ptn107 on 2015-12-01
get rid of the config files that were orphaned
```
dpkg -l | grep -e ^rc | awk '{print $2}' | xargs apt-get -y purge
```

---

### Post by Bucky Ball on 2015-12-01
Looks like you've done a good job killing the unwanted kernels. I've been hanging back with the symlinks as it would get confusing throwing an explanation of that in the middle of this.

If you want to go there, perhaps post a new thread about it and post the link here. We should be able to set that up in no time and, as you have nothing in the /home directory at the moment, perfect time to do it. 

DO NOT delete or move any of the hidden files/folders. If you had a seperate /home partition, everything would go in there, including your hidden folders. As you're setup with /home directory, the system will be looking for the hidden folders in there and moving them will cause (possibly severe) breakage. 

The symlink method moves only your personal data, not system settings saved in the hidden files/folders. :)

---

