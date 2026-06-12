---
title: "Recovering and Solving Synaptic causing full disk error?"
date: 2005-06-14
forum: General Help
---

### Post by dpod on 2005-06-14
Hi,
The problem I had yesterday ([http://ubuntuforums.org/showthread.php?t=41563](http://ubuntuforums.org/showthread.php?t=41563)) has reoccurred, and seems to be related  a bug ([https://bugzilla.ubuntu.com/show_bug.cgi?id=2757)](https://bugzilla.ubuntu.com/show_bug.cgi?id=2757)). Since I'm currently basically locked out of Linux, I'd appreciate any help.

The issue is that installing packages can lead to what I think is probably the root getting filled to the point that one can't run anything or reboot in anything but terminal mode. I was promiscuously downloading fonts yesterday with synaptic when I got a disk full error, even though /home was showing 10.2 gig (yes I checked it was gigabytes). When I looked at "filesystem", however, I was getting 0 space free.

Yesterday, I got Gnome running again by logging in through terminal and deleting the contents of /tmp and /var/cache/apt/archives/ (which cause some minor problems). When I checked to see if Synaptic was running it asked me to run dkpg --config -a to finish an install. This then got me the same disk full error: programs couldn't start(not even a new terminal or man pages), and I gradually lost functionality on open programs such as Gaim, Evolution, and terminal. I am now more or less stuck out again, though I imagine I canstill get in with terminal.

My questions are: 
a) is there anyway of finding out (from terminal) what is getting filled and fixing that (deleting files or whatever) so I can properly reboot
b) is there anyway of getting stopping synaptic (if that's where the problem lies) doing what it is doing with these packages?
c) Is there any way of ensuring that Ubunutu doesn't allow synaptic to fill the file syste to the point that it can't load a desktop on reboot (or run programs in the current session).

The bug was listed as normal priority; since currently the only solution I can see is reinstallation, and since it seems to be unstoppable, I've raised it to critical. Since it seems to be happening to others, it may need a patch, even!

Any ideas would be greatly appreciated; I was in the middle of some important work (to me at least) and I've lost 1.5 days on this.

---

### Post by Xian on 2005-06-14
[QUOTE=dpod]a) is there anyway of finding out (from terminal) what is getting filled and fixing that (deleting files or whatever) so I can properly reboot[/QUOTE]
I can't help you with the bug as I've never encountered this, but as for identifying where the bloat is on your system, I'd recommend that you read in [THIS](http://www.ubuntuforums.org/showthread.php?t=41680) thread.

---

### Post by az on 2005-06-14
This would not happen if you put everyting on one partition.  That is the default.

By making seperate partitions, you open the possibility of filling up your root wheile lots of free space is left on your home.

Why did youmake seperate partitions?

I agree that there is no system which checks for space left on a filesystem and this is a problem.

---

### Post by Xian on 2005-06-14
[QUOTE=dpod] I was promiscuously downloading fonts yesterday with synaptic when I got a disk full error, even though /home was showing 10.2 gig (yes I checked it was gigabytes). [/QUOTE]
I suppose the question really being how much space was provided for the partition that you were actually downloading these packages to? If /home is on a separate partition then it doesn't matter if it has 100GB's free since it will not be used by the main filesystem for space allocation.

---

### Post by dpod on 2005-06-14
I followed the diagnositc advice recomended by Xian ([http://www.ubuntuforums.org/showthread.php?t=41680)](http://www.ubuntuforums.org/showthread.php?t=41680)). There isn't really an stand out huge file, which got me wondering about the partitions.

I had a friend set them u with me and just took his advice. On a 40 GB (dual boot) drive we did the following:

hda1 primary 3.2 GB
hda2 primary 18.3 GB
hda5 logical 501.7 MB swap
hda6 logical 4.0 GB
hda7 logical 14.0 GB

I don't know how to check which drives are being usefor which, except I suspect that hda2 contains my home (hda5 is obviously swap) and probably hda7 or hda1 is the boot. When I was going through m files with du -sh I found 3.2 GB in /var/usr, of which 1.2 was in lib (mostly thousands of small files) and 1.6 in share (again, mostly smallish files with no > 1GB standouts.

This makes me wonder indeed if my partitions are too small.

My questions then are:
a) should I/can I collapse the home and boot partitions?
b) failing that should I/can I increase the space available to the non-/home directory (either hda1 or hda4)
c) How c I figure out which is which?
d) Should I be doing/considering something else

---

### Post by Xian on 2005-06-14
First we need to figure out what is where and how much there is of it. :)

You can either look in your /etc/fstab to see where your mount points are, or you can just open a terminal and enter the command below:

```
$ mount
```

Next let's see how much data is on each mounted partition.
Same procedure and enter this command:

```
$ df -h
```

---

### Post by dpod on 2005-06-14
[QUOTE=Xian]First we need to figure out what is where and how much there is of it. :)

You can either look in your /etc/fstab to see where your mount points are, or you can just open a terminal and enter the command below:

```
$ mount
```
[/QUOTE]

Done.
```

hda6 type ext3 (rw,errors=remount-ro)
 proc on /proc type proc (rw)
 sysfs on /sys type sysfs (rw)
 devpts on /dev/shm type devpts (rw,gid=5,mode620)
 tmpfs on /dev/shm (rw)
dev/hda7 on /home type ext3 (rw,bind)
 /dev on /.dev type unknown (rw,bind)
 none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

```
[QUOTE=Xian]

