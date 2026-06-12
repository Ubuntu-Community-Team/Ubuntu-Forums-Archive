---
title: "/ full 91%"
date: 2021-09-16
forum: General Help
---

### Post by Quarkrad on 2021-09-16
I've been here before (long time ago) but struggling I'm afraid.  I have separate **/** and **/home** on different partitions - **/** is 30GB and is 91% full!   I have mounted **/** as **/mnt/nvmeOn1p2** and have the following info:

```
dad@dadubuntu:/mnt/nvme0n1p2$ sudo du -hx --max-depth=1 / 2> /dev/null
716M	/var
88K	/tmp
6.8G	/usr
4.0K	/srv
808M	/opt
8.0K	/media
108M	/boot
8.0K	/mnt
3.5M	/root
4.0K	/cdrom
206M	/sambashare
24M	/etc
16K	/lost+found
10G	/

```

This is where I getting a little confused.  I think the above tells me **/ **or **/dev/nvme0n1p2** is 10G in size (I have confirmed this by looking at **/mnt/nvme0n1p2** via caja).  However, gparted is telling me **/** or **/dev/nvme0n1p2** is 30Gb and using 25Gb.  I have recently been playing with my rdiff-backup setup, which may not be relevant, when I started to get something like .... 'your root system is 91% full'.... message.

---

### Post by ActionParsnip on 2021-09-16
What is the output of:
```

sudo parted -l
uname -a
lsb_release -a

```
Thanks

---

### Post by Quarkrad on 2021-09-16
```
dad@dadubuntu:~$ sudo parted -l
[sudo] password for dad: 
Model: ATA KINGSTON SA400S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  120GB  120GB  ntfs               msftdata


Model: ATA Hitachi HUA72302 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA WDC WD20EZRX-22D (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ext4


Model: ATA KINGSTON SA400S3 (scsi)
Disk /dev/sdd: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  106MB  105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB  16.8MB               Microsoft reserved partition  msftres
 3      123MB   240GB  239GB   ntfs         Basic data partition          msftdata
 4      240GB   240GB  533MB   ntfs                                       hidden, diag


Model: Samsung SSD 970 EVO Plus 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  211MB   210MB   fat32        EFI System Partition  boot, esp
 2      211MB   31.7GB  31.5GB  ext4
 3      31.7GB  78.9GB  47.2GB  ext4
 4      78.9GB  289GB   210GB   ext4
 5      289GB   500GB   211GB   ext4


dad@dadubuntu:~$ uname -a
Linux dadubuntu 5.4.0-84-generic #94-Ubuntu SMP Thu Aug 26 20:27:37 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
dad@dadubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal

```

---

### Post by grahammechanical on 2021-09-16
@quarkrad

I do not understand the command that you have used. Please keep that in mind. I think that you are confusing the / partition size with the / folder size. In the / partition there are folders including / and /root. 

On my system Disk Usage Analyser is showing / folder as full. Which it would do because it is a folder that can vary in size. Or, so I think. The Disks utility is showing my / partition as 30% full. It is a 40GB partition with 28 GB free.

All of this stuff confuses me as well. Think of the partition as / and not as root. I do that and it becomes easier to understand. If you are getting messages that your / partition is getting full then you know what to do. Use GParted to expand the size of the partition.

Regards

---

### Post by Impavidus on 2021-09-16
gparted says it's full, but du doesn't see the files taking all that space. Could it be that some files are hiding underneath a mountpoint? We occasionally have people here who wrote their backups to /media/backups whilst their backup drive was unmounted, then mounted their backup drive and wondered why their disk was full.

---

### Post by Quarkrad on 2021-09-16
My backup drive is auto mounted via fstab - however, there is a possibility that something odd has happened.  I would like to investigate this. How would I go about searching for these backup or partial backup files that could be residing on /dev/nvme0n1p2?

---

### Post by oldfred on 2021-09-16
If data in a normal folder, you  can use ncdu.
change to / & run ncdu, if you see a large folder, you then click on it to see what is in it.

But it could be you deleted files as root user and then root's trash has data? That often is hidden and since trash not shown.
to also see hidden files.
sudo ncdu

---

