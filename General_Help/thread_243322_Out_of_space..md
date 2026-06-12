---
title: "Out of space."
date: 2006-08-24
forum: General Help
---

### Post by Metroid48 on 2006-08-24
Hey, my root directory (/) had about 5 GB in it. I decided to do a backup using Simple Backup Config. Then, I left my computer and when I came back the partition was 99% full. Now, a lot of apps won't launch and I have too many problems with running Ubuntu.

I was just wondering, where are the files the backup utility created. I told it to use a different drive, so the backup shouldn't have gone in the root directory.

Finally, what can I do to get the space back so that apps will start working again?

Thanks,
-Metroid48

---

### Post by peabody on 2006-08-24
I suspect that the problem so many things are broken is due to / being full and therefore applications can't make temporary files in /tmp.

This may help solve your problem:

sudo mkdir /folder/on/new/drive
sudo mv /tmp /tmp.old
sudo ln -s /folder/on/new/drive /tmp

---

### Post by Metroid48 on 2006-08-24
Okay, I tried the following:

```
sudo mkdir /media/sdb1/Backup
sudo mv /tmp /tmp.old
sudo ln -s /media/sdb1/Backup /tmp
```

And the last two commands just worked instantly (it should of taken SOME time, right?). After, programs aren't working still. Also, I can't even open Nautilis or anything to check the status of the disks.

EDIT: GNOME-Terminal won't even start now.

---

### Post by peabody on 2006-08-24
My bad, I forgot something:

sudo chmod 1777 /folder/on/other/drive

And that is the speed at which the commands should happen, nothing's being copied here, we're just symlinking a folder.

I really don't recommend that you use the same backup folder though, I was suggesting that you use a seperate folder on the other drive since applications are going to make temporary files here.

---

### Post by Metroid48 on 2006-08-24
But how can I execute it?

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> But how can I execute it?

Ctrl+Alt+F1 should get you to a text terminal where you can login.  Alt+F7 to get back.

Edit: ??? I think I lost him.  Was worried about that.  Well anyway, if you manage to get back and everything still isn't working, you should be able to get things back to normal by from the recovery mode by:

```

rm /tmp
mv /tmp.old /tmp

```

then reboot.

---

### Post by Metroid48 on 2006-08-24
Okay, I booted a live cd since the other one was slowed to a crawl. (I hadn't read your advice about Ctr-Alt-F1 yet)

I went ahead and checked everything and found that it still says 0 bytes available on /media/usbdisk-1 (root folder while not using live cd).

What should I do? Is it supposed to be like that? Btw, there's still a folder called tmp.old with some stuff in it.

Also, it says /media/usbdisk-1/tmp is only 13 MB?](*,)


EDIT: /media/usbdisk-1/var is 113 MB!

---

### Post by peabody on 2006-08-24
> 
Also, it says /media/usbdisk-1/tmp is only 13 MB?


> 
sudo ln -s /media/sdb1/Backup /tmp


If the folder is only 13 megs that shouldn't be too surprising because we didn't copy over your old /tmp, just moved that /tmp name to a new folder.

I'm a little confused by what you linked /tmp to.  Was it /media/sdb1/Backup?  Was it /media/sdb1/tmp?  Is your Ubuntu onstall on a usbdisk?  is /media/usbdisk-1 where your Ubuntu install is?

Basically, when a disk is 99% full, only root can make new files, which explains why most applications don't work because many of them need to make new files.  /tmp isn't the only thing causing problems now that you mentioned it.  What is your partition layout?  is /home on a seperate partition?  I kind of assumed you had home on a seperate partition, but now that I think about it you probably don't.

---

### Post by Metroid48 on 2006-08-24
Okay, this is my partitioning. I installed the operating system and FAT32 on an external usb drive. The first partition is a FAT32 for storage that's 27 GB. The second partition is a Ext3 that's currently empty and ammasses to 3 GB (I was going to move the /var and /tmp folders, but the live cd would refuse to format it as a ext3. I only just got it to format this time around). The third, which is the root partition (/) is 4.89 GB and is an Ext3. It's currently full. Then I've got a 1 GB swap partition, and then some 500 mb of unallocated space.

Okay, so really it's just the third partition that's full. I could probably put the /tmp and /var folders on the second partition now that it works, but how would I do that? Would I just link it, like you were doing?


