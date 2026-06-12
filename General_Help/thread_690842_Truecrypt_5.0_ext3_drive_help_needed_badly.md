---
title: "Truecrypt 5.0 ext3 drive help needed badly"
date: 2008-02-07
forum: General Help
---

### Post by kingleer on 2008-02-07
Edit: I was trying to play around with TC 5 and create an ext3 partition. 

Solution: This is possible with TC 5, but the volume gets dismounted randomly. Go back to 4.3a where you've got a CLI. 

TC5 has a ******** of design flaws. Seriously.

---

### Post by mrsteveman1 on 2008-02-07
Is the truecrypt device still mapped?

It should be something like /dev/mapper/truecrypt0, you can find out by doing truecrypt -l

Post the results of a new mkfs.ext3 on your mapped truecrypt device, but be careful if you have more than one TC volume mounted you don't want to write over another one.

---

### Post by kingleer on 2008-02-07
> 
Is the truecrypt device still mapped?

It should be something like /dev/mapper/truecrypt0, you can find out by doing truecrypt -l
 

When it's mapped it's something like that in 4.3a. Not in 5.

---

### Post by mrsteveman1 on 2008-02-07
Odd problem thats for sure, I've never had trouble making ext3 partitions on truecrypt devices, even huge whole drives.

Try formatting it for another fs from linux, like reiserfs and see what happens.

---

### Post by kingleer on 2008-02-07
> 

Try formatting it for another fs from linux, like reiserfs and see what happens.

 

Creating a reiserfs partition is possible in version 5. Ext3 isn't. Solution: Use 4.3a to make ext3 volumes

---

### Post by kingleer on 2008-02-07
Out of curiosity is reiserfs a good file system? Better than ext3?

---

### Post by mrsteveman1 on 2008-02-07
I might have missed something in all the links you posted above, but why is /dev/loop0 involved?

Shouldn't it be /dev/mapper/truecrypt0 or similar for the mapped TC device?

---

### Post by kingleer on 2008-02-07
> 

I might have missed something in all the links you posted above, but why is /dev/loop0 involved?

Shouldn't it be /dev/mapper/truecrypt0 or similar for the mapped TC device?
 


I think it's because I'm using truecrypt 5.0.  Maybe /dev/mapper/truecrypt0 is used in the earlier versions of truecrypt (4.3a) and that's what you're thinking off. I can only hypothesis though,because I'm not a linux expert and am using instructions I found in guides. :(

---

### Post by mrsteveman1 on 2008-02-07
Ahh ok, my server is still using 4.3a and i rarely even reboot it so i haven't yet upgraded.

I'll update it now so i can test it a bit.

edit: bah i'm not real happy about this switch to using FUSE in linux and OS X, but i suppose its for the best. Thats probably why its /dev/loop0 now, they aren't using the device mapper in linux anymore.

---

### Post by kingleer on 2008-02-07
> 
Ahh ok, my server is still using 4.3a and i rarely even reboot it so i haven't yet upgraded.

I'll update it now so i can test it a bit.

 

Thanks, I really appreciate all your help.

---

### Post by kingleer on 2008-02-07
> 

edit: bah i'm not real happy about this switch to using FUSE in linux and OS X, but i suppose its for the best. Thats probably why its /dev/loop0 now, they aren't using the device mapper in linux anymore.

 

I find the gui lacking. Why can't I just create fat, ntfs, ext3, ext2 partitions using the gui? All are integrated into ubuntu really well...

If you want to go back to 4.3a, I can upload the binaries.

---

### Post by mrsteveman1 on 2008-02-07
I've got copies of the various versions, in fact i have the source which is what i used to make my binaries.

I'm going to guess that the reason you can't make anything but FAT partitions in TC for linux and OS X is to keep things cross platform, IE users are going to have problems moving TC volumes between systems because of the filesystem even though TC is totally cross platform. Although, i really believe TC should just warn users and not omit the functionality entirely.

