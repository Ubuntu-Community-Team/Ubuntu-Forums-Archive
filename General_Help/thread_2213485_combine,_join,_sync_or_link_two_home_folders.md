---
title: "combine, join, sync or link two home folders"
date: 2014-03-26
forum: General Help
---

### Post by captain_chaos2 on 2014-03-26
I am a bit of a newbe at this I have been using 12.04 dedicated (no other OS) for some time, I have now installed 13.10 alongside and would like to know how to join or combine the two home folders into one common folder so as to access my files with either. I have googled for two days and can't seem to find a workable solution. If some one can point me in the right direction I would be most grateful. :confused: hope this is posted in the right place.

---

### Post by CaptainMark on 2014-03-27
You have two options really the way I see it,

1) Use one as your main OS and use its home folder as per normal, then in the second OS use fstab to mount the main OS partition in a specific place and use symbolic links to access the main OS' home folder instead of the second OS' home folder

2) Create a third partition and have all of your home folders data on that partition and use fstab and symbolic links to reach this third partition from both OS'

Be aware, it is safer not to directly link one home folder to another home folder but to have a series of links linking ~/Documents to /other/os/Documents and ~/Music to /other/os/Music etc etc.

Here is the information you will need to get you started, post back if you get stuck.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://askubuntu.com/questions/214643/help-with-creating-symbolic-link](http://askubuntu.com/questions/214643/help-with-creating-symbolic-link)

And on a side note, as always. ALWAYS backup data before you start if you are modifying partitions.

---

### Post by freebird54 on 2014-03-27
> **captain_chaos2 said:**
> I am a bit of a newbe at this I have been using 12.04 dedicated (no other OS) for some time, I have now installed 13.10 alongside and would like to know how to join or combine the two home folders into one common folder so as to access my files with either. I have googled for two days and can't seem to find a workable solution. If some one can point me in the right direction I would be most grateful. :confused: hope this is posted in the right place.

This is the right place to get an answer - although it may not be exactly what you were hoping!  First off, I would recommend NOT running a common /home, although most of the advantages you expect are available in another way. The problem is the way that Linux distros work - versions of programs are often different between releases, and as they are updated regularly along with the OS, chaos can ensue when an update 'down' is attempted! I have tried it a couple of times, and ended up with re-installations required after a while each time. :)

What DOES work well is to have a common DATA partition, and have both OS's  use it.  In particular it is very useful to have all the 'default' Ubuntu directories found in /home to be actually links to a common place.  By this I refer to **Documents**, **Downloads**, **Music**, **Pictures** and **Videos** folders that appear by default in each new system installation.

I don't know your familiarity with partitioning etc, so I won't go into too much detail yet - and you could ask for more if needed and if you decide to try this solution.  Essentially, you create a partition to be separate from both, determine its UUID, and mount it as (a suggestion) **/mnt/data**.  Then you rename Documents to OldDocuments, Downloads to OldDownloads and so on in your home directory.  Create a set of default directories in /mnt/data (Documents, Downloads, Music etc) and link them to the /home directory.  At this point you will see them 'back' in your /home - but they really are the ones on /mnt/data.

Once you copy the contents of OldDocuments to the new Documents, OldPictures to the new Pictures etc etc, it is time to do the same thing in your 'other' OS version.  That is, boot into it, do the same renames, create the same link statements (the directories themselves will already exist!) and copy anything different from the OldDocuments etc directories to the new Documents etc directories - and no matter which you are in, your data will be available to both.  Better yet - only one of the OS versions has to do the data backups!

If any of this sounds too complicated - get more detailed help on any parts that sound beyond your experience level before trying it - but the information you need to do it is also out there on this forum and elsewhere with some careful Googling.  Good luck! :)

Much greater Gurus than myself may weigh in on this subject - but this is one way to safely achieve much of what you probably want.

---

### Post by oldfred on 2014-03-27
+ on freebird54's suggestions.

Other threads related to shared data partition.
 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by captain_chaos2 on 2014-03-28
Thank you very much for all your reply's, I'll work through the data and get back to you. 
I have13.10 and 12.04 set up as dual boot on a separate hard drive in separate partitions. I have disconnected this (physically unplugged) hard drive so as not to corrupt anything.
I have a clean 500G hard drive I am trying to set up so as to share files as some files need to be worked on in one distro and then in another older program on the other using Mono, and am landing up with files duplicated across the two which is becoming a little messy. Once I have this drive nicely set up I'll move the files. 

Thanks again

---

### Post by freebird54 on 2014-03-28
Perfect for the setup I described - and recommend!  Just remember to to rename the 'originals' to Old+originals before setting up the links in each of the others  :)  That way you won't lose any by accident, only on purpose.  Also - as soon as you have the setup right - back that up too!

Nearly everyone here has learned THAT the hard way at one time or another....

---