### Post by philhughes on 2021-09-16
The way gparted shows your root file system is mounted appears strange to me. It shows the mount point as /./mnt/nvme0n1p2. I would expect it just to be "/". Can you post the contents of /etc/fstab?

---

### Post by Impavidus on 2021-09-16
> **Quarkrad said:**
> My backup drive is auto mounted via fstab - however, there is a possibility that something odd has happened.  I would like to investigate this. How would I go about searching for these backup or partial backup files that could be residing on /dev/nvme0n1p2?
You can unmount the other filesystems so that no mountpoints within your root partition are in use, then search again. It may be easier to do so from a live disk.
> **oldfred said:**
> If data in a normal folder, you  can use ncdu.
change to / & run ncdu, if you see a large folder, you then click on it to see what is in it.
Interesting tool, never heard of it. It doesn't appear to be installed by default. I guess the ncdu package needs to be installed.

> **philhughes said:**
> The way gparted shows your root file system is mounted appears strange to me. It shows the mount point as /./mnt/nvme0n1p2. I would expect it just to be "/". Can you post the contents of /etc/fstab?
Strange indeed. Having the root partition simultaneously mounted at / and /mnt/nvme0n1p2/ may confuse some tools.

---

### Post by Quarkrad on 2021-09-16
I'm struggling here - and beginning to wondering if I have a problem at all!  I did get a message/pop-up about / being full but the more I look into this the more I am confused.

gparted shows this odd mount point /mnt/nvmen0n1p2 because I created that mount point yesterday.  I was hoping to be able to 'see' what was in that partition. I (think) I understand everything is under / irrespective of physical partitions but as this / partition is the one that is full I'm struggling to use the terminal to examine just that partition. 

 I have a basic Desktop with nothing particularly complicated on it - although there are some kmv environments but they reside on a separate hd to my / and /home nvme ssd.  These kvm machines are accessed via /media/dad/virt.

Since 8.04 when I joined / has always had a small footprint and remained so (to a degree) whereas /home can/does grow.  I've always set my / partition to 20GB and had no problems.  So ..... a few months ago when I installed a new 500GB ssd and rebuilt I allocated 30GB for / and  47GB for /home.   I thought 30GB for / was far too large but I had the space (and when I installed 20.04 indeed the footprint of / was small).  My computer usage hasn't really changed so I'm confused/intrigued why / is now 25.17 GB - when I installed 20.04 I cannot remember what size  / was what, but it was way small than 10GB, now it has doubled????

I've had a go with ncdu but need more time with it as I need (again possibly confused) it to show me just my nvme0n1p2 partition.  I'm going to have a go at unmounting via a live cd as see if this helps me.

---

### Post by mikewhatever on 2021-09-16
Can you remove that extra mount point, and try the "du -..." again. I don't see any merrits of this double mount, it might just confuse df.

---

### Post by TheFu on 2021-09-16
> **Quarkrad said:**
>  gparted shows this odd mount point /mnt/nvmen0n1p2 because I created that mount point yesterday.  I was hoping to be able to 'see' what was in that partition. I (think) I understand everything is under / irrespective of physical partitions but as this / partition is the one that is full I'm struggling to use the terminal to examine just that partition. 

NEVER mount a file system more than 2 places at the same time, unless you are using a **-o bind** option. Pain comes with doing that, if it is even allowed.

> **Quarkrad said:**
>   I have a basic Desktop with nothing particularly complicated on it - although there are some kmv environments but they reside on a separate hd to my / and /home nvme ssd.  These kvm machines are accessed via /media/dad/virt.
20.04 storage requirements ballooned in the default install due to more snap packages being used. Snaps pull in dependencies which can cause multiple versions of huge dependent packages to be installed, instead of just 1. Further, each snap, by default, will keep 3 versions - effectively using 3x the amount of storage.  For example, **snap list** shows that I have
```
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  161    latest/stable  canonical&#10003;  -
gtk-common-themes  0.1-52-gb92ac40             1515   latest/stable  canonical&#10003;  -

```
gnome-3.xx is 200MB, so if I have 3 copies, slightly different versions, that would use 600MB, if I didn't do something about it. As part of my weekly patching, I remove the 2nd and 3rd copies of snaps from each of my systems that still have snaps.  I've purged the snapd subsystem from most of my systems. I don't want it. Don't need it.  But there are a few packages I need that are only available as snaps, so I'm screwed.  I much prefer AppImages or flatpaks over snaps, but each of them still have the bloat problem. There are other issues with each, but there are issues in using the normal .deb/Debian packages too.
If we aren't careful, normal packages that should be small, debian installs will be replaced with bloated snap versions - because Canonical is really pushing snaps, even when they make little sense.

