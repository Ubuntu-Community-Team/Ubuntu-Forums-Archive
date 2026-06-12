---
title: "How to raise size of working partition under Kubuntu 18"
date: 2019-09-08
forum: General Help
---

### Post by petrogromovo on 2019-09-08
Hello[COLOR=#000000],[/COLOR][COLOR=#000000]
I installed Kubuntu 18 [/COLOR]about 3 weeks ago on partition in 28G,
but after installing of  docker seems this space is not enough for my root partition

```
$ df -HT   
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  4,2G     0  4,2G   0% /dev
tmpfs          tmpfs     828M  1,7M  827M   1% /run
/dev/sdb5      ext4       28G   27G     0 100% /
tmpfs          tmpfs     4,2G  186M  4,0G   5% /dev/shm
tmpfs          tmpfs     5,3M  4,1k  5,3M   1% /run/lock
tmpfs          tmpfs     4,2G     0  4,2G   0% /sys/fs/cgroup
/dev/sdb7      ext4       30G   15G   13G  54% /mnt/_Prior_Kubuntu_18
/dev/sdb8      fuseblk   399G   88G  311G  23% /mnt/_work_sdb8
/dev/sdb1      ext4      347M   91M  235M  28% /boot
/dev/sda6      fuseblk   237G  136G  101G  58% /mnt/Work_sda6
/dev/sda8      fuseblk   628G  606G   22G  97% /mnt/Media_sda8
tmpfs          tmpfs     828M   21k  828M   1% /run/user/1000

```

My working partition is /dev/sdb5. Also I use /dev/sdb7 for ubuntu installation.
In gparted I see : [https://imgur.com/a/sCNFsAt](https://imgur.com/a/sCNFsAt)

I think to raise size of /dev/sdb5 and /dev/sdb7 till 50G and to get disk from /dev/sdb8 .
Can you advice in which(simple and safe) way and using which tools can I make it ?
Is it better to make it from my current Kubuntu 18 or run it live from my usb installation ?

Thanks!

---

### Post by nathanhawthorne12 on 2019-09-08
If this was done via LVM it would be trivial, but I am unsure how you would do this without LVM, Create a new partition for Docker?

---

### Post by yancek on 2019-09-08
In order to resize/change partitions, they need to be unmounted so you cannot do it from the installed OS.  Use a 'live' CD/USB which should have a partition manager on it.  Most of the Ubuntu based systems have GParted but I'm not sure that is the case with Kubuntu but it should have some partition manager.

Problems I see, it is necessary to have partitions adjacent to each other before you can make these changes and we don't have that information.  Run sudo fdisk -l (lower case Letter L) and post the output here.

Additionally, the partition (sdb8) you want to use to expand your Linux partition to is a windows ntfs filesystem so you will have to re-format that to ext4.  This will result in loss of data so you need to back up and data on sdb8 before doing anything.

---

### Post by petrogromovo on 2019-09-08
my 2 disks hdd(sda) and ssd(sdb) :
```
$ sudo fdisk -l
Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x311221b2

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          3199  126820351  126817153  60,5G  7 HPFS/NTFS/exFAT
/dev/sda2        126822398 1891549183 1764726786 841,5G  f W95 Ext'd (LBA)
/dev/sda3       1903833088 1953523711   49690624  23,7G 83 Linux
/dev/sda4       1891549184 1903833087   12283904   5,9G 83 Linux
/dev/sda5        127952896  127995903      43008    21M 83 Linux
/dev/sda6        127997952  589574143  461576192 220,1G  7 HPFS/NTFS/exFAT
/dev/sda7        589576192  630534143   40957952  19,5G 83 Linux
/dev/sda8        630536192 1856688127 1226151936 584,7G  7 HPFS/NTFS/exFAT
/dev/sda9       1856690176 1891549183   34859008  16,6G  7 HPFS/NTFS/exFAT

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0003d842

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sdb1  *         2048     718847    716800   350M 83 Linux
/dev/sdb2          718848  104859647 104140800  49,7G  7 HPFS/NTFS/exFAT
/dev/sdb3       104872381 1000206899 895334519   427G  f W95 Ext'd (LBA)
/dev/sdb5       104872383  159412994  54540612    26G 83 Linux
/dev/sdb6       159413058  163622024   4208967     2G 82 Linux swap / Solaris                                                                                                       
/dev/sdb7       163622088  222355664  58733577    28G 83 Linux                                                                                                                      
/dev/sdb8       222355731 1000206899 777851169 370,9G  7 HPFS/NTFS/exFAT        

```
Is it possible to cut pieces of space from /dev/sdb8 and move them to unallocated area before /dev/sdb8 and next this unallocated area(or half of it) add to /dev/sdb7?
It seems to me that similar way I used priorly, but I can not for sure in which OS(Windows or ubuntu) and with which app I used...

> **nathanhawthorne12 said:**
> If this was done via LVM it would be trivial, but I am unsure how you would do this without LVM, Create a new partition for Docker?
I provided info for my disks, buit how to create a[COLOR=#000000] new partition for Docker ?[/COLOR]

---

### Post by Dennis N on 2019-09-08
Well, your home folder usage is counted in sdb5, so move some files from there to the other 'work' partitions. Then you free that space for installing another application in /, and/or space for Docker to use in there.

---

### Post by oldfred on 2019-09-08
If a newer user, often better to have a separate /home partition as mount, ownership & permissions is automatically taken care of when installing.  You could move /home to a new partition.

But since you have other Linux partitions, you may want to consider just another data partition for most of the data in /home. I use 25 to 30GB for / but have many / partitions on system. The others are test or experiments as I do not want to change my main working 18.04LTS install. So I mount a data partition and link folders back into home so I have all the standard folders, but the are in another partition.

       [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by TheFu on 2019-09-08
I would quickly solve the issue by using a symbolic link from the partition without enough room to a partition that has plenty of space. Move all the docker files/images to the other partition.  This is a hack, but takes just a few minutes. As long as the symbolic link makes the path seem exactly the same as before, it will work.

Then you can waste time screwing around with partitioning and adding more storage, if that is your choice.  You can mount additional storage to /var/ or to /var/lib/docker/ ... if you like.

Like nathanhawthorne12 , I'd use LVM and this sort of issue would be trivial, but normally, LVM needs to be setup during the install to be the most useful.  I use separate LVs for each virtual machine or Linux Container. The storage LV for each separate VM is presented as raw, block, storage.  This makes storage extremely flexible, easy to modify sizes as needed. Easy to clone.  The main trick is NEVER allocate all the available storage until it is needed.  Then allocate a sufficient amount only where needed.

But your first task is to clean up / so there is some working storage available.  Until that happens, the physical machine is at great risk for crashing due to out of space problems.
Here's my partition table:
```
Device     Boot   Start        End   Sectors   Size Id Type
/dev/sdb1  *       2048    1499135   1497088   731M 83 Linux
/dev/sdb2       1501182 1000214527 998713346 476.2G  5 Extended
/dev/sdb5       1501184 1000214527 998713344 **476.2G** 8e **Linux LVM**
```
All the LVM stuff is inside sdb5.  The LVs inside there are:
```
$ sudo lvs
  LV                VG       Attr       LSize   
  libvirt-lv        hadar-vg -wi-ao---- 200.00g
  lv-blog44-1604    hadar-vg -wi-ao----  16.20g
  lv-lubuntu11-1604 hadar-vg -wi-ao----  31.00g
  lv-spam61-1604    hadar-vg -wi-ao----   7.00g
  lv-vpn09-1604     hadar-vg -wi-ao----   7.50g
  lv-xen41-1604     hadar-vg -wi-ao----  12.50g
  lv-zcs45-1604     hadar-vg -wi-ao----  25.00g
  root              hadar-vg -wi-ao----  22.33g
  swap_1            hadar-vg -wi-ao---- 976.00m
  test-1804         hadar-vg -wi-a-----  10.00g

$ sudo vgs
  VG       #PV #LV #SN Attr   VSize   VFree  
  hadar-vg   1  10   0 wz--n- 476.22g **143.74g**

```
I have 140G available to be used still, when needed. Also, libvirt-lv was allocated with 200G, but is only using 2G:
```
/dev/mapper/hadar--vg-libvirt--lv ext4      197G  1.8G  186G   1% /var/lib/libvirt
``` I did that before I decided to make each VM use an LV.  That 200G is effectively available.  LVM supports shrinking LVs too, but it has to be done on an unmounted LV.  That can be inconvenient.

Again, usually, setting up LVM happens during the OS installation, but you can do it on any empty disk you like. Total data loss will happen to the partition converted to LVM, so backup anything you don't want to lose.

To see the available commands, install LVM2 and then use tab-completion to see the commands that begin with pv, vg, and lv.  One of the primary reasons to use LVM is for the ability to take snapshots of running systems which can be used to backup onto other media. This is enterprise storage and works exactly the same as Veritas or any of the commercial storage volume managers.

---

### Post by petrogromovo on 2019-09-09
Thank you for your help!
I checked and see that my Home directory is 1.8 GiB, so moving of Home seems not a decision.
/var/lib/docker/  takes 11.1 GiB.

1)So the best decision seems to reinstall my OS and during installation to select additive partition as LVM partition.
Actually during prior installations of Kubuntu I did not pay attention where LVM is selected ? Please, any hints.

2) To free disk space on current OS I run
> sudo apt-get remove docker-ce
but I have only 200 MiB free.
Is it safe to remove /var/lib/docker/ manually under root or there is a better way?

---

### Post by petrogromovo on 2019-09-09
I opened Kubuntu install wizard and without reinstalling my OS I checked :
1) I need to select "/" and "/boot" partinions with option to format them.
2) Also I need to select 1 more partinion, but which type have I select for it? 
When  select point for additive partinion I see next options  : &#8220;/&#8221;,  &#8220;/boot&#8221;,  &#8220;/home&#8221;,  &#8220;/tmp&#8221;,  &#8220;/usr&#8221;,  &#8220;/var&#8221;,  &#8220;/srv&#8221;,  &#8220;/opt&#8221;,    &#8220;/usr/local&#8221;?
Which of them have I to select (with formatting it) to use for docker?
3) Could you please provide a link how on new installed OS to istall and use  docker to keep all its data on this addtive partition ?

