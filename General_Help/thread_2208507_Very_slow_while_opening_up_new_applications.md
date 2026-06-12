---
title: "Very slow while opening up new applications"
date: 2014-02-28
forum: General Help
---

### Post by Vaneet_Goyal on 2014-02-28
I am new to the Linux platform and have been experimenting with KUBUNTU and LUBUNTU on a fairly old HP laptop (Intel 1.73 Ghz dual core processor, 1 GB RAM, 160 GB hard disc, GeForce 7400 nvidia graphics card). I recently revived it from a crash and don't want to use windows anymore :) 

I installed KUBUNTU first and soon realized that LUBUNTU would suit me best. I purged the KDE components and installed the LUBUNTU desktop as described in various forums. I have also installed standard programs like VLC. libreoffice, gimp, cheese etc.  

There's a dramatic change in the speed and the system runs very smoothly. But the only problem I have is that the system takes a while to load applications. I need to wait c.5 seconds before an application (like Chromium, firefox, folders, vlc....) would load. After loading the system runs very fast, smooth and without any issues.

Please suggest if I could make any changes to decrease the loading time for applications. Thanks

---

### Post by Vaneet_Goyal on 2014-02-28
Other information I forgot to mention:

UBUNTU: 
Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-59-generic-pae
GNOME 3.4.2

System Status:
Available disk space: 1.9 GB (Although I have more than 60 gigs to spare in another module. The module on which LUBUNTU is mounted is only 10 GB)

---

### Post by mörgæs on 2014-03-01
Hi, welcome to the fora.

Please post (in CODE tags) the output from **df -m**.

---

### Post by Vaneet_Goyal on 2014-03-01
```
Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/sda1           9387  7133      1778  81% /
udev                 491     1       491   1% /dev
tmpfs                200     1       200   1% /run
none                   5     0         5   0% /run/lock
none                 500     9       492   2% /run/shm
```

---

### Post by mörgæs on 2014-03-01
As you mentioned yourself you have very little space left on the disk, which is unhealthy. Normally fragmentation is no problem on Linux but it becomes a problem when the system is choking. 

Your installation is a K/L/Ubuntu mixture and an old one, too (12.04). The Lubuntu parts are unsupported. 

I suggest moving everything of value out of sda1 and doing a fresh install of Lubuntu 13.10. Maybe more adjustments are necessary but this is a good first step.

---

### Post by Vaneet_Goyal on 2014-03-01
Thanks [mörgæs]("http://ubuntuforums.org/member.php?u=939075"). Will do a fresh installation of 13.10. Is it possible to increase disk space for the time being (maybe use some of the 60gigs from another module which is just sitting idle)?

---

### Post by mörgæs on 2014-03-02
What exactly do you mean by module? Hard disk / partition / ... ?

---

### Post by amjjawad on 2014-03-02
Hi,

I highly appreciate you do a full backup for your data, use GParted to create new partition table, prepare your partitions:

Root Partition (10GB - 20GB)
Swap Partition (1GB - 2GB)
Home Partition (the rest)

And then install either:
Lubuntu 13.10
or
Xubuntu 12.04.4 LTS

Note: in 17th of April, 14.04 LTS will be released and no matter what direction you choose, you can upgrade to 14.04 once released.

How to backup?
Either you copy-paste your 'Home' Folder
Or, see this:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

More about partitioning?
[https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html](https://help.ubuntu.com/lts/installation-guide/amd64/partitioning.html)

And the internet is full of HOWTOs and Guides :)

Support for different cycles?
 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you do need any help, please ask :)

---

### Post by Vaneet_Goyal on 2014-03-02
Thanks [mörgæs]("http://ubuntuforums.org/member.php?u=939075") and [amjjawad]("http://ubuntuforums.org/member.php?u=941822"). Like you guys suggested, I have done a full installation of Lubuntu 13.10 and increased the root partition. I still have the same problem and chromium still takes a lot of time to load. Again, the system runs smoothly once any application like chromium, firefox, xpad, libreoffice, vlc etc. loads. Its only the initial load time of every application that's a problem for me. Please find below the output for df -m

```

Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/sda7          57990  4047     50975   8% /
none                   1     0         1   0% /sys/fs/cgroup
udev                 492     1       492   1% /dev
tmpfs                101     2       100   2% /run
none                   5     0         5   0% /run/lock
none                 501     1       501   1% /run/shm
none                 100     1       100   1% /run/user
```