> **Quarkrad said:**
> Since 8.04 when I joined / has always had a small footprint and remained so (to a degree) whereas /home can/does grow.  I've always set my / partition to 20GB and had no problems.  So ..... a few months ago when I installed a new 500GB ssd and rebuilt I allocated 30GB for / and  47GB for /home.   I thought 30GB for / was far too large but I had the space (and when I installed 20.04 indeed the footprint of / was small).  My computer usage hasn't really changed so I'm confused/intrigued why / is now 25.17 GB - when I installed 20.04 I cannot remember what size  / was what, but it was way small than 10GB, now it has doubled????
20.04 fresh installs, can use a swapfile instead of a swap partition.  **free -hm** will show the size and you can see it in / (I expect).  So, if your swap size is 8G, there will be an 8GB file added to / in addition to all the snaps included by default.

> **Quarkrad said:**
> I've had a go with ncdu but need more time with it as I need (again possibly confused) it to show me just my nvme0n1p2 partition.  I'm going to have a go at unmounting via a live cd as see if this helps me.

ncdu just shows what a du -sh would show in a TUI environment.

If you remove the backup media mounts and prevent those from automatic mounting, then ensure they aren't currently mounted, you can just cd down the directory tree to see if any files have been placed "under" the mount.  "files" means directories too, BTW.

The best way to see which file systems are used is with this command:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
That removes all the cruft and "fake" file systems that don't actually use any storage. It is a much cleaner view.

Also, when using du -sh .... I like to use 
```
du -sh * | sort -h
```
so the output is sorted and I know where to spend my time looking for the excess files and wasted storage.

Another command to see file systems, including more complex storage stuff is:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Between those 3 commands, we can see a good overview of the storage situation.

Don't forget that all Native-Unix file systems will reserve 5% of the blocks in a file system for use by root and only root.  This is important for file systems critical to the OS, but can waste a bunch of storage for pure data file systems.  For example, a 4TB drive that reserves 5% basically prevents use of the last 200GB.  That is just too much storage to waste in that way, so I tune the file system not to reserve any blocks on data-only file systems.  For ext2/3/4, use the tune2fs command for that.

Lastly, don't forget that there are 2 parts to how much storage we have on a file system.
[LIST]
[*]free blocks
[*]free inodes
[/LIST]
Running out of either means no more storage can be used.  All the commands above are showing blocks.  To see the inodes, use ```
df -ihT -x squashfs -x tmpfs -x devtmpfs
``` 
See how the EFI partition doesn't have any inodes?  FAT32 doesn't use them.  ext2/3/4, jfs, xfs, zfs, f2fs, and most other native Linux file systems do.  Don't run out of inodes. It is really bad when that happens.

---

### Post by Quarkrad on 2021-09-16
Thank you.  I have umounted and removed the /mnt/ mount point - gparted now shows the normal / mount point.  Following recent discussions re snaps I do not have it installed on my system.

