---
title: "dpkg tells no free space but I have free space!"
date: 2013-09-30
forum: General Help
---

### Post by m-zainoune on 2013-09-30
Hi everyone,

I was doing some updates on Ubuntu 12.04, and obviously something went wrong.

Now, when I do *sudo apt-get update*, I get this at the end:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```


Here's what I get when I do *sudo dpkg --configure -a*:
```
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device
```

I tried *autoremove, clean, clean all, autoclean* - nothing seems to work.
I even tried this [technique]("http://ubuntuforums.org/showthread.php?t=859901&p=5388560#post5388560").

Here is my df -h (obviously / has enough space):

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        14G  9.6G  3.5G  74% /
udev            997M  4.0K  997M   1% /dev
tmpfs           403M  912K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M   80K 1007M   1% /run/shm
/dev/sda6       130G   42G   82G  34% /home
```

And here are the various errors the Update manager displays:

[[IMG]http://s24.postimg.org/b80x1vjtt/Screenshot_from_2013_09_30_09_34_28.jpg[/IMG]]("http://postimg.org/image/b80x1vjtt/")

[[IMG]http://s10.postimg.org/dzf869t51/Screenshot_from_2013_09_30_09_35_46.jpg[/IMG]]("http://postimg.org/image/dzf869t51/")

[[IMG]http://s18.postimg.org/g2vwb4fmd/Screenshot_from_2013_09_30_09_36_29.jpg[/IMG]]("http://postimg.org/image/g2vwb4fmd/")


Thanks for you help!

---

### Post by Bashing-om on 2013-09-30
m-zainoune; Hi !

Maybe your /boot directory is full, or perhaps all you inodes are used up:
The following command is useful for finding out which directories are using all your space...
```
 du -h --max-depth=1 | sort -hr

```
and to see the inode usage:
```

df -i

```

The package manager generally tells no lies and ->

[INDENT][INDENT]sometimes we have to look
[/INDENT][/INDENT]

---

### Post by m-zainoune on 2013-09-30
Thanks for the quick reply Bashing-om !

Too much inode usage indeed. Here's the *df -i* answer:

```
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       915712 915712       0  100% /
udev            213512    528  212984    1% /dev
tmpfs           218497    451  218046    1% /run
none            218497      3  218494    1% /run/lock
none            218497      4  218493    1% /run/shm
/dev/sda6      8609792 126645 8483147    2% /home
```

And the details of* du -h --max-depth=1 | sort -hr*:

```
16K    ./.gegl-0.0
16K    ./.aptitude
12K    ./.pdfedit
12K    ./.mission-control
12K    ./.dbus
8.0K    ./.qt
8.0K    ./.mplayer
8.0K    ./.hplip
8.0K    ./.fonts
8.0K    ./.cups
4.0K    ./.viking
4.0K    ./Videos
4.0K    ./Ubuntu One
4.0K    ./.themes
4.0K    ./Templates
4.0K    ./Public
4.0K    ./.psensor
4.0K    ./.icons
4.0K    ./.gphoto
4.0K    ./.gnome2_private
0    ./.gvfs
```

What should I do now?

Many thanks,

---

### Post by Bashing-om on 2013-09-30
m-zainoune; Well, not good !

The only thing that one can for an immediate/temporary solution is delete lots of those small files any where on the partition sda1. Once the inodes are used up, there are no more. That number is set in concrete when the partition was formatted.

I am concerned that I do not see the /boot directory in your output. Do you have a separate /boot outside of the "/" directory residing on sda1 ?
Was the "du" command ran from a point that the /boot directory is not seen ?

else:
```

ls -la /boot

```
There are three things one can do to quickly get the system back up.
Delete all the log files in "/var/log/" directory and the sub sub directories, less the current log files;
Delete the old log files at ~/.xsession-errors;
Delete/purge/remove all old kernels on the system and the related config files.

[INDENT][INDENT]that is the sad state of the affair
[/INDENT][/INDENT]

---

### Post by alainhenry on 2013-10-01
I have exactly the same problem. thanks for the careful diagnostic and the hints. I'll work on it tonight and will let you know how I fare.
Alain

---

### Post by Bashing-om on 2013-10-01
@ alainhenry; 

Pleased to be of some aid ! .. In the event of requiring further assistance, please ask. Removing old kernels, for those who have not done so before, can be a daunting experience.

[INDENT][INDENT]help is why we are here
[/INDENT][/INDENT]

---

### Post by m-zainoune on 2013-10-01
Thank you for your help Bashing-om.

Nothing seemed to work, so I just reinstalled.
What should I do for this not to happen again? Periodically do a *sudo apt-get autoclean/autoremove/clean all*?
Shoud I do this through Ubuntu tweaks?

Thanks again,

---

### Post by Bashing-om on 2013-10-01
m-zainoune; Hey !

Thats a bummer (re-installing) .. but in ubuntu it is a sure fire fix !

I am not a proponent of GUI applications that do less than what can be done and UNDERSTOOD from the command line.

All that is required for "housecleaning" is as you have said with the two other things to pay close attention to .. What is going on within the /boot directory. and your log files. Removing old kernels is a part of housecleaning, the system has no way to know if/and when a particular kernel might be of use .. and lays it on the administrator to remove unwanted kernels (images and headers and config files).
do on occasion:
```

ls -la /boot
##and in general
du -h --max-depth=1 | sort -hr ##from various points
##or maybe:
du -h /<dir> | sort -nr | less ##large directories

```


As log files, if not looked at regularly, can get HUGE if there is a problem.

Following this and your system in general use .. you should never then have a problem.

[INDENT][INDENT]piece of cake 
[/INDENT][/INDENT]

---

### Post by alainhenry on 2013-10-02
I erased a number of files and could have the system fully up and running again. Could then uninstall a number of unused packages. 
Following df -i I'm now back to 98% full on inodes, down from 100%.  
I'll follow my system more closely, using your tips above. Many thanks. 
Alain

---

### Post by m-zainoune on 2013-10-03
Thanks for the tips Bashing-om.

Have a great one,

---

