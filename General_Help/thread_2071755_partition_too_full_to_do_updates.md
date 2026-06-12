---
title: "partition too full to do updates"
date: 2012-10-16
forum: General Help
---

### Post by reach on 2012-10-16
Hi there!
I'm a noob, hope you'll still help me:
Ubuntu Server 12.04

I tried to install the regular update using apt-get upgrade and apt-get dist-upgrade, but it doesn't work, because there seems to be a dependency issue with linux-headers-3.2.0-32....

Apparently this can be resolved using apt-get -f autoremove 

But this doesn't work, because the process ends with something like "blabla couldn't be created because: No space left on device. No log created, because the error code indicates a full harddrive" 
(I don't post the full message because it's german, hence useless for most of you)


But what's full? Here's what df -h returns:
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       1,9G  1,4G  419M  77% /
udev            989M  4,0K  989M   1% /dev
tmpfs           399M  996K  398M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            997M     0  997M   0% /run/shm
/dev/sda1        92M   62M   25M  72% /boot
/dev/sda6       1,9G  790M  992M  45% /var
/dev/sda4       1,8T  1,3T  444G  75% /srv1
/dev/sdb1       1,8T  749G  992G  44% /srv2

Any idea which partition could give me problems?

Thx!
reach

---

### Post by newb85 on 2012-10-16
My money would be on your root partition.  It's only 77% full, but you're only 419 MB from full.  1.9 GB isn't a whole lot of space for /.

---

### Post by mcduck on 2012-10-16
> **newb85 said:**
> My money would be on your root partition.  It's only 77% full, but you're only 419 MB from full.  1.9 GB isn't a whole lot of space for /.

Since the error comes when trying to insall a kernel, it's also very likely to be related to the space available on the /boot partition. 25MB sure isn't enough for adding a new kernel...

---

### Post by reach on 2012-10-16
> **mcduck said:**
> Since the error comes when trying to insall a kernel, it's also very likely to be related to the space available on the /boot partition. 25MB sure isn't enough for adding a new kernel...

sounds logical, but how to clean it up? Just delete the old kernel files?

What's surprising me:
I read several tutorials and every single one recommended 100MB. Even more: my system is only a few weeks old!! I did one dist-upgrade already. Can this be the cause of the problem? That the old kernel isn't deleted automatically?

---

### Post by mcduck on 2012-10-16
> **reach said:**
> sounds logical, but how to clean it up? Just delete the old kernel files?

What's surprising me:
I read several tutorials and every single one recommended 100MB. Even more: my system is only a few weeks old!! I did one dist-upgrade already. Can this be the cause of the problem? That the old kernel isn't deleted automatically?

I wonder how old tutorials you might have been reading, in general a seaparate /boot partition isn't even recommended for any normal situation. It was mostly used on older systems where BIOS wasn't able to handle a large hard drive, and therefore you needed a smaller partition to boot from. 

Anyway, a kernel update doesn't actually replace the old kernel version, but instead installs the new version alongside the old one. This way you can always test the new kernel to be sure it's working correctly for you, and in case you get any troubles you'll still have the option of booting with the old kernel.

To get rid of the old kernel(s) you have installed, you should just uninstall them using the package management. Search for old versions of linux-image-*version* and linux-headers-*version* packages. (where the *version* is the version number of the kernel, you don't want to remove the linux-image or linux-headers metapackages)

---

### Post by reach on 2012-10-16
Interesting, thanks!
But too late for me :(
I found the following post:

> I had a similar problem and what i found that worked for me was going into /var/lib/dpkg/info and deleting everything that had that name and you may also have to go into /var/cache/apt/archives and do the same thing. I'm fairly new to linux so if this breaks anything i am sorry. i haven't run into any problems yet that this has caused.

And followed those instructions. I only read later that this wasn't the best recommendation :/
Now I can't ssh my server any more. Hope I can fix it when I'm back home. Otherwise I'll set it up new and consider your recommendation regarding /boot

BTW: do you know a newer recommendation for partitioning? Those I read weren't really old IMHO, but I don't remember.

Thx!
reach

---

### Post by muteXe on 2012-10-16
gparted. comes with the distro, although you'll have to use if from a live cd with your partition unmounted if you wanna have a mess with that.

---

### Post by oldfred on 2012-10-16
My standard suggestion on partitioning.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI if drive ever may be moved to new system)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I use 25GB for / and that includes my /home which is about 2GB mostly .wine and the hidden USER configurations files. All my data is in other data partitions.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
/etInstall with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Details on system partitions, more for complex or server systems
[http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html)

---