```
dad@dadubuntu:~$ snap list

Command 'snap' not found, but can be installed with:

sudo apt install snapd

dad@dadubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4   29G   25G  2.7G  91% /
/dev/nvme0n1p4 ext4  192G  125G   58G  69% /media/dad/workspace
/dev/nvme0n1p3 ext4   44G   15G   26G  37% /home
/dev/nvme0n1p1 vfat  197M  5.2M  192M   3% /boot/efi
/dev/sdb1      ext4  1.8T  1.5T  254G  86% /media/dad/backup
dad@dadubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME          SIZE TYPE FSTYPE MOUNTPOINT
sda         111.8G disk        
&#9492;&#9472;sda1      111.8G part ntfs   
sdb           1.8T disk        
&#9492;&#9472;sdb1        1.8T part ext4   /media/dad/backup
sdc           1.8T disk        
&#9492;&#9472;sdc1        1.8T part ext4   
sdd         223.6G disk        
&#9500;&#9472;sdd1        100M part vfat   
&#9500;&#9472;sdd2         16M part        
&#9500;&#9472;sdd3        223G part ntfs   
&#9492;&#9472;sdd4        508M part ntfs   
sr0          1024M rom         
nvme0n1     465.8G disk        
&#9500;&#9472;nvme0n1p1   200M part vfat   /boot/efi
&#9500;&#9472;nvme0n1p2  29.3G part ext4   /
&#9500;&#9472;nvme0n1p3    44G part ext4   /home
&#9500;&#9472;nvme0n1p4 195.7G part ext4   /media/dad/workspace
&#9492;&#9472;nvme0n1p5 196.6G part ext4   
dad@dadubuntu:~$ df -ihT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type Inodes IUsed IFree IUse% Mounted on
/dev/nvme0n1p2 ext4   1.9M  244K  1.6M   13% /
/dev/nvme0n1p4 ext4    13M  106K   13M    1% /media/dad/workspace
/dev/nvme0n1p3 ext4   2.8M   39K  2.8M    2% /home
/dev/nvme0n1p1 vfat      0     0     0     - /boot/efi
/dev/sdb1      ext4   117M  339K  117M    1% /media/dad/backup
dad@dadubuntu:~$ 

```

---