Linux has fairly good support for both NTFS and HFS+ but the reverse is not true, Windows has very poor support for both ext3 (Ext2IFS is mediocre), and HFS+ which is only available for-pay from macdrive.

OS X has support for ntfs-3g but it would mean 2 simultaneous uses of the FUSE system, one to map the device and another to mount ntfs-3g. I'm sure it would work but it gets complex. EXT3 is supported on OS X though with a separate driver.

I've not really missed the GUI on this linux server, i just wrote a bash script that checks the keys, does device checking and maps the devices, then mounts them afterward if they map right. It was the only way to make it efficient because they are all ext3 partitions.

---

### Post by kingleer on 2008-02-07
So, do you have any idea why I can't create an ext3 truecrypt partition, but have no trouble creating an reiserfs partition? :confused:

>  

OS X has support for ntfs-3g but it would mean 2 simultaneous uses of the FUSE system, one to map the device and another to mount ntfs-3g. I'm sure it would work but it gets complex. EXT3 is supported on OS X though with a separate driver.

 

The OS X version can't even create an HFS volume using the gui. I think all the versions should be able to create any volume their respective Operating systems can read and write to out of the box without additional drivers. I think the users would be smart enough to figure out what filesystem to use if they wanted their container to be crossplatform accessible.

---

### Post by mrsteveman1 on 2008-02-07
I'm going to test it out right now and sacrifice one of my unused drives to see what it does and see what i can find out about it. There are plenty of ways to debug stuff like this so it shouldn't be too difficult.

---

### Post by kingleer on 2008-02-07
Again thanks a lot.

---

### Post by mrsteveman1 on 2008-02-07
It now appears that the linux version of TC has also removed support for the commandline interface, which poses quite a problem on this headless server which has no display or even an installation of gnome or x11.

I'm gonna set up a test system to play around with it but it'll take a bit longer :D

---

### Post by kingleer on 2008-02-07
> 
I'm gonna set up a test system to play around with it but it'll take a bit longer
 

Take your time. I'm reading right now and checking this thread every ten minutes. 

Version 5 isn't ready for mainstream yet imo.

---

### Post by kingleer on 2008-02-08
AGAIN GO BACK TO 4.3a

---

### Post by shanepardue on 2008-02-08
I'm also experiencing the freeze and am interested in a fix as fat will not do. Thanks for having started this topic!

---

### Post by kingleer on 2008-02-08
I found a solution to my problem. Go back to 4.3a. 5 doesn't play nice with ubuntu. 

Anyway, I don't even really use truecrypt. I was just pissed when it wouldn't do what I told it to do, and thought I screwed up my install.

---

### Post by mrsteveman1 on 2008-02-09
I haven't been able to test things because of a disk problem (root on SSD acting funny), but i do know TC5 switched to using FUSE instead of a native kernel mode driver, so there could be problems because of it. 

The truecrypt forum is up right now so anyone having problems, make a thread in the linux section [here]("http://forums.truecrypt.org/viewforum.php?f=7").

You will need to register an account with a non-free email (yes i hate it too) but afterward you can start a thread and get some help, because this is very obviously a truecrypt problem and not an ubuntu problem.

---

### Post by shanepardue on 2008-02-11
> **mrsteveman1 said:**
> I haven't been able to test things because of a disk problem (root on SSD acting funny), but i do know TC5 switched to using FUSE instead of a native kernel mode driver, so there could be problems because of it. 

The truecrypt forum is up right now so anyone having problems, make a thread in the linux section [here]("http://forums.truecrypt.org/viewforum.php?f=7").

You will need to register an account with a non-free email (yes i hate it too) but afterward you can start a thread and get some help, because this is very obviously a truecrypt problem and not an ubuntu problem.
Here's the thread on their forums regarding this issue. 
[http://forums.truecrypt.org/viewtopic.php?p=39379#39379](http://forums.truecrypt.org/viewtopic.php?p=39379#39379)

Something to note: This problem doesn't arise in Hardy.

---

