---
title: "File System Usage...Now what?"
date: 2014-10-27
forum: General Help
---

### Post by pancho5 on 2014-10-27
Hello!

I am running LXLE on a non-pae laptop.  In viewing the attachment, now what should I do?

Pls advise.:?

---

### Post by TheFu on 2014-10-27
Nothing. Something. Anything?

Is there some problem or a specific question?

---

### Post by pancho5 on 2014-10-27
> **TheFu said:**
> Nothing. Something. Anything?

Is there some problem or a specific question?

Sorry!  Kind of paranoid right now.  No, I am not having a problem.  But, with the FS usage used up, what should I do?  I mean...I get OS updates weekly, and I don't have any other computer.  About two weeks ago, I removed all the games and it saved about 1GB.  

What if I reinstalled LXLE but without 3rd party apps?  Would that help?

---

### Post by TheFu on 2014-10-27
Relax. Here's the storage on my primary desktop:```

$ df
Filesystem                                                 Size  Used Avail Use% Mounted on
/dev/vda1                                                   14G   11G  1.5G  88% /
```

So - as long as you don't fill up the disk, I wouldn't worry.
All anyone running a normal *buntu desktop should have to do is explained here: 
  [http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

basically that comes down to 
* backups
* weekly updates/upgrades
If you have a separate /boot partition - don't let that fill up. After the fact - is too late.  If you have 1G free - relax.

What is using all that storage?  It isn't programs or the OS.  Find the movies/videos/music and delete those.

---

### Post by mörgæs on 2014-10-27
I wouldn't fill a disk more than 3/4, but besides that there is some good advice in the link. Thanks for posting.

---

### Post by TheFu on 2014-10-28
> **mörgæs said:**
> I wouldn't fill a disk more than 3/4, but besides that there is some good advice in the link. Thanks for posting.

Lifehacker.com republished it a few years ago, if that means anything. ;)

---

### Post by mastablasta on 2014-10-28
it's the data files taking up the space. move them to external disk. either USB stick or hard disk. depends on how much money you have. But external USB are now relatively cheap compared to flash disks. you get 500 GB external drive for 45 EUR here. I am sure it is cheaper elsewhere...

---

### Post by pancho5 on 2014-10-30
Okay everyone. I hate to sound like a broken record, but the following is just a little bit more information since my original posting.

I'm using the following disk space for the following: 791MB One movie (I can only upload one at a time); 154MB Document data; 53MB pictures.  The two attached files are my Disk Usage, and DF.

I have done what you have have suggested, installed system and application patches/updates.  Clean up old kernels.  Did a forcefsck.

By the way things are going, it seems like to me that I will run out of Filesystem space within 30-60 days.  Am I being realistic here?  If so, then what other suggestions one might consider?  Keep in mind, for now, I have an "extremely" low budget if anyone thinks I should acquire a newer LT.  I am unemployed.  

I do backup my data on a regular basis on to jump drives.

Any additional help would be much appreciated. [-o

---

### Post by mörgæs on 2014-10-30
> **pancho5 said:**
> I'm using the following disk space for the following: 791MB One movie (I can only upload one at a time); 154MB Document data; 53MB pictures. 

That's around 1 GB in total, and LXLE probably takes 3-4 GB. 

The 37 GB space on the disk is almost used. What takes up the remaining space? Is the trash bin full?

What is 'LT'?

---

### Post by Impavidus on 2014-10-30
Try to find which files and directories take all your disk space. This guide has some ideas on how to do that: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

The problem is not your programs taking too much space or your updates accumulating (provided you uninstall old kernels and occasionally clean the package cache). It could be an overflowing log file though.

---

### Post by pancho5 on 2014-10-31
> **mörgæs said:**
> That's around 1 GB in total, and LXLE probably takes 3-4 GB. 

The 37 GB space on the disk is almost used. What takes up the remaining space? Is the trash bin full?

What is 'LT'?

LT is Laptop.  I normally keep my trash bin empty, especially if I know I have a big file to eliminate.

---

### Post by pancho5 on 2014-10-31
> **Impavidus said:**
> Try to find which files and directories take all your disk space. This guide has some ideas on how to do that: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

The problem is not your programs taking too much space or your updates accumulating (provided you uninstall old kernels and occasionally clean the package cache). It could be an overflowing log file though.

Impavidus:

Thanks for the link.  Looks like I got some learnin' to read for a while!

---

### Post by mörgæs on 2014-10-31
Please post when you have found the explanation. It will help others in a similar situation.

---

### Post by carrington2 on 2014-10-31
i think you should clean cache file.

---

### Post by pancho5 on 2014-11-12
Thanks to Morgeas and others, I'm cautiously learning things about how to manage Ubuntu's Linux FS and Trash.  I issued a sudo find command on Trash, and the following attached files showed all my Trash folders (see attachments).  With that in mind, should I do gksudo on everyone of the Trash foler(s) periodically and delete them to free up space?

---

### Post by TheFu on 2014-11-12
Unused disk is a waste, just like unused RAM is a waste.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

Until there is less than 1-2G of space on a file system, I don't worry. Of course, this depends on the total size of the file system - so if a 4TB file system gets below 100G, I start to worry. Similarly, on a 15G file system, I don't worry until the last 500MB gets full.

Personally, I don't use GUI tools for file management, so I've never had to worry about trash. When a file is deleted, it is deleted.  Plus my backup job removes any temporary files nightly before running from the crontab. There are pros and cons to each method.

Seems to me that Trash should be automatically managed by the GUI, but I dunno if that is true.

---