### Post by TheFu on 2021-09-16
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4   29G   25G  2.7G  91% /
/dev/nvme0n1p4 ext4  192G  125G   58G  69% /media/dad/workspace
/dev/nvme0n1p3 ext4   44G   15G   26G  37% /home
/dev/nvme0n1p1 vfat  197M  5.2M  192M   3% /boot/efi
/dev/sdb1      ext4  1.8T  1.5T  254G  86% /media/dad/backup
```

This output shows me exactly why I love LVM.  Everything except /boot/efi would be inside LVM and the places with way too much storage would be smaller and I could add 10G more to / in about 10 seconds.  BTW, I've had to do that on my 20.04 system when my initial allocation proved to be insufficient.

As for finding what's using all the storage under /, there are many techniques. I'd start with 
```
sudo du -xsh /* | sort -h
```
The -x option prevents following down other file systems. The sudo is needed to prevent all the permission denied for root-only stuff.  I ended up with this:
```
4.0K    /media
4.0K    /mnt
4.0K    /srv
16K     /lost+found
64K     /snap
684K    /opt
872K    /tmp
1.3M    /run
9.9M    /root
19M     /etc
208M    /boot
6.7G    /home
7.3G    /var
7.4G    /usr

```
So, I don't need to look at anything under 500MB ... that leaves just 3 directories.  
```
6.7G    /home
7.3G    /var
7.4G    /usr

```
Seems my command isn't doing what I'd hoped. /home is on a different file system, so it shouldn't be in my list; that was my intent. See:
```
$ sudo du -xsh / | sort -h
15G     /
```
7.3G + 7.4G = 14.7G which is ~ 15G.  Interesting.
Next, I'd work my way down into /var and /usr level by level running the same **sudo du -xsh *| sort -h** at each level and paying attention only to the largest directories.
```
$ sudo du -xsh /var/* | sort -h
0       /var/lock
0       /var/run
4.0K    /var/local
4.0K    /var/mail
4.0K    /var/metrics
4.0K    /var/opt
28K     /var/tmp
612K    /var/www
1.1M    /var/snap
5.9M    /var/backups
6.5M    /var/spool
187M    /var/crash
265M    /var/log
2.6G    /var/cache
4.3G    /var/lib
```
Again, see how the *sort* brings the last 2 in the list to research and how all the others are unimportant?
```
$ sudo du -xsh /var/lib/* | sort -h
....
164M    /var/lib/apt
2.0G    /var/lib/snapd
2.1G    /var/lib/docker
```
Snaps and docker junk.  Hummmm.  Had to switch to root to continue in the docker/ subdir... 
```
# du -sh *| sort -h
...
5.4M    image
2.0G    overlay2
```
overlay2?  Huh?
```
# du -sh *| sort -h
133M    96e5adeed651ec3dda06e1dee03fc332e5e3116fc1937c61c59f4df57cc23c20
1.7G    e960ff412f69b02a5c933b78ae63077ef934fc6f24b799683e4e27f0d78aa7c9

```
And the next level 
```
# du -sh * |sort -h
0       committed
4.0K    link
4.0K    lower
4.0K    work
1.7G    diff
```
Ok ... so there's a docker container using too much space that I forgot about completely.  Looked up a command, 
```
$ docker images
```
which shows I have 2 docker containers - 85.1MB and 1.84GB with one 6 months old and the other 18 months old.  I'd forgotten about them completely.  Can't recall the last time I used docker - don't need it. Time to remove the images and remove docker from the system.  Before I do that, dft is an alias for my fancy **df -hT ....** command.
```
$ dft
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root ext4   19G   15G  2.9G  84% /

```
Ok, all cleaned up:
```
$ dft
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root ext4   19G   13G  5.1G  72% /
```

Thanks for making my work through this.  BTW, I did just get lucky as I went deeper into the directories and found docker stuff. I suppose that was just experience and some luck.  ncdu can probably do it too for people who don't type as quickly, but all the du commands will take longer when they aren't selective.

Back to the /var/lib/snapd directory .... 
```
/var/lib/snapd/snaps$ du -sh *|sort -h
4.0K    partial
33M     snapd_12883.snap
56M     core18_2128.snap
62M     core20_1081.snap
66M     gtk-common-themes_1515.snap
83M     scrcpy_283.snap
100M    core_11606.snap
143M    [COLOR="#800000"]chromium_1732[/COLOR].snap
143M    chromium_1753.snap
158M    freemind_4.snap
165M    gnome-3-28-1804_161.snap
```
Two copies of chromium?  Srsly?  Ok, removed the extra - only 140MB freed, but still.

---

### Post by TheFu on 2021-09-16
/var/cache/apt/archives/ has a bunch of packages that are cached, but not needed. Some examples:

```
37M     linux-modules-extra-5.4.0-45-generic_5.4.0-45.49_amd64.deb
37M     linux-modules-extra-5.4.0-48-generic_5.4.0-48.52_amd64.deb
37M     linux-modules-extra-5.4.0-51-generic_5.4.0-51.56_amd64.deb
37M     linux-modules-extra-5.4.0-52-generic_5.4.0-52.57_amd64.deb
37M     linux-modules-extra-5.4.0-53-generic_5.4.0-53.59_amd64.deb
37M     linux-modules-extra-5.4.0-54-generic_5.4.0-54.60_amd64.deb
37M     linux-modules-extra-5.4.0-58-generic_5.4.0-58.64_amd64.deb
37M     linux-modules-extra-5.4.0-60-generic_5.4.0-60.67_amd64.deb
37M     linux-modules-extra-5.4.0-62-generic_5.4.0-62.70_amd64.deb
37M     linux-modules-extra-5.4.0-64-generic_5.4.0-64.72_amd64.deb
37M     linux-modules-extra-5.4.0-66-generic_5.4.0-66.74_amd64.deb
38M     linux-modules-extra-5.4.0-67-generic_5.4.0-67.75_amd64.deb
38M     linux-modules-extra-5.4.0-70-generic_5.4.0-70.78_amd64.deb
38M     linux-modules-extra-5.4.0-72-generic_5.4.0-72.80_amd64.deb
38M     linux-modules-extra-5.4.0-73-generic_5.4.0-73.82_amd64.deb
38M     linux-modules-extra-5.4.0-74-generic_5.4.0-74.83_amd64.deb
38M     linux-modules-extra-5.4.0-77-generic_5.4.0-77.86_amd64.deb
38M     linux-modules-extra-5.4.0-80-generic_5.4.0-80.90_amd64.deb
38M     linux-modules-extra-5.4.0-81-generic_5.4.0-81.91_amd64.deb
38M     linux-modules-extra-5.4.0-84-generic_5.4.0-84.94_amd64.deb
```
I only need the last 2 kernels, so I only need the last 2 "extra" modules. All the others are just eating space.  I bet there are headers there too.  A quick **ls | wc -l **shows 830 packages.  For kernel stuff, I only need 5.4.0-81 and 5.4.0-84 versions.   Hummm.

Ok, so I have an apt caching system to speed up debian package installs on a different machine. It runs a program called apt-cacher-ng [https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server) , so there is little reason for any of my systems to have very much in /var/cache/apt/archives at all. All the current packages are in apt-cacher-ng.  I can be lazy.
```
sudo apt clean
```
```
And now 
Filesystem            Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root ext4   19G   11G  [COLOR="#008000"]**7.7G**[/COLOR]  57% /
```

So, for fun, I'm going to see how much storage is being wasted on all my running systems in /var/cache/apt/archives ... ansible will make that easy to answer:
```
$ ansible  -a "sudo du -sh /var/cache/apt/archives" current
24K     /var/cache/apt/archives
44K     /var/cache/apt/archives
76K     /var/cache/apt/archives
843K    /var/cache/apt/archives
46M     /var/cache/apt/archives
48M     /var/cache/apt/archives
723M    /var/cache/apt/archives
989M    /var/cache/apt/archives
1.1G    /var/cache/apt/archives
1.1G    /var/cache/apt/archives
1.3G    /var/cache/apt/archives
1.9G    /var/cache/apt/archives
2.6G    /var/cache/apt/archives
```
So 6 systems are wasting about 1G or more space.  BTW, ansible did output the hostnames for each, but I didn't want to share all those names here. Also, I sorted by size.  I like sorted output. ;)
Ok, all better now:
```
22K     /var/cache/apt/archives
24K     /var/cache/apt/archives
44K     /var/cache/apt/archives
76K     /var/cache/apt/archives
80K     /var/cache/apt/archives
84K     /var/cache/apt/archives
100K    /var/cache/apt/archives
156K    /var/cache/apt/archives
208K    /var/cache/apt/archives
224K    /var/cache/apt/archives
46M     /var/cache/apt/archives
48M     /var/cache/apt/archives
1.3G    /var/cache/apt/archives
```
The last box with 1.3G is the apt-cacher-ng system. It also has over 40TB of storage connected, so not really concerned about 2G.

Most people probably should leave the archive/ directory there, but probably want to clean up any extra, old, unused, packages that have been left behind.  Perhaps start by looking for packages that haven't been ***accessed*** in the last 6 months.
```
find /var/cache/apt/archives  -atime +180  -ls
```
Wow. There are a bunch.  After running **sudo apt autoclean**, what is left are packages that cannot be downloaded again through the repos.  That explains why so many old kernel helpers are there.  For a long time, I didn't run autoclean quickly and as those specific packages are removed from the repos, they are orphaned on my systems.  Not installed and still in the local archive is useless. I'll likely never need to install them again, so they aren't doing any good for me. If they haven't been accessed in the last 6 months, do I even need them?  I'd say nope.
```
sudo find /var/cache/apt/archives  -atime +180  -delete
``` took care of those.
Before, 
```
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-root ext4  101G   50G   47G  52% /

```after, 
```
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-root ext4  101G   50G   47G  52% /

```
No real difference - at least for the amount of storage on that system in /.  If I were tight on / or /var on a system, I'd definitely run **sudo apt clean** in the very early steps.

Often times, Unix system have run-away logs and some log files will be writing 1G for every 10 minutes when something really bad happens.  I've seen that a few times on my systems.  I actually setup a task that checks space on an email server every 10 minutes after it did that in 2020, filling the available storage constantly.  For about a week, it was very important until I figured out the issue and solve it.  That watchdog task still runs, but it hasn't complained in a very long time.  Just checked. That former runaway log file is 4M. ;)

---

### Post by Quarkrad on 2021-09-17
I have had a quick run through your commands (thank you for detailing so much work) and at first glance everything looks OK.  However, I will go through it all again slowly/closely.  One bit of confusion, and I have seen this before, is:

```
dad@dadubuntu:~$ sudo du -xsh / | sort -h
10G	/
```

I obviously accept this but **GParted** and **Disks** both state that / is 25GB

---

### Post by TheFu on 2021-09-17
> **Quarkrad said:**
> I have had a quick run through your commands (thank you for detailing so much work) and at first glance everything looks OK.  However, I will go through it all again slowly/closely.  One bit of confusion, and I have seen this before, is:

```
dad@dadubuntu:~$ sudo du -xsh / | sort -h
10G	/
```

I obviously accept this but **GParted** and **Disks** both state that / is 25GB

I'm guessing you mean 25G is used, not the total size.

**Gparted** shows the partition size.
**du** shows the used amount of block space it can find.

If du and parted/fdisk show different used amounts of space, then du cannot see the missing storage and it is almost certainly hidden under some other mounts as others pointed out above.  15G is a bunch of storage to be lost.  Suppose the "automatic mount" for your backup storage didn't work once.  Would the backup task continue anyway, create directories, and write the data to where it thinks you want it?  That is very common. There are many different ways to have a backup script verify that the backup storage is mounted before continuing. You'll want to set that up so this issue doesn't happen again.

You aren't the first to do this.  We've all done it.  I think HermanAB has an elegant solution by creating a .NOT-MOUNTED file in the directory where some other partition/file system will be mounted.  If the backup scripts can see /mnt/backups/.NOT-MOUNTED, then there is a mount failure and nothing should be written until that is fixed.  Another way is to look for /mnt/backups/lost+found/, since all native Linux file systems will create that directory at the root of the file system.  This is a positive test, rather than a negative test like the .NOT-MOUNTED file.
I always did it the harder way that checks the **mount** command output for the expected mounted storage being in the correct location. There are flaws with each.

The easiest way to find the missing storage is to boot into a *Try Ubuntu* environment and do the same searches for storage on the drives when they are each mounted to non-standard locations.  By booting from alternate media, the normal / file system will be mounted somewhere else and you will be able to look under /mnt/old-root/media for files/directories that you though were only on the backup disk.

---

### Post by Quarkrad on 2021-09-17
Afraid I'm going to need some help with terminal commands - especially remounting / in the live environment.  pic 1 shows there is 15GB on /    (taken from a live environment).  Seems I'm getting all sorts of numbers for the size of /

---

### Post by Quarkrad on 2021-09-17
As rdiff-backup is my backup tool I did a search for rdiff-backup and found many of files. However, they were (in total) small and looked like the application files themselves.  Searching for actual file names that would have been backed up by rdiff-backup  resulted in nothing, so it looks to me, there are no partial rdiff-backups in /

---

### Post by Impavidus on 2021-09-17
You used the filemanager to mount that filesystem. Now use du to analyse it:```
sudo du -xh --max-depth=2 /media/ubuntu-mate/35d5b79d-ae24-4c02-8d96-4ae452ed88d1
```I hope I copied that UUID correctly.

Your filemanager may be confused by the symlinks, counting some files double.

---

### Post by TheFu on 2021-09-17
> **Quarkrad said:**
> As rdiff-backup is my backup tool I did a search for rdiff-backup and found many of files. However, they were (in total) small and looked like the application files themselves.  Searching for actual file names that would have been backed up by rdiff-backup  resulted in nothing, so it looks to me, there are no partial rdiff-backups in /

To find if any rdiff-backup versions are in a tree, use
find /path/to/tree -type d -iname rdiff-backup-data/

So, on my backup server, I put backups onto a mount somewhere, but make a convenience symlink from /Backups to that location.  That means I need to trick "find" into dereferencing the top link into the mount ... using "/Backups[COLOR="#FF0000"]/[/COLOR]" with the trailing / character.  Without that, it is on the / file system, not the other one.  I need sudo because backup areas can be blocked off so only root has access. There are definitely some subdirs on each system that only root can access as well. That's how I roll/role. ;)
```
sudo find /Backups/  -type d -name rdiff-backup-data
```
That searches for the versioning directory for each backup area (I probably have 15-20 different systems on that disk). 

The find takes a long while. A few results  are:
```
/Backups/cb35/rdiff-backup-data
/Backups/lubuntu/rdiff-backup-data
/Backups/mail.jdpfu.com/rdiff-backup-data
/Backups/romulus/rdiff-backup-data
.... 

```
You get the idea.

If you don't really know where, then mount each file system under the Try Ubuntu environment ... perhaps to some temporary mounts like:
/mnt/a1
/mnt/a2
/mnt/a3
/mnt/b1
/mnt/b2
/mnt/b3
....
and use 
```
sudo find  /mnt/ -type d -name rdiff-backup-data
```

This won't work running in the normal environment or with the partitions mounted where they normally would be mounted.  That's the problem that is hiding there the data is - there is almost certainly a mount placed over the files you want.

You can also look through the different rdiff-backup sets and look for missing days in your list.  I backup daily, but sometimes my laptop isn't on when it is time for backups ... so a few days each week don't happen. It is just a laptop and doesn't actually have anything critical on it. It is never my "system of record" for anything.  Anyway, 
```
$ sudo rdiff-backup --list-increments /Backups/posc
Found 80 increments:
    increments.2021-06-20T00:07:03-04:00.dir   Sun Jun 20 00:07:03 2021
    increments.2021-06-22T00:07:03-04:00.dir   Tue Jun 22 00:07:03 2021
    increments.2021-06-23T00:07:04-04:00.dir   Wed Jun 23 00:07:04 2021
    increments.2021-06-24T00:07:04-04:00.dir   Thu Jun 24 00:07:04 2021
    increments.2021-06-25T00:07:05-04:00.dir   Fri Jun 25 00:07:05 2021
    increments.2021-06-26T00:07:04-04:00.dir   Sat Jun 26 00:07:04 2021
    increments.2021-06-27T00:07:03-04:00.dir   Sun Jun 27 00:07:03 2021
    increments.2021-06-28T00:07:03-04:00.dir   Mon Jun 28 00:07:03 2021
    increments.2021-06-29T00:07:03-04:00.dir   Tue Jun 29 00:07:03 2021
...
    increments.2021-09-12T00:07:04-04:00.dir   Sun Sep 12 00:07:04 2021
    increments.2021-09-13T00:07:03-04:00.dir   Mon Sep 13 00:07:03 2021
    increments.2021-09-15T00:07:04-04:00.dir   Wed Sep 15 00:07:04 2021
    increments.2021-09-16T00:07:03-04:00.dir   Thu Sep 16 00:07:03 2021
Current mirror: Fri Sep 17 00:07:05 2021
```
So, it is clear that Jun 21st, Sept 11th, 14th,  backups are missing.  On your system, that would be the nights where the backup storage probably wasn't mounted correctly ... so look under the mount location there.  The backup needs to be umount'ed to look, right?  If all the versions are there, per your automatic backup schedule, none missing, then that isn't the disk you need to worry about.  Move on and look for another partition/LV/subvolume (normal/LVM/btrfs storage terms) that may not have been mounted where and when expected, but is now.

---

### Post by Quarkrad on 2021-09-18
Finally - solved, **/ **has gone down from 25G to 10G - there maybe other bits & pieces so I will have a closer look around.   It seemed my problem was an rdiff-backup that backed itself up to my **/** partition instead of /media/dad/backup/rdiffbackup where it is supposed to go..  @TheFu gave me a pointer in #17 when he said "Suppose the "automatic mount" for your backup storage didn't work once" - it looks like that is exactly what happened.  I will start another thread to get some more information/help on this .NOT-MOUNTED file. Thank you everyone who has helped me with this, to me, confusion.

---

### Post by TheFu on 2021-09-18
> **Quarkrad said:**
> Finally - solved, **/ **has gone down from 25G to 10G - there maybe other bits & pieces so I will have a closer look around.   It seemed my problem was an rdiff-backup that backed itself up to my **/** partition instead of /media/dad/backup/rdiffbackup where it is supposed to go..  @TheFu gave me a pointer in #17 when he said "Suppose the "automatic mount" for your backup storage didn't work once" - it looks like that is exactly what happened.  I will start another thread to get some more information/help on this .NOT-MOUNTED file. Thank you everyone who has helped me with this, to me, confusion.

Actually, in post #5, Impavidus, said 
> gparted says it's full, but du doesn't see the files taking all that space. **Could it be that some files are hiding underneath a mountpoint?** We occasionally have people here who wrote their backups to /media/backups whilst their backup drive was unmounted, then mounted their backup drive and wondered why their disk was full. 
That is what I picked up on and followed as the nearly 100% most likely issue whenever multiple GB is being used, but cannot be located.

Search the forums for HermanAB's mount-checking/validation technique. It takes advantage of the fact that when we mount a file system on a directory, that hides the files inside.  If there is a zero-length file there BEFORE the mount, then after the mount, it won't be seen.  Basically, that file uses an inode, but only 1 storage block. Very efficient.  None of us invented these things.  We all saw someone else doing it first and almost always for exactly this issue.

---

