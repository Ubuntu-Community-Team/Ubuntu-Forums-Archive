---
title: "root filesystem is full - / 100%"
date: 2007-11-30
forum: General Help
---

### Post by lowracer on 2007-11-30
my root filesystem is showing 100% usage this morning.  

```
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb1              8.3G   7.9G      0 100% /

```

```
 sudo du --max-depth 1 -x
56      ./lost+found
1358188 ./var
4       ./home
13460   ./etc
1514752 ./media
5124    ./bin
73340   ./boot
0       ./dev
4       ./initrd
543664  ./lib
4       ./mnt
179480  ./opt
0       ./proc
4196    ./root
6768    ./sbin
4       ./srv
0       ./sys
24636   ./tmp
4185756 ./usr
4       ./backup
4       ./windows
7909448 .
```

I have a separate /home partition.  What can I do to fix this?  I've done apt-get clean and aptitude clean but still I'm at 100%.  I can't run the Synaptic Package Manager due to the filesystem being full.

I'm running Gutsy with all the latest upgrades.

Thanks,
-Mark

---

### Post by thelatinist on 2007-11-30
You could manually uninstall openoffice, which should free up enough space to allow you to run a package manager.

```

sudo aptitude remove openoffice.org-base openoffice.org-calc openoffice.org-math openoffice.org-draw openoffice.org-impress openoffice.org-writer openoffice.org-xsltfilter  openoffice.org-testtool openoffice.org-thesaurus-en-us openoffice.org-style-default openoffice.org-style-industrial openoffice.org-evolution openoffice.org-emailmerge openoffice.org-gnome openoffice.org-onlineupdate openoffice.org-pyuno openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-kde-integration openoffice.org-java-common openoffice.org-javafilter openoffice.org-gtk openoffice.org-gnome openoffice.org-gnome-integration openoffice.org-graphicfilter openoffice.org-common openoffice.org-core openoffice.org-core01 openoffice.org-core02 openoffice.org-core03 openoffice.org-core03u openoffice.org-core04 openoffice.org-core04u openoffice.org-core05 openoffice.org-core05u openoffice.org-core06 openoffice.org-core07 openoffice.org-core08 openoffice.org-core09 openoffice.org-core10 openoffice.org openoffice.org-help-en-us ubuntu-desktop language-support-en python-uno thunderbird-locale-en-gb
```

You probably wouldn't even need to remove all of those.  Customize to your liking.

The long-term solution, though, will be to enlarge your partition using the gparted livecd.

---

### Post by Irony on 2007-11-30
Try this;

[http://ubuntuforums.org/showthread.php?t=315654](http://ubuntuforums.org/showthread.php?t=315654)

---

### Post by viking777 on 2007-11-30
Run this command instead and see what you get:

```
sudo du -xh --max-depth=1
```

Edit: Actually I just tried it your way and on my system it gives the same results as my code (except for the -h switch which gives it in 'human readable' form) The reason I asked you to try my code was that you appear to have a large amount of data in /media which is unusual because the -x switch should stop it from reading remote drives. So what is in there exactly? I'm not just being nosey, it is just that I had an identical problem about a week ago and I found out that instead of having a mounted drive in /media I actually had a hard copy of another drive. This only showed up when I unmounted all the drives in /media and ran du again and the data still showed up even with the x switch. At the moment my /media drive shows 80k whereas yours shows something like 1.5Gb which made me think that you may have the same problem.

---

### Post by atlfalcons866 on 2007-11-30
you can reclaim 5% of your space if your using ext3 by doing

> sudo tune2fs -m 1 /dev/sdb1

---

### Post by geirha on 2007-11-30
You've got about 1.5GiB in /media, you've probably moved files over there thinking they would be stored to a different partition (but it probably wasn't mounted at the time, so they were put on the root partition instead)

---

### Post by lowracer on 2007-11-30
I'm looking in /media but I don't see 1.5GB there...  Maybe I'm missing something:

```
:/media$ ls -lash
total 36K
4.0K drwxr-xr-x  8 root root 4.0K 2007-11-30 09:05 .
4.0K drwxr-xr-x 23 root root 4.0K 2007-11-29 10:39 ..
4.0K drwxr-xr-x  3 root root 4.0K 2007-11-30 07:35 backup
   0 lrwxrwxrwx  1 root root    6 2007-11-29 10:39 cdrom -> cdrom0
4.0K drwxr-xr-x  2 root root 4.0K 2007-11-29 10:39 cdrom0
   0 lrwxrwxrwx  1 root root   45 2007-04-20 07:22 .directory -> /etc/kubuntu-default-settings/directory-media
4.0K -rw-r--r--  1 root root  244 2007-11-30 09:05 .hal-mtab
   0 -rw-------  1 root root    0 2007-11-30 09:03 .hal-mtab-lock
   0 lrwxrwxrwx  1 root root   42 2006-11-20 19:17 .hidden -> /etc/kubuntu-default-settings/hidden-media
4.0K drwx------  2 root root 4.0K 2007-07-12 06:53 ipod
4.0K drwxr-xr-x  2 root root 4.0K 2007-11-29 10:39 sda1
4.0K drwxr-xr-x  4 root root 4.0K 2006-12-20 10:15 sda2
4.0K drwxr-xr-x  6 mark mark 4.0K 2007-11-29 07:47 sdc1

```

OK I think I found it, you guys were right, it was an errant backup file weighing in at 1.5GB:

:/media$ sudo umount backup
umount: backup: not mounted
mark@mark-desktop:/media$ sudo du --max-depth=1 -xh
4.0K    ./cdrom0
1.5G    ./backup
4.0K    ./sda1
4.0K    ./sda2
4.0K    ./sdc1
4.0K    ./ipod
1.5G    .

doing a sudo rm -rf backup cleared out the errant 1.5GB file.  I'm down to a root partition at 81%.

Thanks for all the help...

---

### Post by geirha on 2007-11-30
Use the du command you used earlier, in /media. sdc1 seems to have some data inside it though, is anything mounted there (df -h)?

---

