---
title: "Ubuntu disk utilities show free space incorrectly"
date: 2007-02-28
forum: General Help
---

### Post by Patrick K on 2007-02-28
On one of my Fat32 partitions I have about 20GB of files. The total size of the partition is 35.6GB so it has about 15GB free. 

Nautilus shows 35.6GB as total and 35.6GB as free space. The property page shows contents as 20.8GB yet the free space on the property sheet shows as 35.6. 

System Monitor shows 36.1 total, 540MB used, and 35.6 free. 

GParted show 36.12 total, 558.5 used, and 35.5 unused.

I'm not concerned about the discrepancy between apps since they could be reading GiB or GB. I am concerned about the discrepancy between what they show and what is actually on the partition. If someone didn't know better they could think the partition was nearly empty and format it losing all the data. (I wonder if this might be part of some of the partitioning issues that appear on this forum.) This isn't the only partition that has this issue. Another has backups stored on it yet the total used is shown as 18MB. In reality there is around 15GB. Others seem to read correctly. 

Why are the disk utilities reading these partitions incorrectly?



Here is the fdisk -l output
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         610     4899793+   b  W95 FAT32
/dev/hda2             611       19457   151388527+   f  W95 Ext'd (LBA)
/dev/hda5             611        5325    37873206    b  W95 FAT32
/dev/hda6            5326       10040    37873206    b  W95 FAT32
/dev/hda7           10041       14749    37825011    b  W95 FAT32
/dev/hda8           19327       19457     1052226   82  Linux swap / Solaris
/dev/hda9           14750       15532     6289416    b  W95 FAT32
/dev/hda10          15533       17559    16281846   83  Linux
/dev/hda11          17560       19326    14193396   83  Linux

Partition table entries are not in disk order

```
BTW, I have no problem accessing any of the partitions or files on my system

---

### Post by chggr on 2007-02-28
You can use this command to see how much space is left on your partition: 

df -h

Is the output of this command correct or not?

---

### Post by Patrick K on 2007-02-28
Here is df -h output:
```
                 Total  Used   Free  Percent
/dev/hda6   37G  541M   36G   2% /media/hda6

```

Here is what both Windows and I think it should be:
```
                        Total         Used       Free      Percent
    F: Local Disk FAT32 36967 MB  21395 MB 15571 MB  42 % 