Thanks!

---

### Post by TheFu on 2019-09-09
I don't use docker.  Any docker specific questions need someone else to address.
Formatting wipes all data.  I use linux containers and treat them like zombies, killing/replacing as needed.  They are temporary and only valid for about a week before a new version needs to be created and deployed.  1 application == 1 container.   Attempting to use docker like a full VM is a mistake. It is not a "best-practice" for enterprise container use.  If anything inside the docker container needs to be modified for any reason, shoot it in the head, and build a fresh container.  That should happen once a week or so, as the application gets patched.  Applications with slower patching cycles can last longer in a container.

I've never touched Kubuntu nor seen the KDE installer.  In Ubuntu, there is a checkbox to "Use LVM on the full disk" (or something close to that), which wipes the OS install disk.  On 18.04 Ubuntu Server, there is a more advanced storage setup possible. I've only seen it a few times and don't recall the details.  I install onto a new physical machine about once every 5 yrs, but I install into virtual machines about once every 3 months. 

I don't really understand what "additive partinion" means.  I always do a basic install with ssh-server into 25G of storage and leave all the other storage setup to be handled later.  The other disks get 1 partition with LVM and a different VG for each.  Then I make LVs, sized as needed.  LVs can be thought of as easy-to-resize partitions.

If you don't want to reinstall the OS, you don't have to, but the base install into that huge partition seems like a waste.