### Post by captain_chaos2 on 2014-03-28
Ok I'm going with [COLOR=#ff0000]CaptainMark's[/COLOR] 2nd option which if I understand correctly is what [COLOR=#ff0000]freebird54[/COLOR] and [COLOR=#ff0000]oldfred[/COLOR] have recommended. 
Thanks for the links, unfortunately I am pretty green at this and most of them I have already looked at and just about all have completely gone over my head.
My partitioning skills are pretty limited in and to GParted, but having the correct commands I do prefer terminal but as yet have not used it for partitioning.

So what I had was both devs on dual boot:-

/dev/sda/1      ext4             250GB     boot           Precise 12.04

/dev/sda/2     extended       250GB
   /dev/sda/6      ext4          230GB                      Ubuntu 13.10
    /dev/sda/5   linux-swap     20GB

What I have now done is resized in GParted to :-

/dev/sda/1      ext4             15GB     boot           Precise 12.04
unalocated                         235GB  

/dev/sda/2     extended       250GB
   /dev/sda/6      ext4          16GB                      Ubuntu 13.10
    /dev/sda/5   linux-swap     4GB                        I believe +-3GB is about right for swap on 32bit
unalocated                         230GB  


A couple of questions :-

>   Essentially, you create a partition to be separate from both, determine its UUID, and mount it as (a suggestion) **/mnt/data**.

Is the separate partition a Logical or Primary partition? 

What is the definition of a UUID (Universal Unique Ideentifier)? I Have read these
  [https://help.ubuntu.com/community/UsingUUID#Using_LABEL](https://help.ubuntu.com/community/UsingUUID#Using_LABEL)  
  [https://en.wikipedia.org/wiki/UUID](https://en.wikipedia.org/wiki/UUID)

Would it be for example something like this [COLOR=#0000cd]UUID="8c4e69f8-5074-42c0-8134-0b2429c4c02c [/COLOR]generated for the new partition?

I believe also  it is recommend to have two swap files, if true where would I put the second?

This is what I originally attempted but it got a bit untidy

/hda1 - 100 mb - boot for 1st distro
/hda2 - 100 mb - boot for 2nd distro
/hda3 - 500 mb - SWAP
/hda4 - 4.7 GB - root for 1st distro
/hda5 - 4.7 GB - root for 2nd distro
/hda6 - 7 gb - /share

which I got from:-
[http://www.linuxforums.org/forum/newbie/60680-linux-linux-dual-boot.html](http://www.linuxforums.org/forum/newbie/60680-linux-linux-dual-boot.html)


I hope these questions are not too silly or my post too long winded, 
thanks thus far.

---

### Post by oldfred on 2014-03-28
Generally with desktop installs it is better not to have a separate /boot. It may be required with RAID or LVM or LVM with encryption.  Otherwise a /boot is another partition to manage and does not have to be. Some other distributions default is LVM with /boot separate. Actually if dual booting better not to even use that default but manually install in ext4 partition without /boot.

I have two data partitions since I used to boot Windows. One still is NTFS to share data with XP and even though not using Windows I have not moved data into LInux formatted partition, yet.
I have /mnt/shared & /mnt/data. Then I link folders in those data partitions into my /home. You can set mount with bind (see above) or directly mount in /home if onlyl one folder or you do not mind drilling down. I prefer to have several folders in my data partition and link. But as with most computer things there are multiple ways and some prefer one and some another. 

On my last remaining MBR(msdos) drive all data partitions are logical. I now use gpt partitioning on all new drives (expect to use drive with UEFI in future) and then with gpt there is no primary or logical partitions, they all are the same or in effect all primary.

You also can share the swap file unless hibernating. If hibernating then you cannot share as the other install would overwrite the hibernation data in swap. But if dual booting best not to hibernate anyway and Linux boots very quickly so hibernation does not save much if anything.

I normally suggest 10 to 25GB for / (root) but on the smaller size you will have to regularly houseclean. I use about 10 to 11GB in my 25GB / partition and am aggressive about moving data and some hidden folder in /home like Firefox & Thunderbird profiles to my data partition for sharing.

This is the procedure I use to create mount, assign ownership & permission & edit fstab.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.


 sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by freebird54 on 2014-03-28
For the setup you have in mind, I would probably go with just 4 partitions:
1: / for system 1
2: / for system 2
3: /mnt/data for both
4: swap

I would probably give about 20 GB to each of the 2 systems, and swap would be set according to your RAM.  It is often recommended that swap be double your RAM - but the larger your RAM, the less likely you are to need that much swap - unless you are hibernating, of course.

My current setup is similar now, as I have the 2 systems living on an SSD, and the data in a couple of partitions on a spindle drive, and the speed up is most impressive... as is the simplicity of backups.
BTW - I had help from the same source as you (oldfred) and he knows :)

Any chance of adding another physical drive to your setup - sometimes one can be found for not much - and it would make your life easier (in computer terms :) )

Good luck, and feel free to ask if lost.

PS - that indeed was a UUID you posted - and you can discover them anytime with 
```
sudo blkid
```
thus allowing you to make an entry in fstab if you do it that way..

---

### Post by captain_chaos2 on 2014-03-28
Ok reconfigured Hard drive (external usb 500GB) to the following

sda5  26GB  12.04
sda6  26GB  13.10
sda7  4GB    swap
sda8  4GB    swap
sda9  440GB  mnt/data
 
reisntalling 12.04 now. 

Ill be running this drive on ASUSP8H61-MLX, intel G530 LGA1155 2.40GHz 2MB Cache If that means anything to anyone.

Thanks for all the help, I will get back to you when I am finished if not sooner.

---

### Post by captain_chaos2 on 2014-03-29
Hi freebird54 sudo bklid should be sudo blkid I only spotted it as I often reverse figures I recon it's because I view the world from a different angle.

I have hit a brick wall and cant figure this out.>   Create a set of default directories in /mnt/data (Documents, 
Downloads, Music etc) and link them to the /home directory.  At this 
point you will see them 'back' in your /home - but they really are the 
ones on /mnt/data.
I have:-
 ```
chaos@chaos-12-04:~$ ln -s /mnt/data/Downloads /home/chaos/OldDownloads
```
Works perfectly for Downloads and Documents in 12.04, I get a Downloads link in Home OldDownloads as with Documents but the rest IE:- Videos, Pictures, Templates and all of directories in 13.10 give a broken link:confused: any ideas?

---

### Post by freebird54 on 2014-03-29
> **captain_chaos2 said:**
> Hi freebird54 sudo bklid should be sudo blkid I only spotted it as I often reverse figures I recon it's because I view the world from a different angle.

I have hit a brick wall and cant figure this out.
I have:-
 ```
chaos@chaos-12-04:~$ ln -s /mnt/data/Downloads /home/chaos/OldDownloads
```
Works perfectly for Downloads and Documents in 12.04, I get a Downloads link in Home OldDownloads as with Documents but the rest IE:- Videos, Pictures, Templates and all of directories in 13.10 give a broken link:confused: any ideas?

OK - Assuming you have renamed all of the directories as Olddirectories, then here is the sequence:
```

cd
ln -s /mnt/data/Documents
ln -s /mnt/data/Downloads
ln -s /mnt/data/Music
ln -s /mnt/data/Pictures
ln -s /mnt/data/Videos

```

**cd** should take you to your /home/*username* directory.
The other commands should create what APPEARS to be directories, but in fact when you open them, you see the contents from the /mnt/data versions.

This will give a full set of those directories, with their original names in your /home/*username* directory.  If you have any contents to move from the Oldxxxx versions of the dirs into the 'new' ones - do that before removing the Oldxxx ones.

I hope that clears it up for you.

Have a g:):)d day

PS:  I don't even a different outlook for an excuse - just bad typing! (and proofing).  I am actually experiencing some keyboard anomalies right now - and I don't know if it's the board, the batteries in it (wireless) or something with the prerelease of 14.04!  However, I still should have caught it  :redface:

---

### Post by captain_chaos2 on 2014-03-29
Nope same result even after updating, upgrading and rebooting both distros :confused:

 I'll not be putting any files or programs on until I have this drive working seamlessly.
Thanks for all the help thus far :popcorn:

---

### Post by freebird54 on 2014-03-29
> **captain_chaos2 said:**
> Nope same result even after updating, upgrading and rebooting both distros :confused:

 I'll not be putting any files or programs on until I have this drive working seamlessly.
Thanks for all the help thus far :popcorn:

Not sure where the problem could be - I'll run down the steps again:

1. Have a partition, formatted (ext4?) and ready to go.
2. Have it mounted as /mnt/data
3. Create a set of working directories - 1 each of Documents, Downloads, Music, Pictures, Videos and any others you know you want to share.
4. go to /home/*username* - and ensure that versions of those names that were created by the install are NOT there under those names -- if they have contents, then rename them Old(whatever name)
5. in a terminal, follow the commands of my last post (cd, ln -s /mnt/data/Documents  etc etc)
6. still in terminal ```
cd /mnt/data/Documents
echo > testfile Testing123
```
7. go to /home/*username* and check the contents of the Documents directory - should include a file called **testfile**

Do any other testing you wish - it SHOULD be working at this point  :)

g'night 4 now...

---

### Post by captain_chaos2 on 2014-03-29
It's after midnight I'm going to bed.

Run through all of that and land up with a whole lot of broken links in the home folder.
Run```
cd /mnt/data/Documents
``` I get```
cd /mnt/data/Documents: No such file or directory
```
The ```
echo > testfile Testing123
```gives me a testfile in Home not Downloads, which is to be expected seeing as the link is broken, and the instruction is in effect coming from the home directory and not mnt data. Thanks again.

---

### Post by freebird54 on 2014-03-29
> **captain_chaos2 said:**
> It's after midnight I'm going to bed.

Run through all of that and land up with a whole lot of broken links in the home folder.
Run```
cd /mnt/data/Documents
``` I get```
cd /mnt/data/Documents: No such file or directory
```
The ```
echo > testfile Testing123
```gives me a testfile in Home not Downloads, which is to be expected seeing as the link is broken, and the instruction is in effect coming from the home directory and not mnt data. Thanks again.

I suspect that the problem still lies in - implementation - shall we say :)  If the circumstances are as described, then what I posted WILL work.  My first suspicion is that a CaSe error is creeping in somewhere - that's all too easy to miss!  Or, perhaps, the partition is not being mounted. Could you post the result of:
```
mount
```here - to make sure that I have the correct names for the partitions involved?  Remember - what I posted assumes a particular starting point for all the pieces involved.  In particular, your /home/*username* directory needs to NOT have the directories we have been working on present when you start to link things up - and the /mnt/data directories DOES NEED the directories present.

Hope this helps - and the **mount** command output should help clear up any other difficulties I can think of...

---

### Post by captain_chaos2 on 2014-03-29
Hi freebird54 thanks again, code for mount as below

```
chaos@chaos-12-40:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/chaos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chaos)
/dev/sda6 on /media/f15d3f5e-594b-47b6-b416-beaca3bd0107 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9 on /media/data type ext4 (rw,nosuid,nodev,uhelper=udisks)
chaos@chaos-12-40:~$ 

```hope it makes sense

---

### Post by freebird54 on 2014-03-30
> **captain_chaos2 said:**
> Hi freebird54 thanks again, code for mount as below

```
chaos@chaos-12-40:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/chaos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chaos)
/dev/sda6 on /media/f15d3f5e-594b-47b6-b416-beaca3bd0107 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9 on /media/data type ext4 (rw,nosuid,nodev,uhelper=udisks)
chaos@chaos-12-40:~$ 

```hope it makes sense

well - the first thing that strikes me is that you are working with **/media/data** rather than **/mnt/data** - which would certainly explain why references to /mnt/data were not getting found.  Did you mount this partition through use of the file **/etc/fstab** ?  I'm guessing not, as it would probably have been done using the UUID :)  The idea behind using /mnt/data rather than /media/data is that anything mounted at /mnt does NOT show up in Nautilus - thus you would see it only through the linked directories in ~  -  which neatly avoids any 'confusion' about how to access it.  However, if you leave it as is, and change **/mnt** to **/media** everywhere I had it in those line-by-line instructions- it should all work anyway...

OK?

---

### Post by captain_chaos2 on 2014-03-30
Right after much messing around I have it working on 12.04 under**  /media/data**.

I had a lot of trouble with the download server site, slow, timed out etc. so I changed server and got a good clean update for 12.04

Now with 13.10 I get **System program problem detected** and I see that in the install 
```
chaos@chaos-12-40:~$ mount 
/dev/sda5 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev)
``` 
second line  (rw,errors=remount-ro) from the** mount **comand you got me to run the other day.

When I open 13.10 I find the data file has become **  /media/chaos/data**.

Running either:-
[B]ln -s /media/data/Documents
ln -s /media/chaos/data/Documents

[/B]I get a broken link12.04 is on [B]/dev/sda5
[/B]13.10 is on [B]/dev/sda6

[/B]
I hope I'm not over thinking the whole thing but it seems I should reformat the drive and start again with a clean install.

I'll let you know how I get on thanks again:KS:KS

---

### Post by freebird54 on 2014-03-30
> **captain_chaos2 said:**
> Right after much messing around I have it working on 12.04 under**  /media/data**.

I had a lot of trouble with the download server site, slow, timed out etc. so I changed server and got a good clean update for 12.04

Now with 13.10 I get **System program problem detected** and I see that in the install 
```
chaos@chaos-12-40:~$ mount 
/dev/sda5 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev)
``` 
second line  (rw,errors=remount-ro) from the** mount **comand you got me to run the other day.

When I open 13.10 I find the data file has become **  /media/chaos/data**.

Running either:-
[B]ln -s /media/data/Documents
ln -s /media/chaos/data/Documents

[/B]I get a broken link12.04 is on [B]/dev/sda5
[/B]13.10 is on [B]/dev/sda6

[/B]
I hope I'm not over thinking the whole thing but it seems I should reformat the drive and start again with a clean install.

I'll let you know how I get on thanks again:KS:KS

I don't think you need to start again entirely - but you need to mount the data "drive" yourself as /mnt/data for it to show up the same in both systems.  When the system automounts the partition, it creates directories for 'chaos' and lost+found automatically - and you don't need the complication of the extra layer.  I don't have a link handy to walk you through the mount procedure (though there may be one in the ones that oldfred left you) but they are easily found.  Essentially, all you need to do is edit the file /etc/fstab to add in the partition, using the UUID you find with blkid.  You make this change to BOTH systems, THEN follow the steps I gave you for creating the linked directories. If you run **gparted** to clear off the data partition, then modify the fstab for both systems, then follow the steps -- it WILL work :)

Luck...

---

### Post by oldfred on 2014-03-30
It seems you are letting Nautilus create default mounts, not creating your own mount point.
Recent versions changed a default mount from /media/data to /media/$USER/data. I think it is to make it user specific not / (root).

Also if your 12.04 is sda5, then that is not your data partition, but your other install. You need to link to the same data partition in both installs. While you can mount your other install, that is less common. I only mount my other installs with Nautilus on an occasional basis where I may what to see something in that install.

To create mounts yourself you have to unmount the auto mount if you have done that before remounting under your mount with fstab.

---

### Post by captain_chaos2 on 2014-03-31
Ok silly me I totally missed that sorry
 > then modify the fstab for both systems, then follow the steps -- it WILL work :smile:
I have only been modifying one system#-o ie 12.04 I figured the hierarchy wrong, I thought data controlled the system not the system controlling data kinda basic when I look at it now.
I'm truly thankful for all the help and patience. Ill let you know when I have it sorted.

---

### Post by captain_chaos2 on 2014-03-31
I,m now totally at a loss, it seems as **oldfred** says > It seems you are letting Nautilus create default mounts, not creating your own mount point. I can't get rid of /mnt/data in 13-10
```
chaos@chaos-13-10:~$ sudo mkdir /mnt/data
mkdir: cannot create directory '/mnt/data': File exists
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ rm /mnt/data
rm: cannot remove '/mnt/data': Is a directory
chaos@chaos-13-10:~$ rm -r /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ rm -rf /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ sudo udisks --detach /mnt/data
[sudo] password for chaos: 
Device file /mnt/data is not a block device: Resource temporarily unavailable
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ sudo mkdir /mnt/data
mkdir: cannot create directory '/mnt/data': File exists
chaos@chaos-13-10:~$ rm /mnt/data
rm: cannot remove '/mnt/data': Is a directory
chaos@chaos-13-10:~$ rm -r /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ rm -rf /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ ls
Desktop           Music         OldDownloads  OldTemplates  Public
examples.desktop  OldDocuments  OldPictures   OldVideos
chaos@chaos-13-10:~$ cd /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo mount /dev/sda9 /mnt/data
mount: /dev/sda9 already mounted or /mnt/data busy
mount: according to mtab, /dev/sda9 is already mounted on /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo chmod -R a+rwX,o-w /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo chown -R $USER:$USER /mnt/data
chaos@chaos-13-10:/mnt/data$ cd
chaos@chaos-13-10:~$ ln -s /mnt/data/Documents
chaos@chaos-13-10:~$ 
```

My partitions are as follows

sda5  26GB  12.04
sda6  26GB  13.10
sda7  4GB    swap
sda8  4GB    swap
sda9  440GB  mnt/data

I can get 12.04 on sda5 to link to /mnt/data on sda9

Maybe I should be looking at Ubuntu 14.04 LTS rather than 13.10 as I have been using 12.04 for about two years now and some of the older programs running in mono won't run on 13.10 and some of the recent updated programs won't run on 12.04.

---

### Post by freebird54 on 2014-03-31
> **captain_chaos2 said:**
> I,m now totally at a loss, it seems as **oldfred** says  I can't get rid of /mnt/data in 13-10
```
chaos@chaos-13-10:~$ sudo mkdir /mnt/data
mkdir: cannot create directory '/mnt/data': File exists
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ rm /mnt/data
rm: cannot remove '/mnt/data': Is a directory
chaos@chaos-13-10:~$ rm -r /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ rm -rf /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ sudo udisks --detach /mnt/data
[sudo] password for chaos: 
Device file /mnt/data is not a block device: Resource temporarily unavailable
chaos@chaos-13-10:~$ 

chaos@chaos-13-10:~$ sudo mkdir /mnt/data
mkdir: cannot create directory '/mnt/data': File exists
chaos@chaos-13-10:~$ rm /mnt/data
rm: cannot remove '/mnt/data': Is a directory
chaos@chaos-13-10:~$ rm -r /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ rm -rf /mnt/data
rm: cannot remove '/mnt/data': Permission denied
chaos@chaos-13-10:~$ ls
Desktop           Music         OldDownloads  OldTemplates  Public
examples.desktop  OldDocuments  OldPictures   OldVideos
chaos@chaos-13-10:~$ cd /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo mount /dev/sda9 /mnt/data
mount: /dev/sda9 already mounted or /mnt/data busy
mount: according to mtab, /dev/sda9 is already mounted on /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo chmod -R a+rwX,o-w /mnt/data
chaos@chaos-13-10:/mnt/data$ sudo chown -R $USER:$USER /mnt/data
chaos@chaos-13-10:/mnt/data$ cd
chaos@chaos-13-10:~$ ln -s /mnt/data/Documents
chaos@chaos-13-10:~$ 
```

My partitions are as follows

sda5  26GB  12.04
sda6  26GB  13.10
sda7  4GB    swap
sda8  4GB    swap
sda9  440GB  mnt/data

I can get 12.04 on sda5 to link to /mnt/data on sda9

Maybe I should be looking at Ubuntu 14.04 LTS rather than 13.10 as I have been using 12.04 for about two years now and some of the older programs running in mono won't run on 13.10 and some of the recent updated programs won't run on 12.04.

Well  - first off. /mnt/data is the partition, not a directory... it is the place where the directories are to go when this is set up correctly.  Did you get the system working in 12.04? I think what oldfred was suggesting you get rid of was the /media/chaos/data mountpoint... when the partition was automounted...

As for whether 14.04 - that's the next move for me - I have it loaded on the 'secondary' system already, and am just waiting for its official release to switch most uses over to it (on 12.04 at the moment). It already seems pretty good, despite an oddity with my USB keyboard hookup at the moment.

To be sure of what you are actually dealing with at the moment, I would need to see the result from:
```

cat /etc/fstab
mount
ls -l ~
ls -l /mnt/data

```
from each system.  Then I would know what is going on much better :)

---

### Post by captain_chaos2 on 2014-04-01
Thanks** freebird54**

Code as requested:-


```
chaos@chaos-12-40:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c618a6fb-f9c0-4737-b4f9-77babdfb4862 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=15509a35-ac38-4d40-a846-46ee8e8b728c none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=e604cf17-767b-4024-b0a4-438e7d6ba43a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
chaos@chaos-12-40:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/chaos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chaos)
/dev/sda6 on /media/f15d3f5e-594b-47b6-b416-beaca3bd0107 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9 on /media/2c358bb9-597a-488a-a0f3-3ff42c24d2a7 type ext4 (rw,nosuid,nodev,uhelper=udisks)
chaos@chaos-12-40:~$ ls -l ~
total 48
drwxr-xr-x 2 chaos chaos 4096 Apr  1 09:21 Desktop
-rw-r--r-- 1 chaos chaos 8445 Mar 29 10:12 examples.desktop
drwxr-xr-x 2 chaos chaos 4096 Mar 29 11:41 Music
drwxr-xr-x 2 chaos chaos 4096 Mar 30 00:24 OldDocuments
drwxr-xr-x 2 chaos chaos 4096 Mar 29 15:17 OldDownloads
drwxr-xr-x 2 chaos chaos 4096 Mar 29 15:33 OldPictures
drwxr-xr-x 2 chaos chaos 4096 Mar 29 11:41 OldTemplates
drwxr-xr-x 2 chaos chaos 4096 Mar 29 15:40 OldVideos
drwxr-xr-x 2 chaos chaos 4096 Mar 29 11:41 Public
-rw-rw-r-- 1 chaos chaos   11 Mar 30 00:23 testfile
chaos@chaos-12-40:~$ ls -l /mnt/data
total 0
lrwxrwxrwx 1 chaos chaos 23 Mar 29 14:36 Documents -> /home/chaos/OldDocuments
lrwxrwxrwx 1 chaos chaos 23 Mar 29 15:04 Downloads -> /home/chaos/OldDownloads
chaos@chaos-12-40:~$ 

```



```
chaos@chaos-13-10:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=f15d3f5e-594b-47b6-b416-beaca3bd0107 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=15509a35-ac38-4d40-a846-46ee8e8b728c none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=e604cf17-767b-4024-b0a4-438e7d6ba43a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
chaos@chaos-13-10:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=chaos)
/dev/sda5 on /media/chaos/c618a6fb-f9c0-4737-b4f9-77babdfb4862 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda9 on /mnt/data type ext4 (rw)
/dev/sdb1 on /media/chaos/EC75-5887 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
chaos@chaos-13-10:~$ ls -l ~
total 44
drwxr-xr-x 2 chaos chaos 4096 Apr  1 13:59 Desktop
-rw-r--r-- 1 chaos chaos 8980 Mar 29 11:18 examples.desktop
drwxr-xr-x 2 chaos chaos 4096 Mar 29 11:36 Music
drwxr-xr-x 2 chaos chaos 4096 Mar 29 16:27 OldDocuments
drwxr-xr-x 2 chaos chaos 4096 Mar 29 16:27 OldDownloads
drwxr-xr-x 2 chaos chaos 4096 Mar 29 16:28 OldPictures
drwxr-xr-x 2 chaos chaos 4096 Mar 29 17:31 OldTemplates
drwxr-xr-x 2 chaos chaos 4096 Mar 29 16:26 OldVideos
drwxr-xr-x 2 chaos chaos 4096 Mar 29 11:36 Public
chaos@chaos-13-10:~$ ls -l /mnt/data
total 0
chaos@chaos-13-10:~$ 

```

How do I get rid of the > /media/chaos/data mountpoint from automount
I find plenty on mount but nothing on unmount, is there code to unmount.
> Did you get the system working in 12.04?

I had it working on 12.04, but when I tried to set it up on 13.01 it broke the links in 12.04.
Now when I deleat partition /dev/sda9 and asighn the unalocated space to a **new partition** formatted as **ext4** it automatically aquires 6.2GB of data where from I don't know.

/dev/sda5 is asigned to 12.04 = 3.66GB used space

/dev/sda6 is asigned to 13.10 = 4.25GB used space

Is it posible that some how the two are being combined in /dev/sda9 = 6.2GB ( the shortfall being comon files)

as I can,t even get it working on 12.04 now, as I'm now getting a
```
mkdir: cannot create directory '/mnt/data': File exists
```
statement on 12.04 as well.:confused:

Gee your patience must be running out on me  ](*,)

---

### Post by freebird54 on 2014-04-01
> **captain_chaos2 said:**
> Thanks** freebird54**

Code as requested:-


```
chaos@chaos-12-40:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c618a6fb-f9c0-4737-b4f9-77babdfb4862 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=15509a35-ac38-4d40-a846-46ee8e8b728c none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=e604cf17-767b-4024-b0a4-438e7d6ba43a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

OK - there is no mention of adding the partition in here - and there needs to be to prevent the system from trying to automount - and causing trouble!  In particular add this in to the BOTTOM of /etc/fstab in BOTH systems(I'm assuming the UUID is correct as shown in the info given - if not, substitute the UUID **blkid** tells you).
```

# / was on /dev/sda9 during installation 
UUID=2c358bb9-597a-488a-a0f3-3ff42c24d2a7  /mnt/data               ext4    errors=remount-ro 0       1

```
The first line is a comment telling you what the UUID refers to for future reference - the second line mounts the partition as /mnt/data (and nothing else!)

You do this by doing the following (carefully! - make no other changes in there without a lot of reading)
```

sudo gedit /etc/fstab

```
and pasting in the lines I show.  When you have done this, and rebooted - you will find that the partition is mounted as /mnt/data.  Then do it to the other system the same way - and it will show up there the same.  
When you check with the **mount ** command, you should see it easily near the bottom.

Then you can create the 5 standard directories (Documents etc etc) in /mnt/data from either system - once.
And THEN you can do the **ln -s** commands successfully... from BOTH systems.
And THEN it will all work (I'm working on prediction here...)

Good luck - I'm not out of patience yet :)

---

### Post by captain_chaos2 on 2014-04-01
Checked UUID=2c358bb9-597a-488a-a0f3-3ff42c24d2a7 is correct.

Sorry I don't quite understand, do I run
 	
> Code:
	sudo gedit /etc/fstab

 	
first and then paste

 
 	> Code:
	# / was on /dev/sda9 during installation 
UUID=2c358bb9-597a-488a-a0f3-3ff42c24d2a7  /mnt/data               ext4    errors=remount-ro 0       1

---

### Post by freebird54 on 2014-04-01
> **captain_chaos2 said:**
> Checked UUID=2c358bb9-597a-488a-a0f3-3ff42c24d2a7 is correct.

Sorry I don't quite understand, do I run
 	


 	
first and then paste

Yup - run the **sudo gedit /etc/fstab** (which opens up the text editor in 'root' power user mode and loads the /etc/fstab file) and then paste those two lines in at the bottom of the file - then save, exit and reboot...

---

### Post by captain_chaos2 on 2014-04-01
**sudo gedit /etc/fstab** worked well with 12.04 but on 13.10 I got this message ```
[B]chaos@chaos-13-10:~$ sudo gedit /etc/fstab
[sudo] password for chaos: 

** (gedit:1870): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found

(gedit:1870): IBUS-WARNING **: The owner of /home/chaos/.config/ibus/bus is not root!

(gedit:1870): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:1870): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
chaos@chaos-13-10:~$ [/B]
```

but Gedit came up and was very similar to 12.04 so I pasted the command in Gedit saved and closed it. After closing and rebooting both OS's show **/dev/sda9 on /mnt /data type ext4 (rw,errors=remount-ro)** but when I try to **mkdir** the 5 standard directories (Documents etc etc) in /mnt/data from 12.04 I get error **file exists**. If I** ls** for /mnt/data  all I get is **lost+found**
If I try from 13.10 to **mkdir** the 5 standard directories (Documents etc etc) in /mnt/data from 13.10 I get error **missing operand**. If I** ls** for /mnt/data  all I get is **lost+found**. 

I think I might have corrupted 13.04 :-& right in the beginning when I > Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. and I now think I may have pasted the UUID string in the wrong place it was similar to if not the same as **UUID=2c358bb9-597a-488a-a0f3-3ff42c24d2a7  /mnt/data               ext4    errors=remount-ro 0       1  **but I definitely did not paste it at the end of the template. Also 13.10 boots a lot slower than 12.04. so I think I should start again with a clean install.

---

### Post by oldfred on 2014-04-01
Minor point. With graphic applications like gedit use gksudo or gksu as a graphical sudo. It can lead to issues in some cases if you just use sudo with gui apps.

Once you create the mount point /mnt/data you do not have to create it again. If you want to remove an entry it would be rmdir command. 

After any edit of fstab, before rebooting run this command as it remounts everything. If no error messages then remount worked. Or if you get any errors you must fix them before rebooting or you may not be able to easily reboot.
sudo mount -a

It almost looks like your links are in your data partition. Links should be in your /home/chaos folder linking to the data partition. You run this from your /home (chaos@chaos-13-10:~$). It actually leaves off the second part of the command which is the where to put link and it defaults to the location you run command from or /home/chaos.
 ln -s /mnt/data/Music


~ is a short cut to /home
fred@fred-Precise:~$ cd /mnt/data
fred@fred-Precise:/mnt/data$ cd ~

Then in my home if I do a ls -l I get this (not sure if it should be root, but does not really matter as I own the linked folder & files:
lrwxrwxrwx 1 root root      19 Mar 24  2012 Documents -> /mnt/data/Documents

But in /mnt/data a ls -l shows this:
drwxrwxr-x 21 fred fred 12288 Mar 31 17:04 Documents

---

### Post by captain_chaos2 on 2014-04-03
I do apologize for my ignorance but I am seriously missing something here. I have started with a new clean install.

sda5  25GB  12.04
sda6  25GB  13.10
sda7  4GB    swap
sda8  4GB    swap
sda9  400GB mountdata

In root of both 12.04 and 13.10 I have both mnt and media directories in sda5 and sda6 respectively.

in 12.04 I ran> sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data                 
[COLOR=#0000cd]sudo mount /dev/sda5 /mnt/data as sudo mount /dev/sda9 /mnt/data (my drive, partition)[/COLOR][COLOR=#ff0000]
[/COLOR]
I land up with data directory in /mnt/data in my sda5 partition with 21.7GB free space obviously the balance of 12.04's allocated 25GB sda5 partition.

Now when I reboot I get ```
ata_id [202]:HD10_GET_Identity failed for '/dev/sda' : Invalid Argument
```
Now I tried to repair it as was suggested elsewhere on this forum with this
[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)
and got into a horrible mess so I don't want to go down that road again with this install.

My understanding is this, please tell me if I'm wrong :-

/mnt/data should refer back to sda9 and have about 400GB?

> 1. Have a partition, formatted (ext4?) and ready to go.
2. Have it mounted as /mnt/data
3. Create a set of working directories - 1 each of Documents, Downloads,  Music, Pictures, Videos and any others you know you want to share.
4. go to /home/*username* - and ensure that versions of those names  that were created by the install are NOT there under those names -- if  they have contents, then rename them Old(whatever name)
5. in a terminal, follow the commands of my last post (cd, ln -s /mnt/data/Documents  etc etc)
6. still in terminal 

I honestly think I'm stuck on step **2 **:oops:

---

### Post by freebird54 on 2014-04-03
> **captain_chaos2 said:**
> I do apologize for my ignorance but I am seriously missing something here. I have started with a new clean install.

sda5  25GB  12.04
sda6  25GB  13.10
sda7  4GB    swap
sda8  4GB    swap
sda9  400GB mountdata

/mnt/data should refer back to sda9 and have about 400GB?



I honestly think I'm stuck on step **2 **:oops:

You sort of are stuck on step 2.  Step 2 should have been following the instructions about modifying /etc/fstab so that the mounting is done on the reboot, not directly by you.  If you do that (modifying the /etc/fstab file) on both systems, then both will be ready for the rest of the steps - and yes, the /mnt/data will refer to the large partition waiting for your data.

If you allow the partition to automount (by not having it already mounted before that can happen) then confusion will result with just about any method you can try on your own - because if it mounts on /media automatically, it adds in directories you don't want/need.  If you mount it on the fly, you will end up with other difficulties as you just saw.

Once you have it mounted (which you can test by looking at the output from **mount**) then you shold have an EMPTY space (**cd** to it and try **ls -l**) to create the directories you want.  If you do NOT get those results, then post the output of those commands again and we'll try to see what went wrong.

Sorry for assuming too much in the early postings - I did not make it simple enough to follow - hopefully it is now?

Good luck...

---

### Post by captain_chaos2 on 2014-04-03
Ok :guitar:I hooked it and I absolutely hate it when this happens as I haven't a clue as to what I've done, but I found the partition /dev/sda9 as /media/mountdata in 12.04 and as /media/chaos/mountdata in 13.10 when I gparted the drive this time I gave /dev/sda9 a label [COLOR=#0000cd]'mountdata' [/COLOR]so as to try and track it. Some how it must have auto mounted as [COLOR=#0000cd]**freebird54**[/COLOR] suggested in an earlier post. Why it is  /media/mountdata in 12.04 and /media/chaos/mountdata in 13.10 I don't know but chaos it certainly is.

So it all works, although I would like to have had it done on /mnt/data as was sugested by [COLOR=#0000cd][B]freebird54


[/B][/COLOR]**[COLOR=#0000cd][/COLOR]**[COLOR=#0000cd][/COLOR]Thank you very much [COLOR=#0000cd]**freebird54**[/COLOR] for all your patience and guidance and  **[COLOR=#0000cd]oldfred[/COLOR]** for all your advice and excellent links :popcorn::KS:KS

If you don't have anything to add (to correct some of my mistakes or oversights) I'll close the post but it seems a bit of a pity I still don't have all the answers and there seemed to be quite a bit of interest in the subject. I hope those following the thread have a little more insight than I do.;)

---

### Post by captain_chaos2 on 2014-04-03
sorry [COLOR=#0000cd]**freebird54**[/COLOR] I missed your post I was drafting mine while yours was posted. I have read this link [https://help.ubuntu.com/community/Fstab  ]("https://help.ubuntu.com/community/Fstab") over and over again And I still haven't understood it properly > In general fstab is used for internal devices,  CD/DVD devices, and  network shares (samba/nfs/sshfs). Removable devices such as flash drives  *can* be added to fstab, but are typically mounted by  gnome-volume-manager and are beyond the scope of this document. could this be my problem as I'm using an external USB drive. I checked on gnome-volume-manager bu thats way over my head.

---

### Post by oldfred on 2014-04-03
If external drive all the instructions may not be as good. They really are for an internal drive that is permanently connected. Or if you disconnect external drive you may break lots of things, but reconnecting would fix those issues. It really would have to be connected when booting every time.

But you should set ownership & permissions for any Linux formatted partition whether internal, external or flash drive.

New versions add user to path of automount by Nautilus so that is normal.

Sometimes external drives do not come up to speed quick enough. One of the goals has been quicker booting. And external drives have to power up and be seen. Some have had issues with external drives coming up to speed too slow to be seen on a cold boot which prevents fstab from mounting them anyway.

---

### Post by freebird54 on 2014-04-03
> **captain_chaos2 said:**
> sorry [COLOR=#0000cd]**freebird54**[/COLOR] I missed your post I was drafting mine while yours was posted. I have read this link [https://help.ubuntu.com/community/Fstab  ]("https://help.ubuntu.com/community/Fstab") over and over again And I still haven't understood it properly  could this be my problem as I'm using an external USB drive. I checked on gnome-volume-manager bu thats way over my head.

Ok - I need to know a little bit more about that - is the entire Linux set (both 12.04 and 13.10) entirely on the external drive?  If so, then at least it would always be there when booting Ubuntu!

I will have to think about what exactly is the best way to work this then - all the intructions I gave were assuming an internal drive (I thought perhaps the lower numbered partitions were on Windows).  Hmmmm.

I'll stick in a bit of a description that might help your understanding though - while thinking of the next solution! :)

```