```
On this partition are 34 Audacity directories. Each contains from 100mb to 1.5gb. With an average of about 550mb each. (Audacity writes each project in 1mb chunks so many directories have several hundred files.) Within the Directory "Tunes" are 19370 items totaling 19.9gb. So as you can see, there are a lot more Gb's used than Ubuntu's utilities show.

---

### Post by Patrick K on 2007-02-28
Anyone care to comment on this?

---

### Post by chggr on 2007-03-01
Well, that's really strange. 

Open this partition, select every file and folder on it, right-click and click on properties. What does it show you under the tab: Contents, totalling ???

Does ubuntu recognize all the files you have on that partition?

---

### Post by Patrick K on 2007-03-01
Thanks for the reply. 

Well, with some 19,000 files, I'm not going to go through each one, that'd probably take a month or more. Selecting random files shows the file size correctly. Selecting all the files in a directory and looking at the property sheet shows the correct number of files and MB for that directory. For instance, one directory has 1232 items totaling 1.2GB. Yet this doesn't seem to be included in the total size of the files when viewing the disk parameters of the whole disk in GParted, System Monitor, or Nautilus. 

I wonder if this situation is unique to my system or if others have the same issue.

---

### Post by chggr on 2007-03-02
I think that the problem is caused because you have too many files inside the folders. A fat filesystem can only support a number of files inside the folder, so if one of your folders has overcome this number of files, then it is not counted on total disk space.

That's what I think. It maybe wrong...

---

### Post by Patrick K on 2007-03-02
I hadn't heard that before but I'll look into it. W98 see the partition and all the files correctly, though. I was reading about the FAT file system and with FAT32 the limit on the number of files in the root directory was removed. However, I was unaware that there was ever any limit on subdirectories.  
Thanks for replying.

---

### Post by Patrick K on 2007-03-04
Anyone have any ideas?

---

### Post by Patrick K on 2007-03-15
I've been seeking an answer for this issue for a while. I hope someone will be able to help. If not perhaps someone has an idea where I might get an answer.

Attached is the property sheet from a directory on this partition.  Notice it says the free space is 35.3GB and the contents total 20.2GB. The total size of the partition is 35.6GB. There are other partitions that are incorrectly noted, also. It would be great if someone could either come up with an answer or direct me to an answer, or at least to a possible answer. 

Should I file a bug report with Ubuntu?
Thanks

---

### Post by Patrick K on 2007-03-16
I've been trying to find an answer to an issue for several weeks. I've post here and have had the post moved to other sub-forums as well.

Here is the post:

[http://ubuntuforums.org/showthread.php?t=372324](http://ubuntuforums.org/showthread.php?t=372324)

Since there doesn't seem to be an answer on the Ubuntu Forums, is there another place that I could seek one?

---

### Post by aysiu on 2007-03-16
Please do not create new threads to draw attention to an old one. If you feel the old thread needs more attention, you can "bump" it every day or two by just adding another post to it. In the meantime, I've merged this in with your other thread.

I'm not sure where else you can go besides the Ubuntu Forums. There are various other Linux forums around: LinuxForums, LinuxQuestions. You may find more knowledgeable people on the Gentoo forums, too.

---

### Post by zeus77 on 2007-04-09
Have you tried running fsck?  [Others]("http://ubuntuforums.org/showthread.php?t=103599") have reported success with this command (unmount first!):
```
sudo dosfsck -vr /dev/hda6
```

zeus77

---

### Post by Patrick K on 2007-04-10
Thanks for the reply. I tried your suggestion but it didn't make any difference. Here is a screenshot taken after running the command you suggested. Notice that the Properties page show the correct used space but not the correct free space. GParted has both the used and free space incorrect, the total size is correct.

---

### Post by zeus77 on 2007-04-11
maybe it's worth trying the Windows CHKDSK program?

---

### Post by Patrick K on 2007-04-11
I have W98 and scandisk, which doesn't find any problems. Windows sees the partition correctly. 

I haven't tried the GParted LiveCD. I'm going download it and see what it turns up. So far there haven't been any problems but I am concerned that there could be in the future. At this point, I'm open to any suggestions.  Thanks, again for your suggestions.

---

### Post by Patrick K on 2007-04-11
As a follow up, I'm running off the Edgy LiveCD. Here is a screenshot of GParted (from the Edgy LiveCD). Notice that it sees **hda6** correctly.. Both the used and free space is correct. 

Any thoughts why the installed copy of Ubuntu doesn't see it correctly?

---

### Post by Patrick K on 2007-04-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/106439](https://bugs.launchpad.net/ubuntu/+bug/106439) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Still looking for an answer.

---

### Post by Patrick K on 2007-04-27
Bump

---

### Post by Patrick K on 2007-04-29
bump

---

### Post by Patrick K on 2007-05-02
bump

---

### Post by dcstar on 2007-05-03
I have just discovered that Nautilus Properties does not count hidden items!

This can lead to a big discrepancy in the "Contents" output to what is actually in a filesystem.

I have reported it: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/112042](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/112042)

---

### Post by Pragmatist on 2007-06-12
From your experiments, it looks like this is a problem for you only in Fiesty.  So, at least for the time being, worse comes to worse you could always roll back to edgy.

In the meantime, please post your **/etc/fstab**

---

### Post by Patrick K on 2007-06-12
I appreciate you taking a look at this. Both Feisty (actually, Ubuntu Studio but regular Feisty had the same problem) and Edgy have this issue. I currently use both Feisty and Edgy (Edgy mainly). I first noticed this problem with Edgy back in February. I hoped Feisty would fix it. I rewrote both fstab files to make them more legible. The only change I made was to rearrange them and change the UID to allow me full access.

Here is fstab from [COLOR="Red"]Feisty:[/COLOR]> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
UUID=2676cc8e-24ed-4458-9c29-80bc5be6866b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=760d70e5-4625-4560-833a-0267e496f789 /home           ext3    defaults        0       2
/dev/sda1       /media/C        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sdb1       /media/D        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sda5       /media/E        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sda6       /media/F        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sda8       /media/G        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sda11      /media/H        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
#/dev/sdb5       /media/I        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sdb6       /media/J        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sdb7       /media/K        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sdb8       /media/L        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sdb9       /media/M        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/sda12      /media/610root  ext3    defaults        0       2
/dev/sda13      /media/610home  ext3    defaults        0       2
/dev/sda7        none           swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0Here is [COLOR="Red"]Edgy's[/COLOR] fstab:> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda12
UUID=a017be90-eff5-4d4a-b83d-3fe29406d3df /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda13
UUID=8ef95f8d-ea34-4c98-ad26-e8604350a592 /home           ext3    defaults        0       2
# /dev/hda9
#UUID=760d70e5-4625-4560-833a-0267e496f789 /media/704home  ext3    defaults        0       2
# /dev/hda10
#UUID=2676cc8e-24ed-4458-9c29-80bc5be6866b /media/704root  ext3    defaults        0       2
/dev/hda1       /media/C        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hdc1       /media/D        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hda5       /media/E        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hda6       /media/F        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
# /dev/hda11
UUID=464C-0CC9  /media/H        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
# /dev/hda8
UUID=4598-9D46  /media/G        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
# /dev/hdc5
#UUID=0000-0DAA  /media/I        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hdc6       /media/J        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hdc7       /media/K        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hdc8       /media/L        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
/dev/hdc9       /media/M        vfat    defaults,utf8,umask=007,uid=1000,gid=46 0       1
# /dev/hda7
UUID=9f1f3a51-6c8e-4d1f-906f-0a72668e25a7 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0Notice that most partitions do not have UUID numbers. I have inquired how the UUID numbers are generated but never got an answer. /media/F is the one with the 21GB error although several other have the same problem but on a lesser scale.

---

### Post by Pragmatist on 2007-06-12
I will study this in more detail, but for the time being, I have two points to make:

1.) You have a very complicated fstab and the largest number of partitions I've ever seen!  In theory I suppose this shouldn't be a problem, but bear in mind that the problems your having could easily be related to the complexity of your arrangement.  Your setup is not simple! :)  With that said, methodical and patient analysis should provide the answers.

2.) There are plenty of answers about UUID out there if you search for them (as opposed to ask, for example).  Here is one important resource that answers your question:
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

Notice this part:
> Since Edgy, Ubuntu requires the use of **UUID** or **LABEL** (for filesystems including swap), or udev-created symlinks (for removable media like CDROMs and USB drives).  **[SIZE=3]Directly using /dev/hd* or /dev/sd* is no longer supported[/SIZE]** (since these device assignments can change from boot to boot):

---

### Post by Patrick K on 2007-06-12
I did a 'net search on UUID but didn't run across that page. I'll give the "Converting" section a try. I don't know why installing Edgy and Feisty didn't automatically create the UUID. I posted at Lunchpad Questions but never got an answer. Any thoughts on this?

As of now in Edgy, the code 
 sudo /sbin/vol_id -u /dev/hda1
returns:
/dev/hda1: unknown volume type

I'll have to reboot to see what Feisty returns.

Time to make some backups and run some code. Hopefully, I can recover if all goes wrong. So far I have held off installing much or creating many data in either Edgy or Feisty, so reinstalling wouldn't be traumatic. Linux, at this point, is still very much in the experimental stage for me.   

As for the number of partitions, they go back to the old partition size restrictions in DOS and Windows and a, somewhat misguided, attempt to organize data. When I'd install a larger drive I'd recreate the same partition scheme. That way the paths remained valid. I still run the original W98 install from 1998. I'd just clone it to the new drive(s) and go. The only hardware remaining is the case and floppy.

---

### Post by Patrick K on 2007-06-13
Feisty returns the same message. 
/dev/sda1: unknown volume type

I'm a bit gun shy about doing what the page you posted suggest. I hope "converting" doesn't screw up things. I think I'll try it on Feisty/Ubuntu-Studio first since I don't use it very often.

---

### Post by Pragmatist on 2007-06-13
What is the output of these two commands:

```
mount
```

```
df -h
```

---

### Post by Patrick K on 2007-06-13
Here is mount in edgy:> /dev/hda12 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda13 on /home type ext3 (rw)
/dev/hda1 on /media/C type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hdc1 on /media/D type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hda5 on /media/E type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hda6 on /media/F type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hda11 on /media/H type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hda8 on /media/G type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hdc6 on /media/J type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hdc7 on /media/K type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hdc8 on /media/L type vfat (rw,utf8,umask=007,uid=1000,gid=46)
/dev/hdc9 on /media/M type vfat (rw,utf8,umask=007,uid=1000,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

df -h> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda12             15G  2.7G   12G  20% /
varrun                252M   80K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  156K  9.9M   2% /proc/bus/usb
udev                   10M  156K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.0M  244M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hda13             15G  289M   14G   3% /home
/dev/hda1             4.7G  829M  3.9G  18% /media/C
/dev/hdc1             7.6G  4.3M  7.6G   1% /media/D
/dev/hda5              37G  2.3G   34G   7% /media/E
/dev/hda6              37G  1.4G   35G   4% /media/F
/dev/hda11            6.8G  1.6G  5.2G  24% /media/H
/dev/hda8             6.0G  1.2G  4.9G  19% /media/G
/dev/hdc6              18G  1.7M   18G   1% /media/J
/dev/hdc7              18G  1.7G   16G  10% /media/K
/dev/hdc8              18G  5.0M   18G   1% /media/L
/dev/hdc9              18G   13G  4.4G  75% /media/M


---

### Post by nonlinear on 2007-07-06
i'm having a similar problem after resizing a partition in gparted...  gparted reports the new increased size, but ubuntu isn't seeing the new space.  ran fsck several times to no avail.  very strange indeed.

EDIT:  To solve the problem, I just resized teh partiton to its orig size, formatted the extra space as ext3, and then re-added it onto the partiton.  i'm not an expert in linux, but i think that when gparted adds on to a partiton, it doesn't change the file system of the stuff you are adding (in my case it was swap or unallocated, can't remember), and ubuntu will only recognize the filesystem assigned to the drive

---

### Post by Patrick K on 2007-07-10
I've thought about reformatting the partitions. All the problem ones are Fat32. I'd have to do them one at a time, but I have room on other partitions to do full backs of each. 

Since they are Fat32 and contain no system files, I wonder if I should use Gparted from the live CD (very slow) or umount them and run the installed version.

---

### Post by kaay on 2007-07-23
My case:
Occasionally I "lose" some free space on my FAT32 partitions, for instance - a 60GB one with 31GB occupied reports less than 100MB free.
Now, before someone jumps at me with a suggestion to clean cache, logs or trash folders under any name, my partitioning utilities (qtparted, etc), and any Windoze see the free gigs correctly. Also, creating big files in Windoze and then deleting them in Ubuntu can increase the reported space.

The following helps:
```
dosfsck -r {partition}
```
(You might need to unmount first).
It should give you
```
Free cluster summary wrong (28382 vs. really 861151)
1) Correct
2) Don't correct
? 1
Perform changes ? (y/n) y
```
This isn't exactly a solution, but a working fix for when the problem manifests itself.

It shouldn't be left to the user to perform such maintenance. Same with flashdrives suddenly becoming read-only (usually after being unplugged without being unmounted), the fix for which is
```
sudo mount -o remount,rw {partition}
```, and equally difficult to find on the net.

---

