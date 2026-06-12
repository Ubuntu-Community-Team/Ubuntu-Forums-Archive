---
title: "/ Running Out of Space"
date: 2019-09-12
forum: General Help
---

### Post by Quarkrad on 2019-09-12
I am getting an error message re the filesystem root having only 959.1MB of disk space (space2).  I have **/** on a ssd in a small partition (see space1) that is physically on sda1.  Disk Analyzer (space3) shows me that it is /media/dad/.. that is taking up all my space.  What I cannot get my head around is that /media/dad.... backup, store2,store1, windata, workspace, virtualbox1 are on physically different HDs.  backup=sdi1, store2=sdc1, store1=sdd1, windata=sdd3.  When I look at my other hds via gparted each partition (e.g. sdi1, sdc1, sdd1, etc) has plenty of space.  There is something fundamental I do not get - I can see sda5, my / partition is full, but it seems to be full due to /media/dad/... that are on different hard disks.  Any help to sort me out much appreciated!

---

### Post by oldfred on 2019-09-12
My / is  30GB on SSD and I use about 8GB, but regularly houseclean. It includes /home, but only the normally hidden files as all my data is in a data partition on HDD.

Post these:
sudo df -h
       cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null
And if one folder looks large like /var run this, example is /var, but use your large folder.
sudo du -hx --max-depth=1 /var 2> /dev/null
And continue drilling down until you find what is large.

---

### Post by Quarkrad on 2019-09-13
For some reason the Code tag doesn't seem to be working - /usr = 7.4G, /var = 6.6G and /home = 12G

I'll start looking in /usr and /var with your other commands

---

### Post by SeijiSensei on 2019-09-13
A common problem is /var/log, especially if you have some hardware issue that keeps throwing errors.  Try
```

cd /var
sudo du -s *

```
which will list the size of each directory under /var like this:
```

6052    backups
600448  cache
28468   crash
395964  lib
4       local
0       lock
29020   log
4       mail
4       metrics
4       opt
0       run
4       snap
64      spool
52      tmp

```

---

### Post by Quarkrad on 2019-09-13
```
dad@dadubuntu:/$ sudo du -hx --max-depth=1 /var 2> /dev/null
[sudo] password for dad: 
4.0K	/var/local
4.0K	/var/metrics
4.0K	/var/mail
464M	/var/cache
4.0K	/var/opt
140K	/var/spool
7.6M	/var/backups
180K	/var/snap
44K	/var/tmp
19M	/var/crash
2.0G	/var/log
4.1G	/var/lib
6.6G	/var
dad@dadubuntu:/$ sudo du -hx --max-depth=1 /usr 2> /dev/null
275M	/usr/src
343M	/usr/local
3.0G	/usr/share
372M	/usr/bin
8.0K	/usr/games
44M	/usr/include
20M	/usr/sbin
3.4G	/usr/lib
7.4G	/usr
dad@dadubuntu:/$ 

```

---

### Post by Quarkrad on 2019-09-13
This was my original terminal output

```
dad@dadubuntu:~$ sudo df -h
[sudo] password for dad: 
Filesystem      Size  Used Avail Use% Mounted on
udev            3.4G     0  3.4G   0% /dev
tmpfs           693M  1.6M  692M   1% /run
/dev/sda5        20G   17G  1.3G  93% /
tmpfs           3.4G   31M  3.4G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.4G     0  3.4G   0% /sys/fs/cgroup
/dev/loop0      219M  219M     0 100% /snap/wine-platform-runtime/23
/dev/loop1       89M   89M     0 100% /snap/core/7396
/dev/loop3      457M  457M     0 100% /snap/wine-platform/125
/dev/loop2       87M   87M     0 100% /snap/ubuntu-mate-welcome/319
/dev/loop4      4.8M  4.8M     0 100% /snap/foobar2000/253
/dev/loop6      218M  218M     0 100% /snap/wine-platform-runtime/30
/dev/loop5      128K  128K     0 100% /snap/software-boutique/39
/dev/loop8      4.8M  4.8M     0 100% /snap/foobar2000/256
/dev/loop7       87M   87M     0 100% /snap/ubuntu-mate-welcome/335
/dev/loop9      8.0M  8.0M     0 100% /snap/pulsemixer/250
/dev/loop10      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop12      87M   87M     0 100% /snap/ubuntu-mate-welcome/324
/dev/loop11      43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop13     8.0M  8.0M     0 100% /snap/pulsemixer/23
/dev/loop14      74M   74M     0 100% /snap/wine-platform-3-stable/6
/dev/loop15     457M  457M     0 100% /snap/wine-platform/122
/dev/loop16      55M   55M     0 100% /snap/core18/1144
/dev/loop17     457M  457M     0 100% /snap/wine-platform/128
/dev/loop18     144M  144M     0 100% /snap/gnome-calendar/28
/dev/loop19      72M   72M     0 100% /snap/software-boutique/31
/dev/loop20      90M   90M     0 100% /snap/core/7713
/dev/loop21      55M   55M     0 100% /snap/core18/1098
/dev/sda1       499M  422M   78M  85% /media/Recovery
/dev/sda4        49G   35G   15G  71% /media/dad/windows10
/dev/sda6        42G   12G   29G  29% /home
/dev/sda2        96M   44M   53M  45% /boot/efi
/dev/sdc1       917G  462G  409G  54% /media/dad/store2
/dev/sdb2       271G  135M  271G   1% /media/dad/virtualbox1
/dev/sdb1       193G   20G  164G  11% /media/dad/workspace
/dev/sdi1       1.8T 1008G  733G  58% /media/dad/backup
/dev/sdd1       788G  392G  356G  53% /media/dad/store1
/dev/sdd3       131G   48G   83G  37% /media/dad/win10data
tmpfs           693M   24K  693M   1% /run/user/1000
dad@dadubuntu:~$ cd /
dad@dadubuntu:/$ sudo du -hc --max-depth=1 / 2> /dev/null
7.4G	/usr
84K	/mnt
13M	/bin
6.6G	/var
4.0K	/lib64
0	/dev
34M	/etc
44K	/boot-sav
2.0T	/media
923M	/opt
4.0K	/srv
12G	/snap
128K	/tmp
56K	/BootInfo
16K	/lost+found
189M	/boot
4.0K	/cdrom
14M	/sbin
12G	/home
838M	/lib
120M	/root
0	/sys
0	/proc
1.6M	/run
2.0T	/
2.0T	total
dad@dadubuntu:/$ 

```

---

### Post by SeijiSensei on 2019-09-13
/var/log is 2 GB in size.  That's really large. 

/var/lib at 4 GB is also unusually large, at least in comparison to my system where it is about 400 MB.

/var/cache/apt/archives can be another problem.  It stores copies of all updated deb packages on your system.  Usually you don't need those.  That's not really the source of your problem though.

---

### Post by guiverc on 2019-09-13
It looks like you've used a lot of space with installed snaps  (ie. your space is apps you've installed; 11.8gb).

fyi:  mounted drives increase the size of your / directory; eg. you should note your disk usage diagram shows you have 2.1TB (not just 20gb).

---

### Post by Quarkrad on 2019-09-13
/var is 5.4Gb (Disk Analyser) of which /var/lib/snapd is 3.2Gb and /var/log is 2.1Gb.  I understand I can delete everything in .../log but I'm not sure about .../snapd.  I have just read a link where somebody also had a large ..../snapd folder and used the following commands.

[B]sudo apt autoremove --purge snapd gnome-software-plugin-snap

rm -fr ~/snap[/B]

Do you think these commands are safe?

---

### Post by #&amp;thj^% on 2019-09-13
> **Quarkrad said:**
> 

rm -fr ~/snap[/B]

Do you think these commands are safe?

[B][U]rm -fr ~/snap
[/U][/B]
This will completely remove snap, and all installed snap packages and their data.

---

### Post by Holger_Gehrke on 2019-09-13
'snap' has the habit of keeping old versions of every package you've installed so you can go back to an older version if the new one doesn't work for you. You've got two version of core, core18, foobar2000, gtk-common-themes, pulsemixer and software-boutique and three each of ubuntu-mate-welcome and wine-platform. you can get a **complete** list of installed snaps showing all revision with 'snap list --all' in a terminal. To get rid of an old revision of a snap you use 'snap remove --revision' with the revision number as shown by 'snap list --all' and the name of the snap. Removing the older versions should free up half to two thirds of the space used by /var/lib/snapd/snaps without removing any program you might still want to use.

I'd advise against just erasing the log-files in /var/log. I'd first check the contents to see what has your system complaining so much that the files get that big. You might have some serious trouble brewing and removing the files might hide the problems ... After checking the logs you should remove the compressed logs (*.gz) and force one or two rotations of the log to get the current logs compressed ('sudo logrotate --force'). Then of course there's the journal. That's the binary version of the logs. You can clean that out with 'journalctl --vacuum-time=' followed by a maximum age for messages you want kept (for example 'journalctl --vacuum-time=2 weeks').

Holger

---

### Post by TheFu on 2019-09-13
If you've played with Docker or any virtual machines, it is easy to create a 10G file in /var/ without knowing it.

[B]find /var   -type f     -size +2G      -print
[/B]
Will find files over 2G in size, for example.  I found an old TV recording from 2012 that was 16G earlier today!

Also, I like to sort the output from du, so the largest directories are grouped as expected.

```
$ sudo du -sh /var/* |sort -h
0       /var/lock
0       /var/run
4.0K    /var/local
4.0K    /var/mail
4.0K    /var/opt
140K    /var/tmp
5.2M    /var/spool
5.9M    /var/crash
15M     /var/backups
168M    /var/log
347M    /var/cache
3.7G    /var/lib
```
The -h option on both handle the "human readable" size outputs as expected.  So, there's some big files in /var/lib/ ... 

```
$ sudo find /var/lib -type f -size +500M -ls
  5767170 1739396 -rw-rw-r--   1 libvirt-qemu kvm      **1781137408** Apr 19 13:16 /var/lib/libvirt/images/ubuntu-mate-16.04.6-desktop-amd64.iso

```
Ah - an ISO file for Ubuntu-Mate - 1.7G in size.  This is on a VM server and that ISO is my recovery OS if anything bad happens to any virtual machine.  I'll be keeping it.  Plus, I mount extra storage there to hold VM files like that:
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt--lv ext4  197G  1.8G  **186G**   1% /var/lib/libvirt
```
Plenty of free storage for it here.

Anyways, figured that having some different tools/commands couldn't hurt. Nothing wrong with anything already posted by others.

---

### Post by Skaperen on 2019-09-13
looks like i need to finish my tool that looks around for what is taking up the most space.  i originally started it in C and moved it to Python.  i have since coded a correct recursive-like file tree walker in Python (simpler than the one in C).  the idea is to keep a list of the 100 largest files and directories as it scans through everything (or the specified tree) and output that list in largest last order when done.  i'm still trying to decide the best way to count hard-linked files in the sum of space used in various directories.  some file system types dynamically allocate space for i-nodes so i need to figure that in, somehow, to get correct directory totals.  file systems like **[COLOR=#0000cd][FONT=courier new]reiserfs[/FONT][/COLOR]** add another complication: tail packing.

---

### Post by Quarkrad on 2019-09-16
Thank you - snaps was a significant contributor and having read some articles on 'snap' I'm going to steer away for a while.  I can see the benefits but have never read about some of the downsides. I have reduced / by nearly 7G so / now sits at 12 rather than 19G.  Appreciate all your help.  (Reduced /var/log and got rid of snaps).

---

### Post by TheFu on 2019-09-16
> **Quarkrad said:**
> Thank you - snaps was a significant contributor and having read some articles on 'snap' I'm going to steer away for a while.  I can see the benefits but have never read about some of the downsides. I have reduced / by nearly 7G so / now sits at 12 rather than 19G.  Appreciate all your help.  (Reduced /var/log and got rid of snaps).

19G would have been fine for /.  12G is a little tight unless you make certain that /var and /home are on different storage, be that partitions or LVs.

Some tools use / for temporary files, so you might find that some tools can't deal with large files anymore.

---

### Post by dragonfly41 on 2019-09-16
There is a regex search (name or content) tool SearchMonkey which can be quite useful.
You can use the Basic | Advanced | Options tabs to setup a search profile e.g. in /var
In Advanced tab > Files: click on (regex) Expression Builder.

---

### Post by braznyc on 2019-10-19
WOO HOO!
I did it: sudo apt autoremove --purge snapd


That thing was eating a lot of memory.

I'm going back to the PPAs.

---