Using LVM is best handled at the partition level.  I would strongly recommend AGAINST using LVM to merge storage from different physical devices into a single LV. Yes, you can do it, but unless you have 100% perfect, backups that are tested to be restored, then that shouldn't be attempted.  I limit my LV sizes to what my backups can easily support. If I can't back it up, then that storage won't be used.

There are a few LVM tutorials available. Howtoforge has one.  LVM is 100% CLI. Any GUI tool cannot be trusted.  Using virtual machines, work through the tutorial so you have hands-on experience BEFORE doing anything LVM on your important systems.  The LVM tools haven't changed much in 15 yrs, so don't worry about the age of any tutorial or guide.  The only things that have changed is today, we have more convenient LVM information display tools - lvs, vgs, pvs.  Those show the data most often needed.  Once in a while, the older tools lvdisplay, vgdisplay and pvdisplay can be helpful if more details are needed, which does happen from time to time, but not all that often.

---

### Post by petrogromovo on 2019-09-12
I opened Kubuntu installation wizard one more time and did not find any "Use LVM on the full disk"  option...

I think about different decision
As that is rather risky to resize partitions with live data and I have 2 partitions 28 and 25 GiB
Biggest for &#8220;/&#8221; and in 25 GiB partition I want to install &#8220;/var&#8221;
Both are on the same ssd disk.


