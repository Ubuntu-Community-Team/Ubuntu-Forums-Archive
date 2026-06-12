---
title: "Backing up Mdadm Question"
date: 2008-04-24
forum: General Help
---

### Post by yeaitsdark on 2008-04-24
I've been looking around online but for some reason I haven't really found anything to answer my question about this. A while back I set up mdadm for raid 5 array and well everything has been working wonderfully. My concern however is my OS (Ubuntu Gutsy) on that machine runs on it's own drive ind. of the array and well, if it crashes I don't want to loose access to my raid. So I was wondering is there a need to backup some configuration of mdadm or is this information included on the drives themselves that the program accesses? In the event I need to reinstall the OS on a new drive, what would I need to do to regain control over that array? Thanks in advance.

---

### Post by justleen on 2008-04-24
considering its a software RAID, you will have some problems restoring everything after a crash..

you should keep a backup of all your data, so in case eveerything fails, you can reinstall ubuntu, recreate the raid set, and copy the data back..

This is (AFAIK) the "flaw" of a software raid: if the software failes, you lose your raid..

Anyone correct me if im wrong on this one!

---

### Post by yeaitsdark on 2008-04-24
Thanks yea that's good to know I don't mind backing up the entire system drive, which really isn't that large and I don't predict any problems but, that's when problems always happen when you least expect them. I found an article [http://kev.coolcavemen.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](http://kev.coolcavemen.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)

Which isn't my situation but based on this information I would think mdadm is able to do what I'm thinking. Also, I'm not dealing with any data corruption we're just talking in theory if my file server system drive fails. On a side note I really impressed with mdadm for being as many say a "slow" system I'm more than happy with it. It's actually quite fast, then again the server is a good system. Also I had read, and hence this inquiry that software raid, while performance my not be the best - is able to be "moved" to another system because it doesn't rely upon a specific hardware card to control the array.

Also, I noticed a mdadm .conf file in /etc/mdadm and was wondering is it that simple? 

Output of mdadm.conf
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=4 spares=1 UUID=69dd6c6a:cad4d50a:3cc4cb4a:934a4e06

I'm confusing myself now as I look for more information. Because basically all I wanna do is make a nice little emergency CD-ROM with some "well that sucked" stuff on it, foremost being a way to bring mdadm back after an OS level crash. (not a raid array crash, although one could in theory cause the other)

---

### Post by smittex on 2008-04-25
Exactly what I was looking for.  In actuality, I am considering a clean install of my OS drive to Mythbuntu 8.04 (from Feisty) for my media/web/pbx server.  My current config is as follows:

/dev/hda drive mounted to / (OS, MythTv, Apache, MySQL, FreePbx, etc.)

/dev/md0: 3 500GB Drives (sda, sdb, & sdc) setup in RAID-5 mounted to /media/stuff

Contents of /etc/mdadm/mdadm.conf:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 30 Sep 2007 22:43:28 -0500
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $


It doesn't seem to look like the other mdadm.conf's I've seen on the web.

Anyway, I am thinking about backing up the contents of the /dev/hda (using tar) and placing on the raid array, but if there is some important configuration file on /dev/hda that sets up the RAID array, if /dev/hda fails, I have no way of reconstructing the array to retreive the backup???

Of course, about 6 months ago, something happened and I couldn't reconstruct the array.  I finally got another drive and used some forensic utility to recover the data and copy to the new drive.  This was a headache and a nightmare since my array is _my backup_.

I am about to boot up to the Ubuntu 8.04 Live CD to see if it can see the array "without the config file", but I was wondering if anyone else has any suggestions about mine and yeahitsdark's concerns.

---

### Post by smittex on 2008-04-25
Ok, it looks like its working well.  Booted to Ubuntu 8.04 AMD64 Live CD & ran the folowing cmds:

