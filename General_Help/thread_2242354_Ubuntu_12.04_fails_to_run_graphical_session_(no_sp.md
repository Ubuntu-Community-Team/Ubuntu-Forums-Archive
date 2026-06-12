---
title: "Ubuntu 12.04 fails to run graphical session (no space on /)"
date: 2014-09-01
forum: General Help
---

### Post by thekiwi5000 on 2014-09-01
Hello,
Recently i experienced X server fails on my Ubuntu 12.04.  When i booted up i got a window sayig that system is running in low-res  mode, the option to run it like that once, failed. - coulnd't log in on  graphics session - the only consoles left were ttys.

  I tried to purge some old kernels with apt-get - but the operation failed! (no space on device)
  So i tried to manually make some free space in /boot via LiveCD Debian Mint system (i ran out of space on / ) and found this answer:

  [http://askubuntu.com/a/401259/321653](http://askubuntu.com/a/401259/321653)
  *All paths are paths on Ubuntu HDD instalation, but all cmd outputs are from Debian Mint running from LiveCD.*
  the problem is that after removing theese old kernels, both *df* and *nautilus* are still showing 0 bytes free:
  ```
mint mint # df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.5G   21M  1.5G   2% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
udev                  1.5G  284K  1.5G   1% /dev
tmpfs                 1.5G  156K  1.5G   1% /dev/shm
/dev/sr0              875M  875M     0 100% /live/image
tmpfs                 1.5G   21M  1.5G   2% /live/cow
tmpfs                 1.5G     0  1.5G   0% /live
tmpfs                 1.5G   28K  1.5G   1% /tmp
/dev/sda7              24G   24G     0 100% /media/79cfe116-4ebf-461c-9d96-e992a7916a8f //<--- my / partition, after old kernel deletion
/dev/loop0            865M  865M     0 100% /media/disk
/dev/sda5             159G   61G   90G  41% /media/home

```  /dev/sda7 is my / partition (was doing this on live Debian Mint)
  The command was invoked from 'sudo su'

This is a duplicate of my question on askubuntu:
[http://askubuntu.com/questions/517518/freeing-space-on](http://askubuntu.com/questions/517518/freeing-space-on)

---

### Post by ian-weisser on 2014-09-01
Looks like your partition is full.
You should poke around in there and delete something big.

Old kernels fill up a 250MB /boot partition, but barely make a drop in a 24GB partition.
I would look for movies and other large data.

There are several utilities out there that will tell you the largest files.
Good old 'du' will do it too.

---

### Post by thekiwi5000 on 2014-09-01
> **ian-weisser said:**
> Looks like your partition is full.
You should poke around in there and delete something big.

Old kernels fill up a 250MB /boot partition, but barely make a drop in a 24GB partition.
I would look for movies and other large data.

There are several utilities out there that will tell you the largest files.
Good old 'du' will do it too.
Ok, so i deleted some unneede files from Desktop, when i 'freed' ~500MB, nautilus still was saying 0 bytes free. Even after re-mount

---

### Post by TheFu on 2014-09-01
UNIX file systems reserve about 2%-5% of the storage for use by root. It is a tunable parameter when the file system is built. This is meant as a safety check for the system - normal users can't fill that last 2% and du will show as 100% full until that safety margin is freed.

I'd look for a "core" file under /var .... when things crash like the kernel or X, a core file is often the result. It is owned by root, so it would bypass the protection.

I'd use this:
```
find /media -type f -size +500M
```
to find the hogs, then reduce the size slightly to find more and more after I've cleaned up the largest files.

---

### Post by thekiwi5000 on 2014-09-01
> **TheFu said:**
> UNIX file systems reserve about 2%-5% of the storage for use by root. It is a tunable parameter when the file system is built. This is meant as a safety check for the system - normal users can't fill that last 2% and du will show as 100% full until that safety margin is freed.

I'd look for a "core" file under /var .... when things crash like the kernel or X, a core file is often the result. It is owned by root, so it would bypass the protection.
OK, so what would i do with the "core" file?

---

### Post by TheFu on 2014-09-01
If you are a C developer, analyze it to determine what happened and create a bug report.

Otherwise - delete it.

---

### Post by thekiwi5000 on 2014-09-01
> **TheFu said:**
> If you are a C developer, analyze it to determine what happened and create a bug report.

Otherwise - delete it.
Where do i find exactly the 'core' file?
here's my /var
```
mint var # ls
backups  crash  jupiter  local  log   opt  spool  www
cache    games  lib      lock   mail  run  tmp


```

---

### Post by TheFu on 2014-09-01
Use the **find** command.

---

### Post by steeldriver on 2014-09-01
You deleted files from Desktop - but is your Desktop even inside the / partition? your df results show a separate /media/home

To seek out big files on /media/79cfe116-4ebf-461c-9d96-e992a7916a8f, you could do something like

```

find /media/79cfe116-4ebf-461c-9d96-e992a7916a8f -size +100M -exec du -h {} \; | sort -hr | head -10

```

---

### Post by thekiwi5000 on 2014-09-01
> **TheFu said:**
> Use the **find** command.

what parrameter should i give? 
```
find |grep core
```
doesn't find anything related

*sorry, it's first time i experienced something like that - i need a good description/guide or hints*

---

### Post by TheFu on 2014-09-01
In the "teach a man to fish" spirit: [http://www.linuxcommand.org/reading_man_pages.php](http://www.linuxcommand.org/reading_man_pages.php)
Reading manpages takes time, but all the information you need is in there - plus there are multiple examples in this thread already.  You might try using the path and iname parameters to find whatever you seek.

"find" is one of those commands that is worth understanding - the are many thousands of examples and how-tos on the internet as well.  Be careful with them and don't just copy/paste without understanding exactly what it does.  Sometimes "find" will find more than you expect, so if it is being paired with an "rm" command, it is possible to wipe an OS accidentally.  I know - I've done this myself back in 1996.

BTW - it is much harder for me to "help and explain" than it is just to post the find command answer. Please appreciate that.

---

### Post by thekiwi5000 on 2014-09-01
> You deleted files from Desktop - but is your Desktop even inside the / partition? your df results show a separate /media/home

To seek out big files on /media/79cfe116-4ebf-461c-9d96-e992a7916a8f, you could do something like

     ```


     find /media/79cfe116-4ebf-461c-9d96-e992a7916a8f -size +100M -exec du -h {} \; | sort -hr | head -10

```


OK, this command found the files, but all of those files are in */home*. What should i do?

I know those commands, but i don't know what is the 'core' file should be found and deleted. What's this file? What's it's name?
> If you are a C developer, analyze it to determine what happened and create a bug report.

Otherwise - delete it.

---

### Post by TheFu on 2014-09-01
"core" - is the filename.  I know it is difficult and complex - until someone states it clearly.  There could be more than one and they might get a suffix or prefix, but the latest one would be named "core" (without the quotes). There may not be any "core" files - I'm just guessing based on history (I've seen this) and probable ways that a file system can become full with root authority.

core files are like crash files on Windows. They get created when something bad happens and the system isn't configured to prevent them.  There is a setting for that.  I don't know what the default is and don't know where to set it.  Google would tell me quickly.

Freeing up space in $HOME won't help solve this issue, right?  $HOME isn't where the OS files sits.  Only freeing up space where the OS needs some will help. Please do not just delete any files that are part of an installed package - that will make things much harder later.  If a package installed the file, then the package must be used to remove it to keep things consistent inside the package manager database.

So - I'm afraid my lack of skill explaining things isn't helping for your current skill level. I hope someone else is better at explaining than me - it is my failure and I apologize.

---

### Post by thekiwi5000 on 2014-09-01
> **TheFu said:**
> "core" - is the filename.  I know it is difficult and complex - until someone states it clearly.  There could be more than one and they might get a suffix or prefix, but the latest one would be named "core" (without the quotes). There may not be any "core" files - I'm just guessing based on history (I've seen this) and probable ways that a file system can become full with root authority.

core files are like crash files on Windows. They get created when something bad happens and the system isn't configured to prevent them.  There is a setting for that.  I don't know what the default is and don't know where to set it.  Google would tell me quickly.

Freeing up space in $HOME won't help solve this issue, right?  $HOME isn't where the OS files sits.  Only freeing up space where the OS needs some will help. Please do not just delete any files that are part of an installed package - that will make things much harder later.  If a package installed the file, then the package must be used to remove it to keep things consistent inside the package manager database.

So - I'm afraid my lack of skill explaining things isn't helping for your current skill level. I hope someone else is better at explaining than me - it is my failure and I apologize.

The problem is that i can't remove/purge **anything** with apt-get, because it gives me 'No space left on device' error ](*,). In this case the only way to free the space on / partition is manually deleting the files. And as i stated in the first post, manually deleting kernels did not free any byte.

---

### Post by Habitual on 2014-09-01
```
df -i 
```output please.

---

### Post by thekiwi5000 on 2014-09-01
> **Habitual said:**
> ```
df -i 
```output please.

executed from sudo su
```
mint / # df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
aufs                  218661     872  217789    1% /
tmpfs                 218661       5  218656    1% /lib/init/rw
udev                  216812     796  216016    1% /dev
tmpfs                 218661       3  218658    1% /dev/shm
/dev/sr0                   0       0       0    -  /live/image
tmpfs                 218661     872  217789    1% /live/cow
tmpfs                 218661       3  218658    1% /live
tmpfs                 218661      48  218613    1% /tmp
/dev/sda7            1597440  530298 1067142   34% /media/stary
```

/dev/sda7 is my /partition.
Please note that im on Live Debian Mint

---

### Post by TheFu on 2014-09-01
I've probably assumed some important details.

Everything is performed when running with the liveCD booted. This liveCD must be the identical release as being fixed. 32-bit for 32-bit; 64-bit for 64-bit and the same release level to the 3rd decimal - "14.04.1" for example.

After boot, use the recovery mode to get a shell and mount the / partition - do NOT mount /home.

apt-get uses temporary files.  dpkg will not.  Based on prior posts here you don't have a separate /boot partition - it is part of / which is about 24G.  The OS should be only 8-10G of that total space so the other .... 15G or so is not related to the OS.  

Any web files, DBs, non-core OS stuff can be moved elsewhere.  Does that make sense? "Elsewhere" means to a different partition.  There must be non-core-OS files in this partition somewhere that can be cleaned up. Using the 'find' command, with the sample options provided above, it should be possible to find the largest files, which are the easiest to clean up.  Only you know your system, the programs on it, what is likely to be sucking all that storage.   If there aren't any really big files - change the size parameter and make it smaller until you find files.

I suppose if you install every GUI program ever invented (or do a bunch of Java development) outside your HOME, then / could become full on a 24G partition.  I don't know.   That just isn't my experience here.  Here's my main desktop 
```
$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        14G   11G  1.8G  86% /
```

So - you've cleaned up lots of non-program stuff, but want to clean up package too.

Using chroot to make the partition on the HDD the current root (/) partition for the running OS. The command will be something like chroot /media/79cfe116-4ebf-461c-9d96-e992a7916a8f - this must be run as root and only impacts that single shell - new terminals won't be trapped inside.

So now you can look for extra Linux kernels that can be removed to free up storage.
```
dpkg -l|grep linux-image
``` will provide a list.  I keep my kernels cleaned up - learned about this issue in 2010-ish and have been diligent since. On a system here:
```
$ dpkg -l|grep linux-image
ii  linux-image-3.13.0-34-generic         3.13.0-34.60                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic         3.13.0-35.62                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic   3.13.0-27.50                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic   3.13.0-29.53                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic   3.13.0-30.55                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic   3.13.0-32.57                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic   3.13.0-34.60                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic   3.13.0-35.62                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.13.0.35.42                         amd64        Generic Linux kernel image
ii  linux-image-generic-lts-raring        3.13.0.35.42                         amd64        Generic Linux kernel image
```
This system was a 12.04 upgrade to 14.04.

Next, use the **dpkg -r {insert-exact-package-name-here}** command to remove the exact, older, kernel, that you don't want/need anymore.  If initrd doesn't get rebuilt, look up how to force it. Something in the output should have the **initramfs-tools**.

Check the storage - **df -h** to see that / isn't 100% anymore. If it is - keep looking for unwanted packages and removing them, not necessarily kernels.

Using dpkg in this way is for emergency purposes.  **aptitude** should be used for daily maintenance needs - it will clean up old packages automatically that apt-get doesn't handle. aptitude is sometimes smarter about dependencies than apt-get. Most of the time, that doesn't matter, but sometimes it matters a bunch.

It is a holiday here - need to do the family things and get the burgers started on the grill.

---

### Post by steeldriver on 2014-09-01
If you only ran find on the filesystem mounted at /media/stary then regardless of whether the files show up in /, /var, /home or whatever, they are part of the problem - based on your previous post it looked like you might have a separate /home partition (and you might still have - just that it's been mounted over an older non-empty /home). However if you want to be absolutely sure you're not traversing into other filesystems, then you can add the -xdev option to your find command.

I'd not sure about the value of searching for core files specifically: afaik the default ulimit -c in Ubuntu is 0 meaning that core files don't actually get created unless you specifically enable them (by setting ulimit -c to a non-zero value). Big *log* files are a more common issue.

---

### Post by thekiwi5000 on 2014-09-01
> **TheFu said:**
> I've probably assumed some important details.

[...]
> **steeldriver said:**
> If you only ran find on the filesystem  mounted at /media/stary then regardless of whether the files show up in  /, /var, /home or whatever, they are part of the problem - based on your  previous post it looked like you might have a separate /home partition  (and you might still have - just that it's been mounted over an older  non-empty /home). However if you want to be absolutely sure you're not  traversing into other filesystems, then you can add the -xdev option to  your find command.

I'd not sure about the value of searching for core files specifically:  afaik the default ulimit -c in Ubuntu is 0 meaning that core files don't  actually get created unless you specifically enable them (by setting  ulimit -c to a non-zero value). Big *log* files are a more common issue.

OK, i freed ~2GiB by removing some old game packages with dpkg in installed OS's recovery mode. Now i have the following problem:

1. I boot up from hdd, when GRUB shows up, i choose recovery mode.
2. When the recovery mode menu shows up, i choose 'resume' option (contiue booting)
3. The 'Ubuntu' screen shows up (a big string saying 'ubuntu' on the center of the screen, with four dots under it)
4. The 12.04 login screen comes up
5. I log in:
  - whatever graphic option i choose ('ubuntu', 'ubuntu 2d', 'gnome', 'gnome classic' etc.) when i click enter, the login screen disappears, several messages print out in the console that show up for ~0.1 sec, the screen goes black, and it goes back to point #4.

I suppose that this is a graphics driver problem. My laptop is Sony VAIO VGN-FZ31M, the graphics inside are NVIDIA GeForce 8400M GT.

---