In Kubuntu installation wizard, when select point for additive partinion I see next 
options : &#8220;/&#8221;, &#8220;/boot&#8221;, &#8220;/home&#8221;, &#8220;/tmp&#8221;, &#8220;/usr&#8221;, &#8220;/var&#8221;, &#8220;/srv&#8221;, &#8220;/opt&#8221;, &#8220;/usr/local&#8221;?


I selected &#8220;/var&#8221; as I tried to install docker and I found that /var/lib/docker/ takes 11.1 GiB.
I think that installing &#8220;/var&#8221; into 25 GiB partition I will not have problems with lack of space.
Installig linux I have never installed some one of options :  &#8220;/home&#8221;, &#8220;/usr&#8221;, &#8220;/var&#8221; into separate partion.
Just want to confirm, no any risk ? If there is what I have to pay attention at installing/working in OS?

---

### Post by SeijiSensei on 2019-09-12
Stop docker, then copy /var/lib/docker to /mnt/_work_sdb8, which has a lot of unused space. Then create a symbolic link to /mnt/_work_sdb8/docker in /var/lib.

```

cd /var/lib
sudo rsync -av docker /mnt/_work_sdb8
sudo mv docker docker.old
sudo ln -s /mnt/_work_sdb8/docker

```

Now restart docker. Does it work as before?  If so, delete /var/lib/docker.old.

Symbolic links are the easiest method to solve storage problems if you have spare space available.