EDIT: Oh, yah. usbdisk-1 is what the live cd mounted my root partition as. usbdisk is the storage space.

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> Okay, this is my partitioning. I installed the operating system and FAT32 on an external usb drive. The first partition is a FAT32 for storage that's 27 GB. The second partition is a Ext3 that's currently empty and ammasses to 3 GB (I was going to move the /var and /tmp folders, but the live cd would refuse to format it as a ext3. I only just got it to format this time around). The third, which is the root partition (/) is 4.89 GB and is an Ext3. It's currently full. Then I've got a 1 GB swap partition, and then some 500 mb of unallocated space.

Okay, so really it's just the third partition that's full. I could probably put the /tmp and /var folders on the second partition now that it works, but how would I do that? Would I just link it, like you were doing?


EDIT: Oh, yah. usbdisk-1 is what the live cd mounted my root partition as. usbdisk is the storage space.

Linking is one way of doing it, but it has to be done carefully.  Curruntly under the Live CD it sounds like the new drive is under /media/usbdisk-1 while under your installed Ubuntu, it's /mnt/sdb1.  The paths needs to be right in your install.

Moving them without linking requires that each folder, /var, /tmp, etc, be on it's own partition.  You'd then edit fstab and an /dev/whatever entry for /var to the new partition and add an entry for /tmp.  I think the linking way is easier if you ask me.

**NOTE:**  When copying over the old stuff, you NEED NEED NEED NEED to do it from the command line with a command that'll preserve the filesystem permissions.  "cp -a old new" is one such way.

---

### Post by Metroid48 on 2006-08-24
No, the third partition is mounted as / in my install, (/media/usbdisk-1 in the live cd), the new ext3 is mounted as.... actually, I couldn't mount it in my install because Disks wouldn't start. In the live cd, it's /media/usbdisk-2.

I'm not sure how to do this. Currently, in my install it isn't mounted, so it won't link right if it isn't mounted. Is there a way to get it to mount when I boot back into my install so that it won't think that /var and /tmp aren't there?

I'm going to see if my install will at least launch disks now. Hold a minute.

Wait, just a sec. When I link it, should I link it with the address the install will see it as or how the live cd sees it?

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> No, the third partition is mounted as / in my install, (/media/usbdisk-1 in the live cd), the new ext3 is mounted as.... actually, I couldn't mount it in my install because Disks wouldn't start. In the live cd, it's /media/usbdisk-2.

I'm not sure how to do this. Currently, in my install it isn't mounted, so it won't link right if it isn't mounted. Is there a way to get it to mount when I boot back into my install so that it won't think that /var and /tmp aren't there?

I'm going to see if my install will at least launch disks now. Hold a minute.

Wait, just a sec. When I link it, should I link it with the address the install will see it as or how the live cd sees it?

Definitely with how your install sees it!

Here, why don't we try and summerize your portitions


/dev/hda3 <-- ext3 root
/dev/hda4 <-- swap gig

/dev/sdb1 <-- new ext3

Edit: nevermind:

/dev/sdb1 <-- FAT32 27 GB
/dev/sdb2 <-- ext3 blank
/dev/sdb3 <-- / 4.something megs

You know what, let's stop guessing, can you please post a copy of the /etc/fstab from the / partition?  Not from the live cd, but from the /media/usbdisk-1/etc/fstab?

---

### Post by Metroid48 on 2006-08-24
Firstly, thanks for helping so much. Secondly, here's the partition layout (btw, hda doesn't exist. For some reason, Ubuntu mounted the laptop's internal drive as sda. sdb is the drive it's installed in)

/dev/sdb1-> Storage FAT32
/dev/sdb2-> Root Ext3
/dev/sdb3-> New Ext3, but I didn't mount it yet in my install.

Anyway, I'm going to fix the link and then switch back to the install. Won't be 5 minutes.

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> Firstly, thanks for helping so much.


Anything for a fellow nintendo fan ;) .

> 
Anyway, I'm going to fix the link and then switch back to the install. Won't be 5 minutes.

Oh boy.  Well, if you get back up and running, try to post that /etc/fstab file I talked about.  Was in the previous post via edit, sorry about that.

What link command did you use?  It sounds like we might be getting our device files and mount points mixed up here.  Under the install I was under the impression that the new partition was under something like /mnt/sdb3?  Don't link to the device files!  Link to the mount points!

It sounds like your install is on a usb drive so in that case it makes perfect sense for the device files to be the sdx ones.  hda is for IDE.  Also, if your drives are SCSi or SATA they might be sdx too.

---

### Post by David Corrales on 2006-08-24
One thing that might help with freeing up some space... boot in recovery mode and type **sudo apt-get clean**. It'll delete all the .deb installation files you got through synaptic.

---

### Post by peabody on 2006-08-24
> **David Corrales said:**
> One thing that might help with freeing up some space... boot in recovery mode and type **sudo apt-get clean**. It'll delete all the .deb installation files you got through synaptic.

