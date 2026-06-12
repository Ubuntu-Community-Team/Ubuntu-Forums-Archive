---
title: "boot is all the sudden 100% used up, how, why and what to do about it?"
date: 2013-08-29
forum: General Help
---

### Post by 777funk on 2013-08-29
Not sure what's happening here...

thanks in advance for any help. By the way this is a dual boot Win XP machine.

---

### Post by oldos2er on 2013-08-29
Do you have a separate boot partition? Please post output from these commands: ```
sudo fdisk -l
``` ```
df -h
```

---

### Post by 777funk on 2013-08-29
Yes I do and here is that output:

> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000773c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          978942   611327999   305174529    5  Extended
/dev/sda5          978944    36106239    17563648   83  Linux
/dev/sda6        36108288   601563135   282727424   83  Linux
/dev/sda7       601565184   611327999     4881408   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06dd06dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976751999   488375968+   7  HPFS/NTFS/exFAT

and:

> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        17G   14G  2.5G  85% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           593M  1.1M  592M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  576K  1.5G   1% /run/shm
/dev/sdb1       466G  333G  134G  72% /mnt/Windows
/dev/sda1       461M  422M   16M  97% /boot
/dev/sda6       266G   18G  235G   7% /home


---

### Post by oldos2er on 2013-08-29
See [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) for info on removing old unneeded kernels.

---

### Post by 777funk on 2013-08-29
Thank you for that!

So I take it old kernels are what's eating up my boot partition? I suppose I could've set my updates to never update and this wouldn't have happened?

Seems like half the time I let it update something ends up going wrong anyhow!

---

### Post by Dennis N on 2013-08-29
A suggestion: keep two or three kernels and related headers installed, and when a kernel upgrade occurs, remove the oldest installed kernel and headers by some method of your choosing, as installed kernels and headers are not automatically removed.

**For anyone who prefers a graphical tool, here is a guide using the Synaptic Package Manager on managing this:**

[http://liam-on-linux.livejournal.com/20347.html](http://liam-on-linux.livejournal.com/20347.html)

---------------------------------------------------------
General Information:

At a minimum there are 3 packages per kernel upgrade. The one starting with linux-image is the kernel. If it is a pae kernel, you would see that added on to the name.

linux-headers
linux-headers-generic
linux-image-generic

Sometimes there are one or two more packages you can remove. The computer I am using now also includes a fourth package named "linux-image-extra-generic".

---

### Post by oldos2er on 2013-08-29
> **777funk said:**
> Thank you for that!

So I take it old kernels are what's eating up my boot partition? I suppose I could've set my updates to never update and this wouldn't have happened?

You want security updates though.

Another possible solution would be to enlarge your boot partition.

---

### Post by 777funk on 2013-08-30
I did this and ended up with problems:

> nick@NickUbuntu:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get purge
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-3.2.0-52-generic-pae : Depends: linux-headers-3.2.0-52 but it is not going to be installed
 ubuntu-tweak : Depends: gir1.2-unique-3.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


---

### Post by 777funk on 2013-08-30
Ok I used Synaptic and it worked. Still not sure why I was having trouble with the xargs apt-get purge. But alls well that ends well.

I wish there were a way to automate this. That'd sure make life a little easier vs having to manually take out the trash every so often.

---