Next let's see how much data is on each mounted partition.
Same procedure and enter this command:

```
$ df -h
```[/QUOTE]

Done
[code]
                 size       used   avail  use    mounted on
/dev/hda6 3.7 GB   3.5        0    100%     /
tmpfs        244MB   0         244   0          /dev/shm
/dev/hda7 13G       2.0      11     16%     /home
/dev          3.7G     3.5G      0     100%   /.dev
none        5.0 M      2.8M  2.3M  56%    /dev

---

### Post by Xian on 2005-06-14
[QUOTE=dpod]```

                 size       used   avail  use    mounted on
/dev/hda6 3.7 GB   3.5        0    100%     /
tmpfs        244MB   0         244   0          /dev/shm
/dev/hda7 13G       2.0      11     16%     /home
/dev          3.7G     3.5G      0     100%   /.dev
none        5.0 M      2.8M  2.3M  56%    /dev
```[/QUOTE]
Okay, it looks like root is partitioned on hda6 and /home on hda7.
And you can see that you've used 100% of your space on hda6.

I know that 3.7 GB sounds like alot, and Ubuntu can live happily on that much space as a minimal installation, but when you start doing alot of downloading it ceases to be a minimal install and then you need more room. For example, listed below is my HD info and you will see that I have used just about the same amount of space on the root directory as you. But the usage percent is only at 39 points since I've allocated almost 10GB's to that directory.

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda9             9.7G  3.6G  5.7G  39% /
tmpfs                 221M     0  221M   0% /dev/shm
/dev/hda3              10G  8.0K   10G   1% /FAT
/dev/hda7              20G  6.2G   14G  31% /gentoo
/dev/hda8              28G   16G   13G  56% /storage
/dev/hda2              12G  2.1G  9.2G  19% /suse
/dev/hda6             5.0G  509M  4.2G  11% /susehome
/dev/hda1              26G  8.2G   17G  33% /ntfs
/dev                  9.7G  3.6G  5.7G  39% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
```

---

### Post by dpod on 2005-06-14
Thanks very much for the guidance so far Xian.

What would you recommend doing? 
Can I/should I point home and root in the same partition (i.e. combine hda6 and hda7)?

Can I/Should I change the partition sizes? Do I do this using the install CD-ROM?

---

### Post by Xian on 2005-06-14
There's several options and I'm not good at all of them. :)

Generally, the most space on your root partition is used by the /usr directory. You can check this out by issuing the command below. Look to see what directories are using the most space. If /usr is a good candidate then you might just want to split that off onto another partition and make note of it in your /etc/fstab file. That way you are increasing the room for other paths in your root partition without having to resize anything.

You can see on my system the /usr path eats 2GB in my / directory.
It is by far and away the largest file system there.

You might also consider splitting off your /var since that is where the APT cache lives.

```
$ sudo du -sh /*
3.1M    /bin
6.8M    /boot
0       /cdrom
2.8M    /dev
40M     /etc
1.3G    /home
4.0K    /initrd
0       /initrd.img
70M     /lib
48K     /lost+found
12K     /media
4.0K    /mnt
4.0K    /opt
452M    /proc
7.9M    /root
9.2M    /sbin
4.0K    /srv
0       /sys
164K    /tmp
2.0G    /usr
151M    /var
0       /vmlinuz
```

---

### Post by dpod on 2005-06-14
my /var and /usr are the two biggest and around 2~3 G each

How would I either split them off or make the root partition bigger? With the partitioner in the installation disk?

I appreciate this help! I think I might a near a solution meaning I can get back to work.

---

### Post by Xian on 2005-06-14
[QUOTE=dpod]How would I either split them off or make the root partition bigger? With the partitioner in the installation disk?[/QUOTE]
The install disk is what I use to partition though others like qtparted. But in any case, yeah you would just need to use/create some free space on your HD, format it for Linux, reboot and mount those new partitions from either Ubuntu or a LiveCD, move the data in your /usr & /var directories over to the created paths, make the proper notations in your /etc/fstab file and then either remount your file system from the command line or just reboot.

Oh, and as with any partitioning action....backup anything you can't afford to lose.

---

### Post by dpod on 2005-06-14
Cheers and thanks. If nobody hears back from me, I guess everything blew up.
-d \\:D/

---

### Post by angkor on 2005-06-15
[QUOTE=azz]By making seperate partitions, you open the possibility of filling up your root wheile lots of free space is left on your home.
[/QUOTE]

By making seperate partitions you also make re-installing an OS a breeze cause you get to keep your /home (lots of settings are saved) or other data kept on seperate partitions.

 Just make sure you give / enough space to work on. I made myself a 10g root partition and it's currently 137MB big. But that's probably cause I have  /var and /usr on seperate partitions as well :)

---

### Post by dpod on 2005-06-15
To be honest, I just gave up: when I tried to resize the partion, I couldn't, I ended up with an extra partition. I decided to hell with it and reinstalled the whole thing getting rid of windows in the process. And then of course 16 hours of setting up wireless (that HAS to get better: I'd say an ad is a waste of time until a newbie and plug and play wireless, streatming media, and smb). But after three complete reboots everything is working wonderfully except evolution... which did last time (unlike everything else) but now doesn't.

So if somebody is following this up later: I don't know the final answer.

---