Good advice, although he may want to backup those debs first in case he ever wants to reinstall and not download 600+ megs of stuff.

---

### Post by Metroid48 on 2006-08-24
Okay, here we go.

When I booted back into my install, XServer wouldn't start (btw, I did make sure I could boot properly before. This isn't the Xserver error thing from the distro update). Then, in console mode, I deleted the syslink, moved the backup folder back, and renamed it to tmp. Yar.

It still wouldn't start. Now, the GDM starts loading (you see the loading mouse cursor), then it flashes to the text based one. 5 seconds later it repeats. However, I did get Lynx (text-based browser) to run, which it wouldn't do without the tmp folder.

Okay, here's the fstab file you wanted:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


--------------

Anyway, any ideas?

-Metroid48


EDIT: Btw, I figured out what went wrong with the syslink. I typed sdb2 instead of sdb1. But still, shouldn't it boot now that I've copied it back over?

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> Okay, here we go.

When I booted back into my install, XServer wouldn't start (btw, I did make sure I could boot properly before. This isn't the Xserver error thing from the distro update). Then, in console mode, I deleted the syslink, moved the backup folder back, and renamed it to tmp. Yar.

It still wouldn't start. Now, the GDM starts loading (you see the loading mouse cursor), then it flashes to the text based one. 5 seconds later it repeats. However, I did get Lynx (text-based browser) to run, which it wouldn't do without the tmp folder.

Okay, here's the fstab file you wanted:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb3       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


--------------

Anyway, any ideas?

-Metroid48

Okay, try this, undo your old symlink stuff, and you should probably do this from the recovery console or the livecd, although if you try it from the live cd, replace /tmp, /home and /var with /media/usbdisk-1/tmp, /media/usbdisk-1/home, /media/usbdisk-1/var:

```

sudo mv /tmp /tmp.old
sudo mkdir /media/sdb3/tmp
sudo chmod 1777 /media/sdb3/tmp
sudo ln -s /media/sdb3/tmp /tmp

```

That should link farm tmp to the new drive.  Your /home is unfortunately still full.  If you're fealing particularyl brave, try this

```

sudo mkdir /media/sdb3/home
sudo cp -a /home/* /media/sdb3/home
sudo mv /home /home.old
sudo ln -s /media/sdb3/home /home
sudo mkdir /media/sdb3/var
sudo cp -a /var/* /media/sdb3/var
sudo mv /var /var.old
sudo ln -s /media/sdb3/var /var

```

That will move both /home and /var, which could also be causing you trouble.

---

### Post by Metroid48 on 2006-08-24
Wait, just one thing before I do this.

Before, I had this:
--VFAT32 -- sdb1
--Unallocated
--EXT3 -- /
--Swap
--Unallocated

But when I created a new EXT3 in the first Unallocated space:
--VFAT32 --sdb1
--EXT3
--EXT3 -- /
--Swap
--Unallocated

Will that change the /dev/sdb2 part for mounting to root?

Just that Q.

Edit: 'Cause, should I add to mount the new EXT3 to fstab?

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> Wait, just one thing before I do this.

Before, I had this:
--VFAT32 -- sdb1
--Unallocated
--EXT3 -- /
--Swap
--Unallocated

But when I created a new EXT3 in the first Unallocated space:
--VFAT32 --sdb1
--EXT3
--EXT3 -- /
--Swap
--Unallocated

Will that change the /dev/sdb2 part for mounting to root?

Just that Q.

Edit: 'Cause, should I add to mount the new EXT3 to fstab?


Probably a good question, what /dev files does the Live CD assign to each partition?  The fact that you can boot at all seems to tell me that your / hasn't changed.  If you can get to /media/sdb3 I don't anything's changed.

Whoa!  Good point, yes, there should be an fstab entry for /dev/sdb3!  However, wasn't there already an entry for it?

Edit: from the fstab
/dev/sda3 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1

There is an entry but its listed as vfat not ext3!  That part should be changed.  The rest is probably fine.

---

### Post by Metroid48 on 2006-08-24
No, there wasn't because it was unallocated space until I made an EXT3 partition there in the live CD. This was the same time I moved the directories and messed everything up.

You know what, I'm going to try just one more boot. When I moved the directories back over, after typing 'exit' I just used Ctr-Alt-Backspace to reboot. Maybe a full reboot will work.

Be back in 5 min, 
-Metroid48

---

### Post by peabody on 2006-08-24
> **Metroid48 said:**
> No, there wasn't because it was unallocated space until I made an EXT3 partition there in the live CD. This was the same time I moved the directories and messed everything up.