I think that perhaps we have a perceptual problem here - possibly from overexposure to Windows?? :)

In a Windows view of the world (dating back to CP/M days in the 70's), storage systems are disk 
drives (floppies at first), and are equal in position, as shown here:

_____________________________
|     |      |      |       |
A:    B:     C:     D:      E:

in which A: and B: were floppy drives - later on C: (and further partitions like D: above) were hard 
drives - and it became standard for the hard drives to start at C:.  When CD drives (and later DVD 
drives) came along, they were added to the end of the list, as in the E: drive above.  The point though, 
is that were all equal in position, and how to find them.  Linux (and Unix and many others) have a 
different view.

In Linux, EVERYTHING starts at / - known as root. This means that not just disk storage, but 
everything in the system!  For instance, for temporary files, there is an item identified as /tmp.  
/tmp may be found in RAM on one system, in the root partition of another, or in an add-on USB stick 
on a third - its position is NOT predefined.  This is also true of drives and partitions.  Any partition 
can be mounted (told where to be found) anywhere at all - although conventions are generally used
 to prevent too much chaos (sorry!).

                           /
 /bin      /etc       /home       /media             /mnt     /tmp  (many others)
                  /home/*username*   /media/cd0       /mnt/data         


Another perfectly 'legal' and viable setup might be more like this:

                          /
 /bin      /etc       /home       /media             /mnt     /tmp  (many others)
                 /home/*username*   /media/cd0        
               /home/*username*/Data

which means the partition would show up as if it were a just another directory (named Data) in 
your /home/*username* directory or ~.  

The difference is created by how the partition is mounted in the /etc/fstab file - that seems to be the 
main reason for its existence :) The reason we suggested using /mnt/data and the rest is that many 
of the programs on the system automatically expect to put or find their data in the 'standard' 
directories like Documents, Downloads, Music etc etc -and it is usually better and simpler to let them!


```

Hopefully that helps you see what HAS been going on - but I'll need a bit of time to see the best setup if its all external....(let me know!) - maybe I'll even test something on my other system.  Maple Leafs and Blue Jays both playing this evening though - so it may take a bit of time :)

---

### Post by captain_chaos2 on 2014-04-03
> I think that perhaps we have a perceptual problem here - possibly from overexposure to Windows?? :)

Ain't that the truth. In the old days I battled with DOS but if you got the commands right you got it right (gigo) but then along came Windows,
made me lazy and kept me ignorant.


> Ok - I need to know a little bit more about that - is the entire Linux 
set (both 12.04 and 13.10) entirely on the external drive?  If so, then 
at least it would always be there when booting Ubuntu!
Yep that is exactly what I,m trying to achieve I'm really sorry I didn't make that clear in the beginning.

As for the / partitioning in Linux vs drive in Windows I'm aware of it and appreciate the concept of running everything from root making 
processing faster but there is still a lot to get my head around and I do get my nomenclature mixed. I thought it good idea to remove the hard 
drive so root wouldn't see it. Is that why I get sda1, 2, 3 and 4 missing in Gparted, they have been assigned to the missing internal hard drive,
 dvd, floppy etc and does that explain why "Floppy Disc" comes up on my file system in Devices in 13.10.?

I do appreciate all the help and guidance thus far and certainly can wait so take all the time you need.

---

### Post by freebird54 on 2014-04-03
> **captain_chaos2 said:**
> 
As for the / partitioning in Linux vs drive in Windows I'm aware of it and appreciate the concept of running everything from root making 
processing faster but there is still a lot to get my head around and I do get my nomenclature mixed. I thought it good idea to remove the hard 
drive so root wouldn't see it. Is that why I get sda1, 2, 3 and 4 missing in Gparted, they have been assigned to the missing internal hard drive,
 dvd, floppy etc and does that explain why "Floppy Disc" comes up on my file system in Devices in 13.10.?


I suspect (without seeing you gparted screen, can't be certain) that you have have first created an extended partition (which takes up the ID sda1) and that partitions beyond that start numbering at 5 (because the primary partition maximum count is 4, and the lower numbers are pre-assigned to them) and those are what you have to work with.  IS this setup intended to remain separate from the internal drive?  I mean, will it only be used when the internal is disconnected?  There are a couple of more issues if not - such as how to get the system to boot to Ubuntu unless you can specify the external as a boot device... and how things will go with the drive identified as **sdb**5,6,7,8,9 ...

If it is to be used as currently seen (separated) it SHOULD still work as we have tried to show here...

BTW - the Maple Leafs hung on to win in overtime, but the Blue Jays fell to .500 ball... :)

---

### Post by captain_chaos2 on 2014-04-04
The setup is intended to be stand alone so I can boot it up on any machine.

/dev/sda1 is extended 457.04GB allocated boot
4MB unallocated preceding and 8GB unallocated at the end

/sda 5,6,7,8 and 9 are primary partitions



I have been running both 12.04 and 13.10 dual booted on an old HP with Pentium 4 and it is as fast if not faster than 
 Windows7 on our ASUSP8H61-MLX, intel G530 LGA1155 2.40GHz 2MB Cache with 4GB Ram.

I now want to run Linux on the above machine with Sata Config changed from IDE to AHCI to run from USB as other members of the family only use windows.
So I can remove the drive at any time and return the machine to windows.


Why this complication? three years ago I built a CNC, machine I found Linux CNC (then EMC2) best suited my needs and ran on Ubuntu 10.04 my introduction. I found a lot more help than criticism on the various Ubuntu and Linux forums, in fact I don't think I have encountered any criticisms  on Linux forums. I was then Writing Cam programs and CAD drawings on windows, this became a pain so I switched to 12.04 for CAD and CAM. Now I am using Blender for 3D, but the old machine although as fast as windows 7 is running out of grunt on big files and latest versions of Blender are running on 13.10 and not on 12.04 (at least the last time I checked) also some of the older CAM programs running on 12.04 wont run on 13.10.

It works as automounted but I would prefer to get it running as you say on MNT.
):P glad to hear your Maple Leafs won I'm going to watch the AFL now,  Hawthorn against Freemantle Dockers last years grand finalists which the Dockers won.

---

### Post by oldfred on 2014-04-04
If you want to fully remove external drive then I might suggest a full install on external drive. Better if USB ports but USB2 will work well. It just is a USB port is not as fast as a SATA hard drive port.

I have a full install in my 16GB flash drive with USB2 and flash drives are slower still especially on writes. But it is functional.

I actually suggest a system on every hard drive even if just a backup to be able to boot in case of issues on other drive(s). I mount same data partitions in every install in every drive.

---

### Post by captain_chaos2 on 2014-04-06
Finally got it sorted:biggrin:
                                                                                                                                       [**[COLOR=#000000]freebird54 post #14[/COLOR]**]("http://ubuntuforums.org/member.php?u=228502")      

                         
> Not sure where the problem could be - I'll run down the steps again:

1. Have a partition, formatted (ext4?) and ready to go.
2. Have it mounted as /mnt/data
3. Create a set of working directories - 1 each of Documents, Downloads,  Music, Pictures, Videos and any others you know you want to share.
4. go to /home/*username* - and ensure that versions of those names  that were created by the install are NOT there under those names -- if  they have contents, then rename them Old(whatever name)
5. in a terminal, follow the commands of my last post (cd, ln -s /mnt/data/Documents  etc etc)
6. still in terminal      Code:
     cd /mnt/data/Documents
echo > testfile Testing123 
7. go to /home/*username* and check the contents of the Documents directory - should include a file called **testfile**


I used this as reference to set up my 500GB USB external drive
**[SIZE=3]Thread: [Making a bootable partitioned usb pen drive]("http://ubuntuforums.org/showthread.php?t=1719346")[/SIZE]**

[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the external USD Hardrive.
Insert the Live CD. 12.04
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
Installation type select "Something else
Continue
Select "New Partition Table" click (**THIS WILL TOTALLY WIPE YOUR HARD DRIVE)** 
Continue
Click "Free space" then click "Add".
Select "Primary", "New partition size ..." 25GB, Beginning, Ext4, and Mount point  "/" then OK.
ie first partition :-           /dev/sda1 ext4   /  check mark “Format?”
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = (4GB), Beginning and "Use as" = "swap area" then OK.
ie second partition :-          /dev/sda2 swap
Click "Install Now".
Select your location.
Continue
Select Keyboard layout.
Continue
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Continue
Wait until install is complete.
Click restart
Remove 12.04 live CD click  Enter
Wait for reboot
Insert 13.10  Live CD. Leave tray open
Restart
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
Installation type select "Something else
Continue
Click "Free space" and "+".
Create partition
Select "Primary", "Size ..." 25GB, Beginning of this space, Ext4, and Mount point = "/" then OK.
ie third partition :-        /dev/sda3 ext4
 
[COLOR=#0000cd]1. Have a partition, formatted (ext4?) and ready to go.[/COLOR]

Click "Free space" and "+".
Create partition
Select "Primary", "New partition size ..." = 445 GB), Beginning of this space,ext4, OK. (no mount point!!!)
/dev/sda4 ext4 
 
select:-        /dev/sda3 ext4  / 
device for boot loader installation :    /dev/sda  
Click "Install Now".
No mount point assigned for ext4 file system in partition #4 (leave as is unmounted)
Continue
Select your location.
Continue
Select Keyboard layout.
Continue
Insert your name, username, password, computer name and select if you want to log in automatically .
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Continue
Enter Email
Returning user
Password
Continue
Wait until install is complete.
Click restart
Remove 13.10 live CD click  Enter
Wait for reboot


 [COLOR=#0000cd]2. Have it mounted as /mnt/data  in both systems[/COLOR]

 **13.10 Saucy Salamander**
**Step 2**
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda4 /mnt/data
#where sda4 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R chaos:chaos /mnt/data   (substitute your username:username)
 
[COLOR=#0000cd]3. Create a set of working directories - 1 each of Documents, Downloads, Music, Pictures, Videos and any others you know you want to share.[/COLOR]
**Step 3**
cd /mnt/data
mkdir Documents
mkdir Downloads
mkdir Pictures
mkdir Templates
mkdir Videos 

[COLOR=#0000cd]4. go to /home/*username* - and ensure that versions of those names that were created by the install are NOT there under those names -- if they have contents, then rename them Old(whatever name)[/COLOR]
**Step 4**
rename Documents to OldDocuments, Downloads to OldDownloads etc in home directory.
 
[COLOR=#0000cd]5. in a terminal, follow the commands of my last post (cd, ln -s /mnt/data/Documents etc etc)[/COLOR]
 [B]Step 5
[/B]cd
ln -s /mnt/data/Documents
ln -s /mnt/data/Downloads
ln -s /mnt/data/Music
ln -s /mnt/data/Pictures
ln -s /mnt/data/Videos 

[COLOR=#0000cd]6. still in terminal 
Code:
cd /mnt/data/Documents
echo > testfile Testing123
[/COLOR]
Code:
cd /mnt/data/Documents
echo > testfile Testing123
 
go to /home/*username* and check the contents of the Documents directory - should include a file called **testfile**
 
[COLOR=#0000cd]2. Have it mounted as /mnt/data[/COLOR][COLOR=#ff0000]  in both systems[/COLOR]
**12.04 Precise Pangolin**
**Step 2**
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda4 /mnt/data
#where sda4 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R chaos:chaos /mnt/data
 
[COLOR=#0000cd]3. Create a set of working directories - 1 each of Documents, Downloads, Music, Pictures, Videos and any others you know you want to share.[/COLOR]
**Step 3** (This step is not necessary in second system)
cd /mnt/data
mkdir Documents
mkdir Downloads
mkdir Pictures
mkdir Templates
mkdir Videos 
these should all come up as “File exists” as they were created in previous 13.10

[COLOR=#0000cd]4. go to /home/*username* - and ensure that versions of those names that were created by the install are NOT there under those names -- if they have contents, then rename them Old(whatever name)[/COLOR]
**Step 4**
rename Documents to OldDocuments, Downloads to OldDownloads etc in home directory.
 
5[COLOR=#0000cd]. in a terminal, follow the commands of my last post (cd, ln -s /mnt/data/Documents etc etc)[/COLOR] [B]
Step 5[/B] 
cd
ln -s /mnt/data/Documents
ln -s /mnt/data/Downloads
ln -s /mnt/data/Music
ln -s /mnt/data/Pictures
ln -s /mnt/data/Videos 
[B]
Step 5[/B]
go to /home/*username* and check the contents of the Documents directory - should include a file called **testfile**

[**[COLOR=#000000]freebird54[/COLOR]**]("http://ubuntuforums.org/member.php?u=228502") thank you so much for all your time and patience:popcorn::popcorn: It finaly paid off I was about to give up last night when I spotted my final mistake:redface: IE sudo chown -R $USER:USER$ /mnt/data, sudo chown -R $chaos:chaos$ /mnt/data when I should hve used sudo chown -R chaos:chaos /mnt/data. Was by far not my only mistake but was the one that almost sank the ship.
Also a big thankyou to **oldfred** for his valued input and excelent links.:popcorn::popcorn:

If there aren't any edits, coments or aditions you would like to make, I'll close the thread as solved. Cheers thanks again.

---