#sudo apt-get install mdadm
#ls /dev/md*  ..(nothing)
#sudo cat /proc/mdstat ..(nothing interesting)
#sudo mdadm --assemble --scan
    (/dev/md0 started)
#sudo mkdir /media/stuff
#sudo mount /dev/md0
    (/dev/md0 mounted to /media/stuff)
#ls /media/stuff
    (all my stuff shows up!!!!)

Now I'm gonna reboot to the OS already installed (Feisty) and make sure nothing was corrupted (which I seriously doubt) and backup the system (< 8GB) to the array (using tar).  And while crossing my fingers, reboot to the Mythbuntu 8.04 AMD64 Alternate CD and format / and install Mythbuntu.  I will try to get back on the success of adding the raid array after format/install so yall can get a feel for it.

---

### Post by Sp0tteh on 2008-04-27
> **smittex said:**
> Ok, it looks like its working well.  Booted to Ubuntu 8.04 AMD64 Live CD & ran the folowing cmds:

#sudo apt-get install mdadm
#ls /dev/md*  ..(nothing)
#sudo cat /proc/mdstat ..(nothing interesting)
#sudo mdadm --assemble --scan
    (/dev/md0 started)
#sudo mkdir /media/stuff
#sudo mount /dev/md0
    (/dev/md0 mounted to /media/stuff)
#ls /media/stuff
    (all my stuff shows up!!!!)

Now I'm gonna reboot to the OS already installed (Feisty) and make sure nothing was corrupted (which I seriously doubt) and backup the system (< 8GB) to the array (using tar).  And while crossing my fingers, reboot to the Mythbuntu 8.04 AMD64 Alternate CD and format / and install Mythbuntu.  I will try to get back on the success of adding the raid array after format/install so yall can get a feel for it.

Hey, how did you go with this?

---

### Post by smittex on 2008-04-27
Well, after some troubles with the Mythbuntu install (GUI not starting & some GRUB issues), i finally got in.  Installed mdadm and issued

#sudo mdadm --assemble --scan
    (/dev/md0 started)

looks like everything worked correctly and was able to mount my /media/stuff.

I think for anyone wanting to test how it would work, just boot to a Live CD, apt-get install mdadm (it wont touch your hd) and issue the above cmd.

---

### Post by yeaitsdark on 2008-04-30
Ah sweet ok. Yea I was slack on rechecking this post :S because I figured maybe no one else had this concern. So yea that's great thanks so much for looking into that. It's just well awesome to know it's that simple! I no longer fear for my data lol.

- and at times I tell myself I'm normal...

---

### Post by smittex on 2008-05-02
Well after Mythbuntu et.al., my system was essentially useless.  I popped in the LiveCD and formatted/reinstalled Mythbuntu on the PATA drive.  Now, once in the OS, I installed mdadm, sudo mdadm --assemble --scan (/dev/md0 started), but when I mount (sudo mount /dev/md0 /media/stuff) it gives me "You must supply filesystem type".  A quick addition of " -t ext3" comes up with "filesystem can't be found".  dmesg | tail comes up with "VFS: Can't find ext3 filesystem on dev md0."

Any ideas?  I've been searching google/ubuntu forums like mad for the last 2 days with no avail.

---

### Post by yeaitsdark on 2008-07-27
Hey, I know it's quite a while after the fact. A few days ago, I just redid my file server. Our situations might be different because I have my "system" on a single non-raided hard drive, and my array on the 5 others. I just unplugged all the "raid" drives and made sure to let the new os (ubuntu just to clarify) only touch the drive that wasn't in the raid. 

I did sudo mdadm --assemble --scan (started no problems) then added an entry to my fstab so it would auto mount and the like. 

My thinking, is maybe - and like I said (a while after you last post), but did you overwrite one of the partitions? or did one of the drives fail?

At any rate, I'm curious to see how you made out. I hope you were able to resolve that. But with raid, being as we want to know our data is safe - even late in the game it would be good info to know what happened with your situation.

---

