---
title: "Upgrading to 14.04."
date: 2015-02-06
forum: General Help
---

### Post by Bobby_James on 2015-02-06
I am considering upgrading from 12.04 LTS to 14.04 LTS.

a) is there any reason not to upgrade?

b) I only have 12GB of free disk space. Is that enough?

Thanks!

---

### Post by chaale on 2015-02-06
Hi Bobby_James!

For (a), I think it depends on your actual system/applications. I would let others give you a better answer, but for now, you might want to look at this : [http://serverfault.com/questions/606089/would-it-be-advised-to-use-ubuntu-14-04-lts-over-12-04-lts](http://serverfault.com/questions/606089/would-it-be-advised-to-use-ubuntu-14-04-lts-over-12-04-lts)

As for (b), this amount of space is fair enough. But you will surely be limited in terms of programs/applications to install (eg. heavy programs) by available drive space. But you might already be aware of this potential problem.

#Edit : For everyday computing (surf the web, check emails, use Word processor...), you might also be interested in lightweight distributions of Ubuntu, ie. Xubuntu or Lubuntu.

Regards

---

### Post by slickymaster on 2015-02-06
Basically it's you choice.

LTS releases are designed to be stable platforms that you can stick with for a long time. Ubuntu guarantees LTS releases will receive security updates and other bug fixes as well as hardware support improvements for five years. The current LTS release, Ubuntu 14.04, will be supported until April 2019.

When support for 12.04 ends (April 2017) you won't get any updates but 12.04 will still work.

---

### Post by grahammechanical on 2015-02-06
> [COLOR=#000000]I am considering upgrading from 12.04 LTS to 14.04 LTS.[/COLOR]

Are you wanting to upgrade an existing 12.04 to 14.04? Or are you thinking of installing 14.04 in another partition? Ubuntu 14.04 will install in less than 8GB of space. I have frequently installed the very latest versions of Ubuntu in 10GB partitions. I am not clear whether this 12GB of free space is for another partition or is free space inside an existing 12.04 partition.

Regards.

---

### Post by Bobby_James on 2015-02-06
> **grahammechanical said:**
> Are you wanting to upgrade an existing 12.04 to 14.04? Or are you thinking of installing 14.04 in another partition? Ubuntu 14.04 will install in less than 8GB of space. I have frequently installed the very latest versions of Ubuntu in 10GB partitions. I am not clear whether this 12GB of free space is for another partition or is free space inside an existing 12.04 partition.

Regards.

It is free space in an existing 12.04 partition.

---

### Post by ajgreeny on 2015-02-06
What exactly is your partition layout; apart from swap, do you have just the one root partition for Ubuntu or have you also a separate /home or /data partition from which you could move some space?

On a previous installation of Ubuntu I had a root partition of 10GB, and a separate /home of 150GB from which I had to "steal" another 5GB when root got a bit too full for comfort.  It is very easy to do with gparted from a live system, but it is imperative that you just leave gparted to do its job, which will take a very long time (possibly an hour or two depending on partition sizes), and DO NOT cancel or stop it or you will do great damage and possibly lose all data and your OS.

As with all partition work it is sensible to have good backups of everything important to you just in case it all goes to worms.

---

### Post by monkeybrain20122 on 2015-02-06
Stay away from 'upgrade', it takes a long time and likely will leave you with a broken system especially if you have customised your system a lot and have third party software such as proprietary video driver. If you want 14.04, backup your data and do a fresh install, takes about 30 minutes to reinstall the OS and all the software. It would be even easier if you have a seperate /home partition. Personally I would get 14.04, 12.04 is too old by now IMO.

---

### Post by monkeybrain20122 on 2015-02-06
> **ajgreeny said:**
> 

On a previous installation of Ubuntu I had a root partition of 10GB, and a separate /home of 150GB from which I had to "steal" another 5GB when root got a bit too full for comfort.  It is very easy to do with gparted from a live system, but it is imperative that you just leave gparted to do its job, which will take a very long time (possibly an hour or two depending on partition sizes), and DO NOT cancel or stop it or you will do great damage and possibly lose all data and your OS.

.

Alternatively, you can  clone the file systems on both with fsarchiver, then delete/reformat the partitions, expand or shrink it as you want and restore the images. It may seem like more work in this case, but if you want to do more complicated reconfiguration (say I have dualboot and want to move or resize the /root and /home for the second OS to add a third, provided that no Windows is involved) the method above is must faster, safer and more flexible than using gparted alone.

---

### Post by deadflowr on 2015-02-06
> **Bobby_James said:**
> I am considering upgrading from 12.04 LTS to 14.04 LTS.

a) is there any reason not to upgrade?

b) I only have 12GB of free disk space. Is that enough?

Thanks!

answer for a: Laziness: why tempt fate when something you have works.
And then have to do a little extra work when it now does not work.

answer for b: it'll tell you how much space is needed to successfully upgrade, read that before proceeding.
It's doubtful, though, that you would need more than 12GB (more commonly you'd need no more than 2GB of free space). 

But I do not know how much stuff you've tried to install. So if you suffer from chronic-package-installation fever(where you install packages all the time, regardleess of anything else --but really, though you'd need to have installed likely thousands of oddball extra packages and program to reach 12GB ) then you could possibly exceed the 12GB threshold...

---

### Post by Bobby_James on 2015-02-06
> **ajgreeny said:**
> What exactly is your partition layout; apart from swap, do you have just the one root partition for Ubuntu or have you also a separate /home or /data partition from which you could move some space?


My partitions are somewhat messy:

#1 is Windows Recovery
#4 is Windows 8.
#5 is Ubuntu.
#6 is Samsung Recovery.
#7 is Samsung Recovery.

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  524MB  523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   839MB  315MB   fat32        EFI system partition          boot
 3      839MB   973MB  134MB                Microsoft reserved partition  msftres
 4      973MB   316GB  315GB   ntfs         Basic data partition          msftdata
 5      316GB   473GB  157GB   ext3         Basic data partition          msftdata
 6      473GB   499GB  26.2GB  ntfs         Basic data partition          hidden, diag
 7      499GB   500GB  1074MB  fat32        Basic data partition          hidden, diag
 8      473GB   473GB  1049kB                                             bios_grub

---