Would appreciate any further suggestions. Thanks :)

---

### Post by Vaneet_Goyal on 2014-03-02
Also, please note that I have reduced the swapiness to 10 as suggested in some of the forums.

---

### Post by amjjawad on 2014-03-02
Hi,

Could you please post the output of:

```
sudo fdisk -l


```

Please put the output between 'code' tags.

Thank you!

---

### Post by Vaneet_Goyal on 2014-03-02
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93b97aa3


   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        2046   312560639   156279297    f  W95 Ext'd (LBA)
/dev/sda5       122881248   312560639    94839696    7  HPFS/NTFS/exFAT
/dev/sda6            2048     1953791      975872   82  Linux swap / Solaris
/dev/sda7         1955840   122879999    60462080   83  Linux


Partition table entries are not in disk order



```

---

### Post by amjjawad on 2014-03-02
> **Vaneet_Goyal said:**
> ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93b97aa3


   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        2046   312560639   156279297    f  W95 Ext'd (LBA)
/dev/sda5       122881248   312560639    94839696    7  HPFS/NTFS/exFAT
/dev/sda6            2048     1953791      975872   82  Linux swap / Solaris
/dev/sda7         1955840   122879999    60462080   83  Linux


Partition table entries are not in disk order



```

Hi and thanks for posting!

I see you didn't go for my previous suggestion to create 'new' partition table and start planning for your partitions as suggested.
If you're not dual-booting and Linux is the only system installed and there is only just one, usually, your partitions should be:

/dev/sda1 = root
/dev/sda2 = home
/dev/sda3 = swap

If your RAM is 1GB then SWAP = RAM or 2xRAM
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

As per your 'current' partitions scheme, I see you're not using /home partition. You can do a simple google search and it will give you many links of why having a home partition (/home) is important :)

From experience, and in order not to have any kind of issues in the future, I suggest to:

1- Backup your files
2- Create New partition table using GParted
3- Create 3 partitions - as I explained on my previous post
4- Install Lubuntu 13.10

As for programs being slow, I suggest to not use Chromium browser on 1GB RAM - [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603)

This is one of my machines: [http://phillw.net/hardware/BnA9pw11](http://phillw.net/hardware/BnA9pw11)
It has less than 512MB RAM and it works fine :)

Don't expect your machine to be super fast. 1GB of RAM and Lubuntu is okay and should give you average performance - that 100% depends on what you're using.

For example: don't expect to open 10 tabs on any browser and your machine will be responsive - just an example.

---

### Post by Vaneet_Goyal on 2014-03-02
Thanks [amjjawad]("http://ubuntuforums.org/member.php?u=941822"). I guess I will wait for the new installation until after the new version is released in April and keep these pointers in mind while creating a new partition table. 
[COLOR=#000000]
And, agree with your point on 10 tabs. Didn't work!!! :P[/COLOR]

---

### Post by amjjawad on 2014-03-02
> **Vaneet_Goyal said:**
> Thanks [amjjawad]("http://ubuntuforums.org/member.php?u=941822"). I guess I will wait for the new installation until after the new version is released in April and keep these pointers in mind while creating a new partition table. 
[COLOR=#000000]
And, agree with your point on 10 tabs. Didn't work!!! :P[/COLOR]

Hi,

You can always upgrade ;)
But I do understand that is your choice and I respect it.

I'm using now Core i5 2nd generation with 8GB RAM. When I login to my desktop (Xubuntu 12.04.4), and run Firefox, it needs 1 second or less. When I run Chromium, it takes 5 seconds or so to show up. So, if an application will take sometime, that does not mean there is something wrong :)

On my 512MB RAM machines, two tabs, one is facebook and one is Gmail ... and the machine will start smoking :P

Nowadays, almost all the well-known websites are very demanding. Not to mention YouTube, watching movies, etc.

If you need anything, please let us know :)

---

### Post by mörgæs on 2014-03-02
Your partitioning is a classic one (and more or less the only one possible) if you want a dual boot. When support for 13.10 is running out in June you can easily delete sda6 and 7 and install 14.04 in the free space.

If your Windows is XP be aware that support is only through middle of April. 

A separate /home will not give you more speed. If a low swapiness didn't help I guess you have to add some memory or just accept the speed as it is. 

Now you have plenty of space but if you get into a similar problem it's a good habit to run ```
sudo apt-get autoremove
``` once in a while.

---