You know what, I'm going to try just one more boot. When I moved the directories back over, after typing 'exit' I just used Ctr-Alt-Backspace to reboot. Maybe a full reboot will work.

Be back in 5 min, 
-Metroid48

Cntrl + Alt + Backspace isn't a reboot, it just kills X and restarts.

Edit: the fstab you gave me listed /dev/sdb3 as being the vfat filesystem?  Are you sure you managed to get it formatted as the ext3 filesystem?  It's important that it's ext3 if you plan to move /tmp /home and /var there.  Double check your /etc/fstab if it really is ext3.  If vfat is still on that line, change it to ext3.

---

### Post by Metroid48 on 2006-08-25
Okay, just in advance, sda is completely irrelevant. You see, I've got two drives. One's internal, with Windows installed (sda) and the external one (sdb) has Ubuntu installed.

I just tried rebooting again. Exact same problem with GDM. Anyway, I'm going to manually add the fstab bit. But I don't know why GDM won't boot.

Maybe I should copy the /tmp from the Live CD? Just wondering.

---

### Post by peabody on 2006-08-25
> **Metroid48 said:**
> 
I just tried rebooting again. Exact same problem with GDM. Anyway, I'm going to manually add the fstab bit. But I don't know why GDM won't boot.

Maybe I should copy the /tmp from the Live CD? Just wondering.

The fact that GDM won't work may be because / is full and therefore /home and /var are full.  Applications frequently make files in /var and /home, and if they can't they don't work.  The only thing is that root processes should still be able to write to the drive provided there's space.

/tmp is completely irrelavant.  You can completely zap /tmp and as long as the folder's still there, everything's fine on reboot.  It's just a scratch space folder.  However, if there isn't any space left on the drive, programs can stop working because they can't make files in /tmp.

At this point I'd recommend that you backup /var/cache/apt/archives to a folder somewhere and try that other guys' advice of sudo apt-get clean.  That should at least give you some space on /.

---

### Post by Metroid48 on 2006-08-25
Just one quick question then. Won't sudo apt-get clean clean the archives for the live cd? Or should I use recovery mode. Actually, I'm going to try recovery mode.

---

### Post by peabody on 2006-08-25
Just in case gdm is still going yonky on you, try to "cd /tmp" from within your booted install.  If you can't do that, then /tmp is still screwed up.

---

### Post by Metroid48 on 2006-08-25
I don't think /tmp is the problem with GDM (btw, I'm still backing up the apt_get archive thing). Lynx works fine, but wouldn't when /tmp was trashed.

Anyway, I'm just finishing backing up.

---

### Post by peabody on 2006-08-25
Okay, good, sounds like /tmp is okay, must be var then.

No problem, I probably should have mentioned that /var/apt/cache/archives would be big.  It's basically all the updates and software you've ever installed through synaptic.

---

### Post by Metroid48 on 2006-08-25
Okay, it only sorta-works now.

This is what happened. I tried logging in my regular user, the one I use all the time. It said that it couldn't write to an authorization file.

I then tried logging into a user that I've only used once, and it said:

"Your session lasted less than 10 seconds."....

Anyway, in the xsessions error file, This was the last line:

mkdtemp: Private socket dir: Permission denied

So, I still can't log in, though GDM loads properly meaning XServer is working.](*,)

EDIT: Oh, yeah. Failsafe GNOME does start without an error, but doesn't load anything. Also, I completely deleted the contents of the /tmp directory, but there's still an empty directory there.

---

### Post by peabody on 2006-08-25
hmmm, if it hadn't been for the other problems related to the new user, I would have assumed it was because the permissions on a dotfile in your home folder were messed up.  That is strange though.

How much space is free on / now?

I bet you the permissions on /tmp are wrong

What does "ls -ld /tmp/" say?

---

### Post by Metroid48 on 2006-08-25
It gets something like this:

drwxrwxr-x root root 4096 [date] /tmp

---

### Post by Metroid48 on 2006-08-25
Hey, it works!

It was actually a problem with fstab. I think, when trying to manually mount the new partition, I messed everything up. Also, I changed the /tmp folder to allow all modification access.

Anyway, thanks for all the help. I'm also going to try moving my /var and /tmp to a new partition(using a guide). What fun!:roll: 

Thanks a LOT peabody and David!
-Metroid48

---

### Post by peabody on 2006-08-25
I'm glad you got everything working again!  Anyway, you probably want the permissions on /tmp to be drwxrwxrwt which is mode 1777.  The "t" part isn't super duper important, but it does prevent other users from deleting files that aren't theirs in the temp folder.

---

