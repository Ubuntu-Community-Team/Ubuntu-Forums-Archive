---
title: "Root file fills VERY quickly one day after fresh install"
date: 2016-03-11
forum: General Help
---

### Post by Fsirett on 2016-03-11
Sorry to bother you all again. I had to reinstall again after having found my root folder filled right up. I thought I had just made an error in the size and I went really crazy! I set aside 100Gb for the root folder. My /home folder is on a completely different drive. 

In any case, I have a 100Gb root followed by a 25Gb swap and the rest of the drive (1Tb) is empty and unused at the moment. 

As I say, my /home folder is (supposed to be!) on a completely different drive and I reinstalled yesterday morning. 

A little while ago, I was warned that my root folder is quickly filling. I have a sneaking suspicion that something might be very wrong.

I have looked at other posts on this subject, but I am not at all certain I understand what they are talking about or how to solve the problem.

I am quite prepared to reinstall once again...and a good thing, too, since I suspect I am going to have to do just that!

From the conversation at [http://ubuntuforums.org/showthread.php?t=2067795](http://ubuntuforums.org/showthread.php?t=2067795)

Here is my blkid report

```
frank@frank:~$ sudo blkid[sudo] password for frank: 
/dev/sda1: UUID="6ac24eb5-c113-4715-9f03-392a5833cff2" TYPE="ext4" PARTUUID="85d56110-01"
/dev/sda5: UUID="642bc694-fa8d-4ab4-bb40-bdad67424580" TYPE="swap" PARTUUID="85d56110-05"
/dev/sdb1: UUID="bc2d4482-c278-40e8-9862-cdd7e4679ce6" TYPE="ext4" PARTUUID="0008b2e1-01"
/dev/sdb5: UUID="2c9bc47c-925d-4123-b518-93580a5a1eba" TYPE="swap" PARTUUID="0008b2e1-05"
/dev/sdc1: LABEL="6a" UUID="da5ddedd-0748-49a5-8483-db9137e48e85" TYPE="ext3" PARTUUID="5d1c6b14-01"
/dev/sdc2: LABEL="6b Documents" UUID="d8658713-6c7a-4e06-84c3-4046c6b62393" TYPE="ext3" PARTUUID="5d1c6b14-02"
/dev/sdc3: LABEL="6c Music" UUID="1f61b3ec-0a12-4b4a-ad3e-db550d98a244" TYPE="ext3" PARTUUID="5d1c6b14-03"
/dev/sdc4: LABEL="6d Downloads" UUID="3fde030a-4b08-4c33-9025-6e81bf0d06c7" TYPE="ext3" PARTUUID="5d1c6b14-04"
/dev/sdd1: LABEL="Five" UUID="b896603d-f8e3-4e1e-9434-51b8f1dedcd0" TYPE="ext4" PARTUUID="0006e6a2-01"
/dev/sdd2: LABEL="Four" UUID="64e5b3bb-9838-4187-9fff-2afc6e7f2c92" TYPE="ext4" PARTUUID="0006e6a2-02"
/dev/sde1: LABEL="My Passport" UUID="B4D48115D480DB4E" TYPE="ntfs" PARTUUID="0004a183-01"
frank@frank:
```

Since I see there are many reports asked for in that conversation, let me include those here. Indeed! Even though I have moved my /home folder to another drive, it appears it is still operating on one within the root folder. I see the dev/sdc1 drive (the new /home, the one I actually want to be using, is in use

Here are my sudo du -hs results.

```
frank@frank:~$ sudo du -hs /*
13M    /bin
91M    /boot
4,0K    /cdrom
580K    /dev
17M    /etc
176G    /home
0    /initrd.img
0    /initrd.img.old
581M    /lib
3,7M    /lib32
4,0K    /lib64
16K    /lost+found
491G    /media
4,0K    /mnt
178M    /opt
du: cannot access &#8216;/proc/1569/task/1569/fdinfo/16&#8217;: No such file or directory
du: cannot access &#8216;/proc/16252/task/16252/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16252/task/16252/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16252/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16252/fdinfo/4&#8217;: No such file or directory
0    /proc
6,6M    /root
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
9,6M    /run
13M    /sbin
4,0K    /srv
0    /sys
596K    /tmp
4,9G    /usr
86G    /var
0    /vmlinuz
0    /vmlinuz.old
frank@frank:~$ 
```

Looking farther, I moved a rather large file from the downloads folder to my partition labelled downloads ( used to keep downloads in a new staging area and keeping my /home folder reasonably sized. I note that when I did this, I see a reduction in the /dev/sda1 root folder as well as in my /dev/sdc1 partition that is called /home that I am using as my real /home. Very confusing 
   
The new, post move du -hs report is:

```
frank@frank:~$ sudo du -hs /*
13M    /bin
91M    /boot
4,0K    /cdrom
580K    /dev
17M    /etc
109G    /home
0    /initrd.img
0    /initrd.img.old
581M    /lib
3,7M    /lib32
4,0K    /lib64
16K    /lost+found
558G    /media
4,0K    /mnt
178M    /opt
du: cannot access &#8216;/proc/16730/task/16730/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16730/task/16730/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16730/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/16730/fdinfo/4&#8217;: No such file or directory
0    /proc
6,6M    /root
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
9,6M    /run
13M    /sbin
4,0K    /srv
0    /sys
596K    /tmp
4,9G    /usr
86G    /var
0    /vmlinuz
0    /vmlinuz.old
frank@frank:~$ 



```


Something I notice here is that there is a /home folder there. I thought I had moved that to another drive. In fact I am certain I did, but this report says I have it in the root file as well! I suspect that might be a part of the problem. I am moving a large part of the download folder to another place to see if that will make a difference. However, I notice that when I look at the properties of my /home folder, it says I have free space in keeping with my new /home partition. However it is a little larger than that reported for the /home folder in the root file

My df -h report is:

```
frank@frank:~$ sudo df -h
[sudo] password for frank: 
Filesystem      Size  Used Avail Use% Mounted on
udev            3,4G     0  3,4G   0% /dev
tmpfs           692M  9,6M  683M   2% /run
/dev/sda1        92G   92G     0 100% /
tmpfs           3,4G   28M  3,4G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           3,4G     0  3,4G   0% /sys/fs/cgroup
/dev/sdc1       477G  144G  310G  32% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           692M   84K  692M   1% /run/user/1000
/dev/sde1       466G  287G  180G  62% /media/frank/My Passport
/dev/sdc4       387G   62G  306G  17% /media/frank/6d Downloads
/dev/sdc3       478G   24G  430G   6% /media/frank/6c Music
/dev/sdc2       486G  8,4G  453G   2% /media/frank/6b Documents
/dev/sdd2       484G  150G  310G  33% /media/frank/Four
frank@frank:~$ 
```

I see that I have indeed put my /home folder on /sdc1, but there is also a (very full) /home file on the root folder. 

From the df -Th I get this:

```
frank@frank:~$ sudo df -Th 
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3,4G     0  3,4G   0% /dev
tmpfs          tmpfs     692M  9,6M  683M   2% /run
/dev/sda1      ext4       92G   92G     0 100% /
tmpfs          tmpfs     3,4G   28M  3,4G   1% /dev/shm
tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock
tmpfs          tmpfs     3,4G     0  3,4G   0% /sys/fs/cgroup
/dev/sdc1      ext4      477G  119G  334G  27% /home
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     692M   84K  692M   1% /run/user/1000
/dev/sde1      fuseblk   466G  287G  180G  62% /media/frank/My Passport
/dev/sdc4      ext3      387G   87G  281G  24% /media/frank/6d Downloads
/dev/sdc3      ext3      478G   24G  430G   6% /media/frank/6c Music
/dev/sdc2      ext3      486G  8,4G  453G   2% /media/frank/6b Documents
/dev/sdd2      ext4      484G  150G  310G  33% /media/frank/Four
frank@frank:~$ 
```

From the Mount command I get:

```
frank@frank:~$ mount 
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3527328k,nr_inodes=881832,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=708532k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sdc1 on /home type ext4 (rw,relatime,data=ordered)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=708532k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sde1 on /media/frank/My Passport type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc4 on /media/frank/6d Downloads type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdc3 on /media/frank/6c Music type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdc2 on /media/frank/6b Documents type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdd2 on /media/frank/Four type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
frank@frank:~$ 
```

That is not at all clear to me as to what it signifies, I am afraid.

And last I see they asked for parted -l. Here is what that turned up.

```
frank@frank:~$ sudo parted -l
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  100GB   100GB   primary   ext4            boot
 2      100GB   1000GB  900GB   extended
 5      100GB   125GB   25,0GB  logical   linux-swap(v1)




Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  241GB  241GB   primary   ext4            boot
 2      241GB   250GB  8588MB  extended
 5      241GB   250GB  8588MB  logical   linux-swap(v1)




Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size   Type     File system  Flags
 1      1049kB  520GB   520GB  primary  ext3
 2      520GB   1050GB  530GB  primary  ext3
 3      1050GB  1571GB  521GB  primary  ext3
 4      1571GB  1993GB  422GB  primary  ext3




Model: ATA WDC WD10EZEX-00U (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size   Type     File system  Flags
 1      1049kB  473GB   473GB  primary  ext4
 2      473GB   1000GB  528GB  primary  ext4         boot




Model: WD Elements 10A2 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot




frank@frank:~$ 
```

So from what I can see, it would appear I have a second /home folder that is accepting entries that seem to be mirroring my real /home folder, more or less. However, that may not be my only problem. 

I am interested...I think that is synonymous with grovelling, begging and praying for...in learning what my problems may be and how to solve them. As it stands, I am now beating my head against the wall to my great relief, when faced with this problem.

Thanks for your help...again!

Frank Sirett

---

### Post by montag dp on 2016-03-11
Somehow you've messed up the partitioning (clearly). Now, I'm not necessarily sure what you did wrong, but I will say that I normally set things up a bit differently. I create one extended partition for Linux, and my root, home, and swap are all under this one extended partition. When installing, I choose to set up my partitions myself. Under the extended partition, I create a 20GB partition and set the mount point to / (100 GB is much larger than anyone should need). Then, I create another partition taking up most of the rest of the space and set the mount point to /home. Finally, I a create a swap partition and set it to be used (as swap, obviously).

I'm not sure if the way you've set up your partitions, with /home under its own extended partition and root and swap as separate logical partitions is the reason for your issue, but this is what works for me. At this point, it looks like you are definitely going to need to completely redo it, though. Be sure to back everything up, of course, especially since you may likely have to format /home.

EDIT: I see now that you want to put /home on a completely separate drive, so my advice may not be so helpful. I've never set up a computer with so many huge hard drives, lol. I would suggest looking at the disk usage analyzer to see what's taking up all the space. If you did somehow duplicate your /home on the partition that is only supposed to be root, that will be apparent with this tool.

---

### Post by montag dp on 2016-03-11
Just one more thing, from what you've posted, I'm not entirely sure that there actually is an extra /home on your /dev/sda1 device, because your du -sh output says /home is 109 GB, but /dev/sda1 is only 92 GB according to df -h. I think du -sh output doesn't distinguish different hard drives or partitions. Someone can correct me if I'm wrong on that point.

---

### Post by steeldriver on 2016-03-11
I suspect you have some massive logs in /var (86G)

For reference, on my (dirty, old) system /var is only 1.3G

---

### Post by Fsirett on 2016-03-11
Actually, it looks to me as if, although I had set up a partition at the start (300Gb) following the swap to act as a /home temporarily and I would transfer the actual pointer to the permanent one after. It is a legacy file, so I can change the OS without having to bother the /home. I prefer a clean install when I upgrade these days.

In any case, what I did was this. I set up the dev/sda drive with three partitions. The first two being for the operating system and the swap and then a third that was called /home. I then pointed to the /sdc1 as /home and, when that worked, I erased the original /home folder. I know that is not the usual way, but it is what I remembered working. It came as a complete surprise to me to find it had a /home folder in the root directory! I am assuming this is the reason that the root file is swelling, or at least part of the reason, and it looks to me as if the two /home files are both active and being used at the same time!

My present thinking, if what I am doing can be called that, is to reinstall with the /home folder on the /sda drive, rename the /home to something else and then point to my /home on /sdc again. 

However, I am not certain that this is the only problem I face, nor am I completely certain this is a good idea. It looks like something that should work to me, but it is also my system that is screwed up and I just happen to be the only one I can blame for screwing it up! I tried blaming my wife, but, as you can probably imagine, that ploy only worked so far. She has her own computer and when she pointed out - very pointedly - that she has never touched my computer and never would along with innumerable threats and accusations that I thought were completely inconsistent with my quite reasonable logic that it had to be her fault made me blame the cat...the fact that we have no cat is immaterial.

In any case, I have come to what is generally accepted to be a wise decision that I should ask before I have another bash, since it would appear the operative result very much involves an impression of "bashing".

Cheers
F S

---

### Post by montag dp on 2016-03-11
> **steeldriver said:**
> I suspect you have some massive logs in /var (86G)

For reference, on my (dirty, old) system /var is only 1.3G
Ah, yes, that's probably it. I didn't notice that /var entry (it's hard to scroll through it on my phone). Good catch.

Frank, when your sdc drive is mounted, it mounts somewhere under /, and it will naturally show up when you run the du command. Since you set up a partition as sdc1 which has the mount point /home, it will also appear when running the du command on /*, like you saw. That doesn't mean that /home is actually taking up space on your root hard drive partition (sda1), though.

---

### Post by Fsirett on 2016-03-11
Referring first to the fact that the /home does not reflect the size in keeping, Now that you mention it, that really does not make much sense to me either and I should have noticed that. When it comes to jumping to conclusions, I can win medals; jumping to contusions as well.

As to the massive logs, I noticed that after my last post, but have no idea how that came about or how to get it under control. I must have done it, but I have no idea how or why. 

Cheers for your observations, I am not certainwhat I can do about them, but you are dragging me (kicking and screaming) down the road to understanding the problems.

F S

---

### Post by Fsirett on 2016-03-11
Thank you very much for the explanation [COLOR=#000000]montag dp, Although it made sense to me in Steeldriver's post, an explanation of the why is something I do appreciate. I may not know much, so there is plenty of room for me to add more. I should have worked that out, but my brain needs jumper cables these days (years?)

[/COLOR]

---

### Post by steeldriver on 2016-03-11
You could try something like

```

sudo find /var -size +100M -exec du -hs {} \; | sort -hr | head

```

to try to identify any unusually large files

---

### Post by montag dp on 2016-03-11
It's also safe to just delete all the logs, if that's what is taking up space.  For example, if you run this:

```
du -h /var/log
```

and see that the directory "journal" has some ungodly large size (say, 86G), simply do this:

```
sudo rm -rf /var/log/journal/*
```

(Don't actually delete the journal directory, just the directories and files underneath.)

EDIT: Actually, I'm not on Ubuntu ... your logs might just be under /var/log, not /var/log/journal.  You'll have to check that.

---

### Post by Fsirett on 2016-03-11
First I ran the```
 find /var -size +100M -exec du -hs {} \; | sort -hr | head
``` command and I saw this. I am a little surprised that there was only the one file listed. Am I correct in thinking that /cups is a printer log?

```
frank@frank:~$ sudo find /var -size +100M -exec du -hs {} \; | sort -hr | head[sudo] password for frank: 
85G	/var/log/cups/error_log
frank@frank:~$ 
```

Now I am running "du -h /var/log"

The report gave me this:

```
frank@frank:~$ du -h /var/log
12K	/var/log/fsck
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdb
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sda6
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdh1
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdh
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sde1
16K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sda1
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sda
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdd2
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sda7
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdc3
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdc1
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdg1
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdc2
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdd
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdg
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdd1
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sde
1,1M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdc
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdb1
4,0K	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57/sdc4
7,4M	/var/log/boot-sav/log/2016-03-11__09h57boot-repair57
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdb
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sda6
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdh1
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdh
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sde1
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sda1
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sda
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdd2
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sda7
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdc3
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdc1
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdg1
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdc2
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdd
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdg
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdd1
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sde
1,1M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdc
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdb1
4,0K	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03/sdc4
7,3M	/var/log/boot-sav/log/2016-03-11__09h41boot-repair03
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdb
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sda6
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdh1
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdh
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sde1
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sda1
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sda
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdd2
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sda7
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdc3
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdc1
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdg1
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdc2
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdd
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdg
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdd1
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sde
1,1M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdc
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdb1
4,0K	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21/sdc4
7,3M	/var/log/boot-sav/log/2016-03-11__09h46boot-repair21
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdb
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sda6
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdh1
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdh
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sde1
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sda1
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sda
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdd2
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sda7
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdc3
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdc1
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdg1
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdc2
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdd
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdg
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdd1
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sde
1,1M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdc
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdb1
4,0K	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45/sdc4
7,3M	/var/log/boot-sav/log/2016-03-11__09h47boot-repair45
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdb
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sda6
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdh1
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdh
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sde1
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sda1
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sda
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdd2
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sda7
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdc3
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdc1
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdg1
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdc2
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdd
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdg
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdd1
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sde
1,1M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdc
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdb1
4,0K	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34/sdc4
7,3M	/var/log/boot-sav/log/2016-03-11__09h49boot-repair34
37M	/var/log/boot-sav/log
4,0K	/var/log/boot-sav/mbr_backups
37M	/var/log/boot-sav
du: cannot read directory &#8216;/var/log/speech-dispatcher&#8217;: Permission denied
4,0K	/var/log/speech-dispatcher
384K	/var/log/apt
4,0K	/var/log/samba
4,0K	/var/log/hp/tmp
8,0K	/var/log/hp
4,0K	/var/log/upstart
85G	/var/log/cups
1,8M	/var/log/installer
44K	/var/log/lightdm
12K	/var/log/dist-upgrade
4,0K	/var/log/unattended-upgrades
85G	/var/log
frank@frank:~$ 
```

I am assuming the "speech-dispatcher" is some sort of voice recognition or artificial voice reproduction. I do not need it whatever. Never used it and will probably never use it so I hope I am able to ignore it. I also notice the boot-repair list is rather long! I might have had a go at repairing things myself, but it could have been my wife, or the cat.

Now I am going to run "sudo rm -rf /var/log/journal/*" and hoping nothing really bad is going to happen. I am going with the suggested version as it is now two AM here and I might need some sleep.

On second thought, the above list shows /var/log/ so I will omit the /journal from the command

Having done that I ran "du -h /var/log" again and this is what I have now:

```
frank@frank:~$ du -h /var/log
4,0K	/var/log
frank@frank:~$ 
``` 

I am now running "sudo du -hs /*" again to see what has happened and to see if there are any other problems in need of attention here:

```
frank@frank:~$ sudo du -hs /*
13M	/bin
91M	/boot
4,0K	/cdrom
880K	/dev
17M	/etc
109G	/home
0	/initrd.img
0	/initrd.img.old
581M	/lib
3,7M	/lib32
4,0K	/lib64
16K	/lost+found
558G	/media
4,0K	/mnt
178M	/opt
du: cannot access &#8216;/proc/1569/fd/16&#8217;: No such file or directory
du: cannot access &#8216;/proc/21136/task/21136/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/21136/task/21136/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/21136/fd/4&#8217;: No such file or directory
du: cannot access &#8216;/proc/21136/fdinfo/4&#8217;: No such file or directory
0	/proc
6,6M	/root
du: cannot access &#8216;/run/user/1000/gvfs&#8217;: Permission denied
9,6M	/run
13M	/sbin
4,0K	/srv
0	/sys
596K	/tmp
4,9G	/usr
891M	/var
0	/vmlinuz
0	/vmlinuz.old
frank@frank:~$ 
```

That seems to have tamed the storm! I will await for the all clear before I mark this as solved.

I have to say, those commands to remove the excess were amazing! I am keeping them close to hand so that I can use them at some future time. Now I have whole new ways to destroy my system! A little knowledge might be a dangerous thing, but a modicum of knowledge and some powerful tools...? I am going to go forth and speak to all my friends with Ubuntu and pretend I know what I am doing now. Cry "havoc"...

Cheers! As I say, I await any posts telling me I have further problems before I mark it as solved. Besides, it is now about two thirty and I can probably use a little sleep

Cheers again!
F S

---

### Post by steeldriver on 2016-03-11
IMHO you would have been better advised to at least take a look in the cups error_log before deleting - the whole point of logging errors is so you can investigate and fix them

---

### Post by montag dp on 2016-03-11
Probably right, although 85 GB is kind of a lot to look through. :) But he should definitely monitor it in the future to find out what's wrong if it starts to happen again.

---

### Post by Fsirett on 2016-03-12
Cheers for the advice. I shall certainly be using the commands to be looking at what is going on in the future.

In fact I have been looking at [https://help.ubuntu.com/lts/serverguide/cups.html](https://help.ubuntu.com/lts/serverguide/cups.html) this morning and I am going to be keeping a close eye on my root files and especially on the logs. It looked to me as if there were quite a few .cups entries and I am now trying to equip myself to monitor that as well. 

On further reading, I see ([http://www.cups.org/](http://www.cups.org/)) that there appears to have been a number of updates to the .cups recently, although that appears to Apple only, but it is interesting to know. 

Thinking about it, I was having some trouble with one .ppa in particular before the problem. I had manually installed Gimp and the .ppa was not being recognised. I was about to remove Gimp completely and reinstall from the Software Centre. That might have been at least a part of the culprit. 

As long as I am here, I will now remove the .ppa I put in, uninstall Gimp and reinstall from the Software Centre and see if my uodate manager works without a hitch.

Nothing like leaping first, I just removed the Gimp .ppa and I now see the Launchpad .ppa is not loading. That might have been a source (again) of the problem. I have changed the server and I am now retrying.

Interesting it is still not loading the Launchpad .ppa. Let me look at the files to see if there is any swelling in my root file.

 That comes out to a "no" that I can see so I guess this problem is solved for the moment and I can now go on and see what is wrong with my upgrades. Never one for one problem. 

Cheers

Frank Sirett

As a P.S. and as a help to any who follow here after, the .ppa that was causing problems resolved to being one that does not yet exist. I saw "launchpad" in the name and assumed it was something that was vital. removed and no problem there either. Maybe this can help others who travel my road.

---

### Post by Fsirett on 2016-03-12
Sorry, it only took a few hours for the problem to reoccur and in the self same place!

First my "du -hs /*" results.

```
frank@frank:~$ sudo du -hs /*[sudo] password for frank: 
13M	/bin
91M	/boot
4,0K	/cdrom
532K	/dev
17M	/etc
156G	/home
0	/initrd.img
0	/initrd.img.old
581M	/lib
3,7M	/lib32
4,0K	/lib64
16K	/lost+found
504G	/media
4,0K	/mnt
178M	/opt
du: cannot access ‘/proc/683/task/683/fdinfo/16’: No such file or directory
du: cannot access ‘/proc/683/fd/18’: No such file or directory
du: cannot access ‘/proc/13291/task/13291/fd/4’: No such file or directory
du: cannot access ‘/proc/13291/task/13291/fdinfo/4’: No such file or directory
du: cannot access ‘/proc/13291/fd/4’: No such file or directory
du: cannot access ‘/proc/13291/fdinfo/4’: No such file or directory
0	/proc
6,5M	/root
du: cannot access ‘/run/user/1000/gvfs’: Permission denied
9,6M	/run
13M	/sbin
4,0K	/srv
0	/sys
283M	/tmp
5,0G	/usr
86G	/var
0	/vmlinuz
0	/vmlinuz.old
frank@frank:~$ 
```

I do worry about  all that /var being filled again. I wonder if it is the same as before?

Looking with the "find /var -size +100M -exec du -hs {} \; | sort -hr | head" command we find:

```
frank@frank:~$ sudo find /var -size +100M -exec du -hs {} \; | sort -hr | head
[sudo] password for frank: 
85G	/var/log/cups/error_log
frank@frank:~$ 
```

Yes, it is exactly the same problem as before. 

I would open it up and look, but it refuses to honour the "gksu nautilus" command because I am short of room in the root.

I am afraid I need more help at getting to the bottom of this one. I am not quite up on just how to look at and interpret the logs at this point.

HELP!

---

### Post by howefield on 2016-03-12
Does the command..

```
tail -n 45 -F /var/log/cups/error_log
```

give you anything ?

You'll need to Ctrl + c out of it.

---

### Post by Fsirett on 2016-03-12
Cheers! I put it in and, although it is not finished yet, it is giving me things that I find of concern:

```
frank@frank:~$ sudo tail -n 45 -F /var/log/cups/error_log[sudo] password for frank: 
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went away, retrying!
E [12/Mar/2016:13:00:50 +0100] File "/usr/lib/cups/notifier/dbus" has insecure permissions (0100775/uid=0/gid=0).
W [12/Mar/2016:13:00:50 +0100] Notifier for subscription 11 (dbus://) went a
```

I have no idea how to fix it, but that looks like a loop to me. I suspect it means I have to change permissions to something or other and that may solve the problem. 

However, I have no idea what to do now.

Cheers again!

F. S.

---

### Post by howefield on 2016-03-12
> **Fsirett said:**
> Cheers! I put it in and, although it is not finished yet, it is giving me things that I find of concern:

It won't "finish" as such, the command will keep showing what is being appended to the file until you "Ctrl + c" out of it, which you can now do and investigate the output. As alluded to earlier in the thread you have to fix it.

---

### Post by Fsirett on 2016-03-12
I understood that, but my fingers are sometimes faster than my brain. 

Am I correct in thinking this is some sort of a loop?

off the topic, what is this I hear about a remake of Steptoe and Son? I was not able to see the originals at the time, but I have found a few of them and I am rather impressed. Only Britain can make intelligent comedies. Maybe not only Britain, but only the British produce them with any success.

F. S.

---

### Post by plucky on 2016-03-12
I did a search for "Notifier for subscription 11 (dbus://) went away, retrying!"

and found this [http://askubuntu.com/questions/648807/cupsd-using-100-cpu-creating-large-80gb-error-log](http://askubuntu.com/questions/648807/cupsd-using-100-cpu-creating-large-80gb-error-log)

See if that works for you

Good Luck

---

### Post by Fsirett on 2016-03-12
Cheers! checking the site now!

---

### Post by Fsirett on 2016-03-12
I have just changed the permissions as suggested here:

> sudo chown root:root /usr/lib/cups/notifier/dbus
might help, now that you have the permissions right. Who is user 1 on your system? If you don't know how the permissions/ownership of the file were changed from the default, the problem might be the tip of an iceberg. If so, reinstalling would be advisable

But from the rest of the post I am also trying this:
> For Ubuntu 15.10 what worked for me was:[INDENT]sudo service cups stop
sudo rm /etc/cups/subscriptions.conf*
sudo rm -r /var/cache/cups
sudo service cups start
[/INDENT](If you cannot stop cups try):
[INDENT]ps aux | grep cups
[/INDENT]Get process id (pid) from output and:
[INDENT]kill -9 (pid you have learned here)
[/INDENT]
The problem looks as if it is the same as mine, and the commands t remove the cache looks familiar, but ending the subscription looks like it might do something. 

I have now restarted the "sudo tail -n 45 -F /var/log/cups/error_log" command and there seems to be no new entries...at the moment!maybe it has to tke some time to get under way again?

I have removed the log (sudo rm -rf /var/log/journal/*) and I am now running "sudo tail -n 45 -F /var/log/cups/error_log" so I can see if there are any new entries

I am now getting:

```
frank@frank:~$ "sudo tail -n 45 -F /var/log/cups/error_log"bash: sudo tail -n 45 -F /var/log/cups/error_log: No such file or directory
frank@frank:~$ 
```

I am assuming that is a sign of all clear, but I must await for wiser heads than mine to verify that. Some would say any heads are wiser than mine. 

My concern here is that the file /error_log does not exist. Is that normal or have I just hidden a problem?

---

### Post by howefield on 2016-03-12
> **Fsirett said:**
> ```
frank@frank:~$ "sudo tail -n 45 -F /var/log/cups/error_log"bash: sudo tail -n 45 -F /var/log/cups/error_log: No such file or directory
frank@frank:~$
```

I am assuming that is a sign of all clear, but I must await for wiser heads than mine to verify that. Some would say any heads are wiser than mine.

Looks more like a sign of entering an incorrect command. :)

```
tail -n 45 -F /var/log/cups/error_log
```

I don't think you need sudo to run it, certainly not the quotes.

PS. Please use default font properties.

---

### Post by Fsirett on 2016-03-12
Of course! I am nothing if not unobservant!

I put in the right line and it came up with:

```
frank@frank:~$ tail -n 45 -F /var/log/cups/error_logtail: cannot open &#8216;/var/log/cups/error_log&#8217; for reading: Permission denied
tail: cannot watch parent directory of &#8216;/var/log/cups/error_log&#8217;: Permission denied
tail: inotify cannot be used, reverting to polling
```

Thus far. Not quite as encouraging. It looks like I have done something that is not quite as beneficial as it seemed.

I am not using the default fonts? I have changed nothing there. It looks the same as all the other posts. What have I done?

---

### Post by Fsirett on 2016-03-12
My question is if this permission thing is a problem at the moment and how can I fix it if it is?

---

### Post by steeldriver on 2016-03-12
Can you post the results of the following please

```

id -Gn

sudo ls -ld /var/log/cups/{,error_log}

```
and
```

ls -l /usr/lib/cups/notifier/dbus

```

---

### Post by Fsirett on 2016-03-12
hello Steeldriver. I thought last night this was put to bed for good, but the vampire broke out on me. Never any garlic when you need it!

In any case, first we have the "id -gn:"

```
frank@frank:~$ id -Gnfrank adm cdrom sudo dip plugdev lpadmin sambashare

```

That was short and sweet, but it is almost meaningless to me.

Next you wanted to see "sudo ls -ld /var/log/cups/{,error_log}:"

```
frank@frank:~$ sudo ls -ld /var/log/cups/{,error_log}
[sudo] password for frank: 
drwxr-x--- 2 root lp         4096 mar 12 08:42 /var/log/cups/
-rw-r----- 1 root adm 90934374807 mar 12 14:30 /var/log/cups/error_log
```

Also short and a bit odd. I see what I think is a time stamp for today six and a half hours ago. Piques my curiosity

Last of all is the "ls -l /usr/lib/cups/notifier/dbus:"

```
frank@frank:~$ ls -l /usr/lib/cups/notifier/dbus
-rwxrwxr-x 1 root root 14336 oct  8 22:54 /usr/lib/cups/notifier/dbus
frank@frank:~$ 
```

My first impression is that the first lines that look like they may be permissions look a little funny. If I knew a little more I could provide graphic proof for how dangerous a little knowledge can be!

Cheers again

F. S.

---

### Post by steeldriver on 2016-03-12
Probably you can't execute 'tail -F' on the cups error_log without sudo because the parent directory's group is 'lp' (which your user is not a member of) and 'others' don't have execute permission. I would not worry about that at this stage.

For reference, on my 14.04 system they are
```

drwxr-xr-x 2 root root 4096 Mar 12 07:25 /var/log/cups/
-rw-r----- 1 root adm     0 Feb  5 08:19 /var/log/cups/error_log

```

I have skimmed the thread - but can't see what version you are running? Perhaps the 'lp' group ownership is normal for that version.

FWIW I have 
```

$ ls -l /usr/lib/cups/notifier/dbus
-rwxr-xr-x 1 root root 14336 Dec 11 14:06 /usr/lib/cups/notifier/dbus

```

(i.e. octal permissions are 7**5**5) which may relate back to the original error about insecure permissions on yours (7**7**5 i.e. group-writeable) - again, if you indicate what Ubuntu version you are running, someone with that version will likely chime in to confirm.

---

### Post by Fsirett on 2016-03-12
Sorry for the omission, I am using 15.10. 

I am now looking up lp to see what that is. I think I saw a reference to lp in an article.

It is not likely to do anything for my understanding, but I am trying to show willing

---

### Post by Fsirett on 2016-03-12
I have just had a look at the lp group information and it seems that it was near vital when one wants to use a Samsung printer. This is interesting because indeed I have a Samsung printer and, if it makes any difference, it is a colour laser printer! When I first got it a colour laser was considered a problem by most reports, but it worked a treat with every Ubuntu up until now. I am going to have to look up Samsung printers to see if I can find a problem there.

---

### Post by steeldriver on 2016-03-12
I'm confused about the status of your issue - is the log file still growing, or not?

If it is not, then you probably don't need to worry about the precise group ownerships and permissions of the various system files - unless you have messed with them, assume that's what they are meant to be

---

### Post by Fsirett on 2016-03-12
Cheers! If that is the case, then it is case closed! I am fascinated by the process and interested in things working properly, but if I need not worry farther, then I am good. As long as this monster does not raise its head again!

If all of the settings are normal, or acceptable, I am good, Cheers!

F

---

### Post by Fsirett on 2016-03-13
No problems for some twelve hours, will delay closing for another twelve hours just to ensure the problem has gone away. 

Cheers for all your help should this be the swan song for this episode, I shall be closing the thread in twelve hours should the problem remain in remission.

One thing I did do was look at my printer files and noticed there was a colour management add on from Ubuntu so I added that in the hopes that it might curtail any further problems. The log showed this and nothing else afterwards. That makes it an hour without entries! Will wonders never cease!

Frank Sirett

---

### Post by Fsirett on 2016-03-14
More than twenty-four hours with no problems! I am declaring this problem solved.

Many thanks for all of you who helped. Very much appreciated and I am storing the solutions away for future use

Cheers

Frank Sirett

---