**Update**: Looks like /mnt/_work_sdb8 is not an ext4 filesystem since it uses fuseblk.  (NTFS I'd guess? Why?) You'll probably need to use /mnt/_Prior_Kubuntu18 instead.  Or reformat some other filesystem like _work_sdb8 to ext4.

---

### Post by petrogromovo on 2019-09-14
Yes, I use sdb7 partition for docker. So after I formatted /sdb7 into  and used /sdb7 in /etc/fstab and restarted OS I run:

```
cd /var/lib
sudo rsync -av docker /mnt/_work_sdb7
sudo mv docker docker.old
sudo ln -s /mnt/_work_sdb7/docker

```
and next :
```
$ docker-compose up -d --build
ERROR: Couldn't connect to Docker daemon at http+docker://localunixsocket - is it running?

```
If it's at a non-standard location, specify the URL with the DOCKER_HOST environment variable.

I found a way of fixing :
```
[COLOR=#000000]sudo  usermod -aG docker $USER[/COLOR]
sudo  newgrp - docker

```

But it did not help. Next :

```
#  sudo systemctl start docker                                           
Job for docker.service failed because the control process exited with error code.
See "systemctl status docker.service" and "journalctl -xe" for details.
# systemctl status docker.service
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sat 2019-09-14 10:52:00 EEST; 3s ago
     Docs: [https://docs.docker.com](https://docs.docker.com)
  Process: 25319 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 25319 (code=exited, status=1/FAILURE)

Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Service hold-off time over, scheduling restart.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Scheduled restart job, restart counter is at 3.
Sep 14 10:52:00 serge-at-hoe systemd[1]: Stopped Docker Application Container Engine.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Start request repeated too quickly.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Failed with result 'exit-code'.
Sep 14 10:52:00 serge-at-hoe systemd[1]: Failed to start Docker Application Container Engine.
# journalctl -xe
-- Unit docker.service has failed.
-- 
-- The result is RESULT.
Sep 14 10:51:58 serge-at-hoe kernel: [UFW BLOCK] IN=enp4s0 OUT= MAC=44:8a:5b:ee:2a:dd:c8:e7:f0:6e:fc:29:08:00 SRC=185.222.211.54 DST=213.109.234.130 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=65064 PROTO=TCP SPT=41109 DPT=23535 WINDOW=1024 RES
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Service hold-off time over, scheduling restart.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Scheduled restart job, restart counter is at 3.
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
--                                                                                                                                                                                                                                           
-- Automatic restarting of the unit docker.service has been scheduled, as the result for                                                                                                                                                     
-- the configured Restart= setting for the unit.                                                                                                                                                                                             
Sep 14 10:52:00 serge-at-hoe systemd[1]: Stopped Docker Application Container Engine.                                                                                                                                                        
-- Subject: Unit docker.service has finished shutting down                                                                                                                                                                                   
-- Defined-By: systemd                                                                                                                                                                                                                       
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)                                                                                                                                                                                                    
--                                                                                                                                                                                                                                           
-- Unit docker.service has finished shutting down.                                                                                                                                                                                           
Sep 14 10:52:00 serge-at-hoe systemd[1]: Closed Docker Socket for the API.                                                                                                                                                                   
-- Subject: Unit docker.socket has finished shutting down                                                                                                                                                                                    
-- Defined-By: systemd                                                                                                                                                                                                                       
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)                                                                                                                                                                                                    
--                                                                                                                                                                                                                                           
-- Unit docker.socket has finished shutting down.                                                                                                                                                                                            
Sep 14 10:52:00 serge-at-hoe systemd[1]: Stopping Docker Socket for the API.                                                                                                                                                                 
-- Subject: Unit docker.socket has begun shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has begun shutting down.
Sep 14 10:52:00 serge-at-hoe systemd[1]: Starting Docker Socket for the API.
-- Subject: Unit docker.socket has begun start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has begun starting up.
Sep 14 10:52:00 serge-at-hoe systemd[1]: Listening on Docker Socket for the API.
-- Subject: Unit docker.socket has finished start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has finished starting up.
-- 
-- The start-up result is RESULT.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Start request repeated too quickly.
Sep 14 10:52:00 serge-at-hoe systemd[1]: docker.service: Failed with result 'exit-code'.
Sep 14 10:52:00 serge-at-hoe systemd[1]: Failed to start Docker Application Container Engine.
-- Subject: Unit docker.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.service has failed.


```
Some confugation/permittions missing?

```
# docker-compose --version
docker-compose version 1.17.1, build unknown
# docker --version
Docker version 19.03.2, build 6a30dfc

```

---

### Post by SeijiSensei on 2019-09-16
Oops. I may have given you the steps in the wrong order.  Docker may be in /var/lib/docker.old rather than /var/lib/docker. Check /var/lib and make sure Docker is in /var/lib/docker.  If not move it and try starting it again.

---

### Post by petrogromovo on 2019-09-16
Yes, I see directory [/var/lib/docker.old]("file:///var/lib/docker.old"), not [/var/lib/docker]("file:///var/lib/docker.old") as it must be?
So I have just rename this dir?

In you command you moved docker into docker.old. What for this old version?
And I had to create docker die as we lack it?
So all commands must look like :

> cd /var/lib
sudo rsync -av docker /mnt/_work_sdb7
sudo mv docker docker.old
mkdir docker
sudo ln -s /mnt/_work_sdb7/docker

?

---

### Post by SeijiSensei on 2019-09-16
I should have put the "mv docker" command above rsync.  It was designed to preserve whatever was already there.  rsync would have created the docker directory on its own when transferring the files.  So yes, try
```

sudo rm -rf docker
sudo mv docker.old docker

```
then restart Docker. The first command removes any directory you might have created so that the second command can rename the docker.old directory to docker.

Sorry for the confusion.  I do reread my postings before submitting, but I guess I just missed this error.

---

### Post by petrogromovo on 2019-09-18
Thank you for you feedback!
 I tried to follow your commnds and I have next problems as I got  "Start request repeated too quickly" errors running docker:
 I have  in /etc/fstab :


 ```
/dev/sdb7 /mnt/_work_sdb7 
``` 




In /etc/docker/daemon.json I have :
```
{
  "data-root": "/mnt/_work_sdb7/docker" ,
  "storage-driver": "overlay2"
}

```
 as I found in this link 
 [https://docs.docker.com/config/daemon/systemd/#custom-docker-daemon-options](https://docs.docker.com/config/daemon/systemd/#custom-docker-daemon-options)
 
 
 Opening /mnt/_work_sdb7 I see content :
 
 ```
/mnt/_work_sdb7# la -ls
total 64
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 builder
 4 drwx--x--x 4 root root  4096 &#1074;&#1077;&#1088; 14 14:56 buildkit
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 containers
 0 lrwxrwxrwx 1 root root    22 &#1074;&#1077;&#1088; 13 18:56 docker -> /mnt/_work_sdb7/docker
 4 drwx------ 3 root root  4096 &#1074;&#1077;&#1088; 14 14:56 image
16 drwx------ 2 root root 16384 &#1074;&#1077;&#1088; 13 18:33 lost+found
 4 drwxr-x--- 3 root root  4096 &#1074;&#1077;&#1088; 14 14:56 network
 4 drwx------ 3 root root  4096 &#1074;&#1077;&#1088; 14 14:56 overlay2
 4 drwx------ 4 root root  4096 &#1074;&#1077;&#1088; 14 14:56 plugins
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 runtimes
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 swarm
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 tmp
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 trust
 4 drwx------ 2 root root  4096 &#1074;&#1077;&#1088; 14 14:56 volumes


```




I tried next :
```
root@serge-at-hoe:/mnt/_work_sdb7# sudo systemctl start docker
Job for docker.service failed because the control process exited with error code.
See "systemctl status docker.service" and "journalctl -xe" for details.
root@serge-at-hoe:/mnt/_work_sdb7# sudo systemctl enable docker
Synchronizing state of docker.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable docker
root@serge-at-hoe:/mnt/_work_sdb7# systemctl status docker.service
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Wed 2019-09-18 18:56:54 EEST; 1s ago
     Docs: [https://docs.docker.com](https://docs.docker.com)
  Process: 29166 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 29166 (code=exited, status=1/FAILURE)
root@serge-at-hoe:/mnt/_work_sdb7# journalctl -xe
-- 
-- The result is RESULT.
&#1074;&#1077;&#1088; 18 18:56:55 serge-at-hoe systemd-resolved[880]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
&#1074;&#1077;&#1088; 18 18:56:55 serge-at-hoe systemd-resolved[880]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: docker.service: Service hold-off time over, scheduling restart.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: docker.service: Scheduled restart job, restart counter is at 6.
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Automatic restarting of the unit docker.service has been scheduled, as the result for
-- the configured Restart= setting for the unit.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Stopped Docker Application Container Engine.
-- Subject: Unit docker.service has finished shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.service has finished shutting down.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Closed Docker Socket for the API.
-- Subject: Unit docker.socket has finished shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has finished shutting down.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Stopping Docker Socket for the API.
-- Subject: Unit docker.socket has begun shutting down
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has begun shutting down.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Starting Docker Socket for the API.
-- Subject: Unit docker.socket has begun start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has begun starting up.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Listening on Docker Socket for the API.
-- Subject: Unit docker.socket has finished start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.socket has finished starting up.
-- 
-- The start-up result is RESULT.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: docker.service: Start request repeated too quickly.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: docker.service: Failed with result 'exit-code'.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: Failed to start Docker Application Container Engine.
-- Subject: Unit docker.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit docker.service has failed.
-- 
-- The result is RESULT.
&#1074;&#1077;&#1088; 18 18:56:56 serge-at-hoe systemd[1]: docker.socket: Failed with result 'service-start-limit-hit'.


```






I tried to use this [https://serverfault.com/questions/845471/service-start-request-repeated-too-quickly-refusing-to-start-limit](https://serverfault.com/questions/845471/service-start-request-repeated-too-quickly-refusing-to-start-limit)  link 
and edited file  /etc/systemd/system.conf in which all parameters were commented I uncommented or added parameters with some values, incrementing them and restarting OS. I made so several times and at least I have :
```
DefaultStartLimitIntervalSec=350s
DefaultStartLimitBurst=260
StartLimitInterval=350s
StartLimitBurst=260
StartLimitIntervalSec=260

```

while all the rest parameters commented, But any way I see errors :


```
&#1074;&#1077;&#1088; 14 18:05:44 serge-at-hoe systemd[1]: docker.service: Start request repeated too quickly.
&#1074;&#1077;&#1088; 14 18:05:44 serge-at-hoe systemd[1]: docker.service: Failed with result 'exit-code'.
&#1074;&#1077;&#1088; 14 18:05:44 serge-at-hoe systemd[1]: Failed to start Docker Application Containe

```


I tried in /etc/systemd/system.conf to change some values to zero, as I googled such possible decision:
```
DefaultStartLimitIntervalSec=0
DefaultStartLimitBurst=260
StartLimitInterval=350
StartLimitBurst=260
StartLimitIntervalSec=0

```But restarting OS I failed to login into the system and has a lot of flash messages on the screen. I modified the file with all 0 :
```
DefaultStartLimitIntervalSec=0
DefaultStartLimitBurst=0
StartLimitInterval=0
StartLimitBurst=0
StartLimitIntervalSec=0

```I reloaded ok but running docker I still have "Start request repeated too quickly" errors:




I have some expierance with docker installing locally priorly without any additive partition and I did not any
"Start request repeated too quickly" errors...


I am really stack . How to fix this error ?

---

### Post by TheFu on 2019-09-18
If it is just docker, blow it all away (delete the files and uninstall the packages) and setup a symbolic link to the new storage so that it "appears" to be under the location in /var/lib/docker (or whatever docker uses), but is actually pointed to a different, mounted, storage area.

Looks like you didn't get the symbolic link setup correctly.  A link from 
*/mnt/_work_sdb7/docker to /mnt/_work_sdb7/docker *isn't correct. That's was it showing above.

I use this sort of fix all the time.  For example:
```
/var/lib$ ls -laF libvirt
total 24
drwxr-xr-x  6 root         root 4096 Sep 15 14:19 ./
drwxr-xr-x 88 root         root 4096 Jul 27 20:05 ../
drwx--x--x  2 root         root 4096 May 23  2018 boot/
drwxr-xr-x  2 root         root 4096 Sep 15 15:04 dnsmasq/
lrwxrwxrwx  1 root         root   13 Mar 19  2019 images -> /stuff/images/
drwxr-x---  7 libvirt-qemu kvm  4096 Aug  3 10:55 qemu/
drwx------  2 root         root 4096 May 23  2018 sanlock/
```
See how "images" points to /stuff/images/ ?  That's a symbolic link for my KVM virtual machines which sit in a different mount location.  Do the same for the /var/lib/docker-whatever.

---

### Post by petrogromovo on 2019-09-19
I removed docker-ce  and  docker-ce-cli

Removed dir :
/var/lib/docker

which dirs had I to remove?

restarted OS

Cherck current links and create new at /mnt/_work_sdb7/docker :
```
serge@serge-at-hoe:/mnt/_work_sdb8/wwwroot/lar/votes$ ls -la / | grep "\->"
lrwxrwxrwx   1 root root    14 &#1089;&#1077;&#1088; 20 21:45 _diskD_Work -> /mnt/Work_sda6
lrwxrwxrwx   1 root root    15 &#1089;&#1077;&#1088; 20 21:46 _diskE_Media -> /mnt/Media_sda8
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:23 initrd.img -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:20 initrd.img.old -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 21:45 _InstallLinux -> /mnt/Work_sda6/Install/__forLinux
lrwxrwxrwx   1 root root    22 &#1089;&#1077;&#1088; 20 20:56 _Prior_Kubuntu_18 -> /mnt/_Prior_Kubuntu_18
lrwxrwxrwx   1 root root    21 &#1089;&#1077;&#1088; 20 21:01 _Video -> /mnt/Media_sda8/VIDEO
lrwxrwxrwx   1 root root    30 &#1089;&#1077;&#1088; 20 20:23 vmlinuz -> boot/vmlinuz-4.15.0-20-generic
lrwxrwxrwx   1 root root    16 &#1089;&#1077;&#1088; 20 20:41 _work -> /mnt/_work_sdb8/
lrwxrwxrwx   1 root root    23 &#1089;&#1077;&#1088; 20 21:45 _wwwroot -> /mnt/_work_sdb8/wwwroot
serge@serge-at-hoe:/mnt/_work_sdb8/wwwroot/lar/votes$ sudo ln -s /mnt/_work_sdb7/docker

```

Install package:
```
serge@serge-at-hoe:/mnt/_work_sdb8/wwwroot/lar/votes$ sudo apt-get install docker-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
docker-ce is already the newest version (5:19.03.2~3-0~ubuntu-bionic).
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up docker-ce (5:19.03.2~3-0~ubuntu-bionic) ...
Job for docker.service failed because the control process exited with error code.
See "systemctl status docker.service" and "journalctl -xe" for details.
invoke-rc.d: initscript docker, action "start" failed.
&#9679; docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Fri 2019-09-20 06:47:16 EEST; 8ms ago
     Docs: [https://docs.docker.com](https://docs.docker.com)
  Process: 18699 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)
 Main PID: 18699 (code=exited, status=1/FAILURE)
dpkg: error processing package docker-ce (--configure):
 installed docker-ce package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 docker-ce
E: Sub-process /usr/bin/dpkg returned an error code (1)
serge@serge-at-hoe:/mnt/_work_sdb8/wwwroot/lar/votes$ ls -la / | grep "\->"
lrwxrwxrwx   1 root root    14 &#1089;&#1077;&#1088; 20 21:45 _diskD_Work -> /mnt/Work_sda6
lrwxrwxrwx   1 root root    15 &#1089;&#1077;&#1088; 20 21:46 _diskE_Media -> /mnt/Media_sda8
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:23 initrd.img -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 20:20 initrd.img.old -> boot/initrd.img-4.15.0-20-generic
lrwxrwxrwx   1 root root    33 &#1089;&#1077;&#1088; 20 21:45 _InstallLinux -> /mnt/Work_sda6/Install/__forLinux
lrwxrwxrwx   1 root root    22 &#1089;&#1077;&#1088; 20 20:56 _Prior_Kubuntu_18 -> /mnt/_Prior_Kubuntu_18
lrwxrwxrwx   1 root root    21 &#1089;&#1077;&#1088; 20 21:01 _Video -> /mnt/Media_sda8/VIDEO
lrwxrwxrwx   1 root root    30 &#1089;&#1077;&#1088; 20 20:23 vmlinuz -> boot/vmlinuz-4.15.0-20-generic
lrwxrwxrwx   1 root root    16 &#1089;&#1077;&#1088; 20 20:41 _work -> /mnt/_work_sdb8/
lrwxrwxrwx   1 root root    23 &#1089;&#1077;&#1088; 20 21:45 _wwwroot -> /mnt/_work_sdb8/wwwroot

```
In the last command I do not see created symbolic link ? Is 
```
sudo ln -s /mnt/_work_sdb7/docker
```

valid format for command ?

---

### Post by TheFu on 2019-09-20
> **petrogromovo said:**
>  <snip> ....
In the last command I do not see created symbolic link ? Is 
```
sudo ln -s /mnt/_work_sdb7/docker
```

valid format for command ?
I cannot tell without knowing the PWD.  The target of that command above defaults to the PWD.

Seems you are missing the key understanding of symbolic links.  Linking /mnt/.... to /mnt/... isn't very helpful.  That just makes a circular link to the same storage.

A safer **ln** command would be 
```
sudo ln -s /mnt/_work_sdb7/docker  /var/lib/docker
```
assuming /var/lib/docker is the correct place.  

Again, I know nothing about docker.

Are you aware that every command on the system has a manual page?  **man ln** 
```
NAME
       ln - make links between files

SYNOPSIS
       ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
       ln [OPTION]... TARGET                  (2nd form)
       ln [OPTION]... TARGET... DIRECTORY     (3rd form)
       ln [OPTION]... -t DIRECTORY TARGET...  (4th form)
...

```
the manpage goes on for 5 pages.  The fist command above is "2nd form".  I'm suggesting using the 3rd form in my example.  Only this manpage uses the 1st, 2nd, 3rd "form" names. Those aren't important except when comparing the different styles of the options for this command.  I've never seen them mentioned with those names before today.

---

