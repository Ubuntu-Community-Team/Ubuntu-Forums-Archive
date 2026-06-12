---
title: "Problem getting chown to work for new ext4 partition"
date: 2020-04-01
forum: General Help
---

### Post by crazybear on 2020-04-01
On the internet, everyone claims it is simple....and I've tried all the 'solutions'...but I'm obviously doing something wrong. I can not get ownership of the partition I just made, so can not copy any files into it. The disk has only one other partition that is also ext4 and bootable. I only want this partition to be for storage. I've tried the formulas I see to put into terminal with then partition name and with the random number assigned to the partition....but nothing is working. Frustrated.....

---

### Post by The Cog on 2020-04-01
It should just be a question of using chown on the point where the partition is mounted (using sudo). Can you post the output of lsblk so we can see where that is. Also include the prompt and command lsblk, so we can see your username too. Then we should be able to post the exact command.

---

### Post by TheFu on 2020-04-01
I understand you are frustrated, for a different reason.

Please provide:
```
/etc/fstab  # line that mounts the storage
df -hT -x squashfs -x tmpfs -x devtmpfs  # to prove it is mounted and where
ls -al {/path/to/the/mount}  # so the current permissions
id
```
Don't forget the attempted chown command.

---

### Post by crazybear on 2020-04-04
Aha, Yes, people make assumptions based on their system or what they think I want for mine. I do NOT want this listed in fstab, as I do NOT want this mounted unless I mount it specifically. 

$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0    55M  1 loop /snap/core18/1705
sdf      8:80   1   1.8T  0 disk 
&#9500;&#9472;sdf1   8:81   1 931.5G  0 part /
&#9492;&#9472;sdf2   8:82   1 931.5G  0 part /media/peter-and-crazybear/[FONT=arial black]_**Storage EXT4 <===== problem partition**_[/FONT]
loop6    7:6    0  91.4M  1 loop /snap/core/8689
loop4    7:4    0  54.7M  1 loop /snap/core18/1668
loop2    7:2    0  93.8M  1 loop /snap/core/8935
loop0    7:0    0  85.9M  1 loop /snap/shotcut/59
sde      8:64   1   2.7T  0 disk 
&#9492;&#9472;sde1   8:65   1   2.7T  0 part /media/peter-and-crazybear/1st-3T-DATA-INFO
sda      8:0    0 465.8G  0 disk 
&#9492;&#9472;sda1   8:1    0 465.8G  0 part 
loop5    7:5    0   5.8M  1 loop /snap/tor/2
loop3    7:3    0  86.1M  1 loop /snap/shotcut/61

It is sdf2 [and a similar situation on another drive not in the hot swap bay at the moment]. sdf1 is obviously the OS partition and no doubt listed in fstab

$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdf1      ext4  917G  746G  126G  86% /
/dev/sde1      ext4  2.7T  2.3T  312G  89% /media/peter-and-crazybear/1st-3T-DATA-INFO
/dev/sdf2      ext4  917G   72M  871G   1% /media/peter-and-crazybear/Storage EXT4

---

### Post by CatKiller on 2020-04-04
> **crazybear said:**
> Aha, Yes, people make assumptions based on their system or what they think I want for mine. I do NOT want this listed in fstab, as I do NOT want this mounted unless I mount it specifically. 

Those two things are orthogonal. Using the *noauto* option in fstab stops the partition being mounted automatically at boot time, but having the entry in fstab prevents the userspace from "helpfully" mounting it somewhere stupid.

---

### Post by TheFu on 2020-04-04
Of course we assume things.  That's required when no data is provided.

There is a technique called automount.  The storage is only mounted when specifically requested.  When that storage isn't being used any more, then the mount is removed.

Either systemd-automount or autofs can be used.  For most people, the systemd-automount method would be easier AND it has lines added to the fstab.  You can put the storage setup in a mount unit file in the systemd config dirs, if you like.

---

### Post by The Cog on 2020-04-05
I assume your username is peter-and-crazybear. So based on the lsblk output you posted, the command you need would be:
```
sudo chown -R peter-and-crazybear:peter-and-crazybear "/media/peter-and-crazybear/Storage EXT4 <===== problem partition"
```
I suspect that's not the actual output from lsblk though, and I'm not even sure that's your username. Still, you should get the idea.

---

### Post by pbear42 on 2020-04-06
> **crazybear said:**
> I do NOT want this listed in fstab, as I do NOT want this mounted unless I mount it specifically. 
For some things, the partition has to be unmounted.  For others, it has to be.

Guess which one **chown** is.  Maybe try reading the man page.

---

### Post by The Cog on 2020-04-08
> **pbear42 said:**
> For some things, the partition has to be unmounted.
Yes, chown has to be applied to the mounted filesystem, because it operates on files inside the filesystem.
I think it may be a common mistake to try to use chown on the /dev/sd? device "file" instead, but that only changes who can read/write the partition itself. Maybe that's what crazybear was doing?

---

### Post by crazybear on 2020-04-08
Sorry, I'm had situational problems related to the pandemic and forgot to subscribe to this thread....I just tried the prescribed 
sudo chown -R peter-and-crazybear:peter-and-crazybear "/media/peter-and-crazybear/Storage EXT4

and it did not work. this is exactly the endless problem I have been having. I now have three such partitions I need to do this with, but if I 
can do one, I only need to change the name. I do NOT  understand the problem. It is not clear about when it needs to be mounted or not. Now I get
chown: cannot access 'EXT4': No such file or directory - which is NOT correct. Is it the problem of a name with no spaces in it? Other problem? Thanks

---

### Post by crazybear on 2020-04-08
OK, it worked....the problem was the " in the directions or the - between storage and EXT4, I don't know which. Removed the first and added the second and it worked.

---

### Post by TheFu on 2020-04-08
> **crazybear said:**
> OK, it worked....the problem was the " in the directions or the - between storage and EXT4, I don't know which. Removed the first and added the second and it worked.

Spaces and funny characters make shell commands harder.  i don't allow spaces in any filenames or directories to avoid that issue.  There are some characters that shells like to expand that i avoid too.  Avoid because the shell is likely to misinterpret them without explicit handling.  Experience teaches those things.

OTOH, almost any characters CAN work, but the price will be the hassles later.

---

### Post by yancek on 2020-04-08
The command you posted in post # 10 did not have the closing quote ( " ) which would have caused it to fail with the error you posted (cannot access 'EXT4': No such file or directory). The command show below should have worked.  Dashes and underscores are better if you want some separation in a name.  If you had a dash ( - ) in the name of the directory Storage-EXT4 and included it in the command it also should work.  Best not to use spaces in directory/file names.

> sudo chown -R peter-and-crazybear:peter-and-crazybear "/media/peter-and-crazybear/Storage EXT4"

---

### Post by TheFu on 2020-04-08
And learning to use **tab-completion** saves a bunch of time for things like this.  Cannot imagine doing shell stuff without tab-completion to fill in the correct files and directories with any needed escapes.

if you aren't using tab-completion already - LOOK it up and watch a youtube video for how to do it.

---

