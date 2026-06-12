---
title: "What is using up my hard drive space?"
date: 2021-08-12
forum: General Help
---

### Post by Autodave on 2021-08-12
Fairly fresh install of 20.04 on an HP Stream.  Disk usage analyzer says "30.1 GB total, 16.8 GB free."  But, there really isn't anything installed except solitaire and Xiphos.  Normally, and install like this would use up less than 3 GB of space.  I noticed a 1.3 GB swap.  However in /usr/lib I am showing 4 GB in use there.  I really coul;d use the extra HD space that I *should* have.......how do I find out where it is all being used up and why?  Was this a corrupted install possibly?

---

### Post by ajgreeny on 2021-08-12
Show us the output of ```
df -hT
``` which is much easier to understand than your description.

---

### Post by grahammechanical on 2021-08-12
> But, there really isn't anything installed except solitaire and Xiphos

There is also Xubuntu installed. Xubuntu developers recommend having at least 20GB hard disk space free when installing Xubuntu. Although we can get away with a minimum of 8GB.

[https://xubuntu.org/requirements/](https://xubuntu.org/requirements/)

When you update/upgrade Xubuntu do you use the software updater utility or use the command line? If we use the command line to update we also need to run a command to remove obsolete packages such as Linux kernels that have been replaced.

```
sudo apt autoremove
```

Regards

---

### Post by Autodave on 2021-08-12
```
$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  895M     0  895M   0% /dev
tmpfs          tmpfs     185M  1.5M  184M   1% /run
/dev/mmcblk0p2 ext4       29G   13G   15G  47% /
tmpfs          tmpfs     924M     0  924M   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     924M     0  924M   0% /sys/fs/cgroup
/dev/mmcblk0p1 vfat      511M  5.3M  506M   2% /boot/efi
tmpfs          tmpfs     185M   12K  185M   1% /run/user/1000
```

---

### Post by Autodave on 2021-08-12
After running autoremove:
```
$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  895M     0  895M   0% /dev
tmpfs          tmpfs     185M  1.5M  184M   1% /run
/dev/mmcblk0p2 ext4       29G   12G   15G  44% /
tmpfs          tmpfs     924M     0  924M   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     924M     0  924M   0% /sys/fs/cgroup
/dev/mmcblk0p1 vfat      511M  5.3M  506M   2% /boot/efi
tmpfs          tmpfs     185M   12K  185M   1% /run/user/1000
```

---

### Post by Yellow Pasque on 2021-08-12
> Normally, and install like this would use up less than 3 GB of space.

For a full Xubuntu install? I don't think so. About 10GB is more of a reasonable expectation.

---

### Post by Autodave on 2021-08-12
OK...might have to readjust a bit.  I just checked another laptop that I recently did a clean install on and I am using almost 8 GB of space.  No swap.  So, using my 1.3 GB swap from the laptop in question, I should be using 9.3 GB but instead I am using 13.3 GB.  That 4 GB that is being consumed somewhere would be useful to have back: even 1/2 of it would be nice.

---

### Post by TheFu on 2021-08-12
If you want a small Linux install, use TinyCore.  64MB should do it. It runs from RAM, so nothing will be faster on any box with 256MB of RAM or more.

[http://tinycorelinux.net/downloads.html](http://tinycorelinux.net/downloads.html) - 21MB for a wired network and GUI computer.  I remember when that was possible in about 4MB. We have definitely bloated our systems.

If you want more pre-installed junk and wifi, 163MB for TinyCorePlus. Good for online banking.

---

### Post by Autodave on 2021-08-12
TheFu:  I have used Xubuntu almost from the start, but I may have to look into something else finally.  I love this Stream because of its size and verified that I can run it for over 8 hours on battery!  

Thanks to all of you!

---

### Post by tea for one on 2021-08-12
Also, if you want to start with a minimal Xubuntu

[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

I use this on my HP Stream 11.6" 32GB 

A few apps added and quite snappy for a 2016 model.

---

### Post by TheFu on 2021-08-12
> **Autodave said:**
> TheFu:  I have used Xubuntu almost from the start, but I may have to look into something else finally.  I love this Stream because of its size and verified that I can run it for over 8 hours on battery!  

Thanks to all of you!

I had an Asus Eee for a few years. It was my first very small laptop.  It got me addicted to smaller, capable, systems. The search is always on when it is time for a new laptop.

---

### Post by Autodave on 2021-08-12
> **TheFu said:**
> I had an Asus Eee for a few years. It was my first very small laptop.  It got me addicted to smaller, capable, systems. The search is always on when it is time for a new laptop.

I had an EEEPC also: 9" screen.  I absolutely loved that machine.  Was quite sad when it died.  Most every machine that i have or have had have been throw-aways.  I have rescued them with Linux and a few parts.  I give them away to folks that can't afford to buy one new.  5 or 10 year old equipment with Xubuntu gives them email and internet capability.  It is amazing what some throw away just because Windows has become so slow that it is unusable.

---

### Post by TheFu on 2021-08-12
Every machine that I've given away ended up being trashed by that person within a few months, so I stopped and make them pay a token amount now.  
People paying $25-$50 for a machine will treat it very different than if it is given. Have a few C2D that I've retired (MB+CPU+RAM+Cooler) that need new homes. Replace them with much faster, newer, lower-power-using, systems.  One of those replacement systems has actually saved more than the extra electricity cost were with the older system over 2 yrs.  These aren't laptops.

---

### Post by Autodave on 2021-08-12
The people that I give them to really have nothing and are quite appreciative to get them and end up taking care of them.  A few of them have had them so long that I have actually replaced them with a "newer" machine than what they were using.  The last one that I replaced had originally been running Windows Vista as per the sticker still on the case!  512K memory!  I didn't even salvage anything from it: just pulled the HD and stuck it in a newer machine and gave it back.  They were SO happy with their new 1.6 dual core and 2 G RAM!

---

### Post by Yellow Pasque on 2021-08-12
There are a lot of things you can rip out from a Xubuntu install to save space - strange fonts, Libreoffice (use abiword instead), cups/sane and all the printer drivers if not printing/scanning.

---

