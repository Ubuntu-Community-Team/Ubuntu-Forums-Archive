---
title: "xubuntu, second HDD &amp; Plex"
date: 2020-02-04
forum: General Help
---

### Post by martyyyn on 2020-02-04
Hello

Context for my problem:
I have Xubuntu running primarily for the use as a Plex Server. It has two hard drives. I am a n00b. Thank you in advance for reading this.

Problem 1:
The plex server doesn't recognise any media or subfolders on the second hard drive ("sdb1") which mounts to "/media/[username]/Second HDD". 

Solution 1:
Having read a number of posts about this the problem might be related to read permissions for the second HDD. This solution seemed relevant to me:
[https://forums.plex.tv/t/problem-with-the-second-hard-drive-on-my-pc/118447/2](https://forums.plex.tv/t/problem-with-the-second-hard-drive-on-my-pc/118447/2)I
 The solution was to edit the file "/etc/fstab" with an additional line of code to remount the second HDD into a different location: "/plex/disk/"

The additional line would read "/dev/sdb1 /plex/disk auto defaults 0 0"


Problem 2:
The problem i'm having with "Solution 1" is that I cannot seem to edit the file "/etc/fstab". I've tried opening it as a text file, or launching a text editor (excuse me if i'm using the wrong terminology here) but it seems pretty sure it doesn't wan't to be edited... 

Solution 2: ???? (help!)



So... as you can see, I need your advice for a solution for problem 2, in order to solve problem 1. Unless of course you think the correct solution to problem 1 is different! I hope this made sense...

---

### Post by CelticWarrior on 2020-02-04
Solution 2 is quite simple actually.

You can use Disks to change the mount options:

[LIST=1]
[*]Select the drive/partition and click in the double cog wheel button > Edit mount options...
[*]De-select User session defaults
[*]Tick "mount at system startup"
[*]Keep the mount point as suggested, under /mnt
[*]Next choose the best option to identify it from the dropdown menu, usually LABEL= provides the more convenient and human readable way
[/LIST]

Reboot and test.

Plex, Emby and others do have a problem with drives mounted in /media but the reason for this eludes me.

---

### Post by martyyyn on 2020-02-04
Hi. Thanks for your reply! I'm 100% with you up until step 4.

If my understanding is correct I should make the mount point: /mnt/plex/disk/Second HDD  ?

So, I tried that and rebooted but nothing seems to have changed? The drive still appears on my desktop and does not appear under /plex/disk ?

Thanks again!

---

### Post by CelticWarrior on 2020-02-04
Keep the mount point as suggested but also avoid spaces if at all possible.

AFAIK it doesn't need to appear under /plex/disk to be recognized by Plex, the problem is when it's mounted at /media, the system default.

---

### Post by martyyyn on 2020-02-04
Okay Thanks!

I think I made a mistake and corrected the mount point to "[COLOR=#000000]/mnt/plex/disk" 

[/COLOR]Rebooted, it seems to have worked! Unfortunately... now i don't seem to have access to add files to the disk?

---

### Post by CelticWarrior on 2020-02-04
> **martyyyn said:**
> Unfortunately... now i don't seem to have access to add files to the disk?

And you could before? Changing the the mount point doesn't change permissions.

---

### Post by martyyyn on 2020-02-04
Yes - i've definitely moved stuff on and off the drive before

I've checked the properties of the folder /mnt/plex/disk and it is owned by "root (root)" and seems to be read only for everyone else.

---

### Post by CelticWarrior on 2020-02-04
Again, why did you changed it from the recommended mount point in Disks? You're only creating problems for yourself. This should have been as simple as I posted initially. The only thing needed was to avoid the system default /media and use /mnt instead, everything else staying the same (identify by LABEL is optional).

---

### Post by martyyyn on 2020-02-04
Ah. Yes misunderstood you twice. Sorry - I am in over my head here! I will use /mnt instead.

---

### Post by martyyyn on 2020-02-04
Okay I have retraced my steps and rebooted. It is correctly mounted at "/mnt"

However the drive doesn't let me add anything etc. It's essentially read only to me now. I can see everything that was in it before it was remounted - just a folder i'd named "test" for moving items back and forth into trying to get plex to recognise them.

---

### Post by martyyyn on 2020-02-04
I've moved the drive around to a different directory. The issue is that wherever it goes becomes owned by "root" rather than my username...

---

### Post by CelticWarrior on 2020-02-04
Is it under /mnt now?

---

### Post by ajgreeny on 2020-02-04
What filesystem is on the HDD #2?  I assume it must be a Linux filesystem, eg, ext4 if you can see ownership and permissions.

If files in your home are streamable by Plex have you tried mounting the HDD at some folder in your home. eg /home/username/plex, then make sure the mountpoint belongs to you.

---

### Post by TheFu on 2020-02-04
I've been running a plex server for years.  Some opinions:

File systems:
* Avoid NTFS. It causes issues and bad performance.
* Prefer a native Linux file system. If you don't have a specific reason to pick one, use EXT4.

Mount points and directories:
* No spaces in any paths.  EVER.  Spaces, funny characters like (){}[] or any shift+{num} just make hassles. Avoid.  Do it now.
* Review the **File System Hierarchy Standards** for where stuff should be mounted.  /media/ is for temporary mounts that automatically happen. This is a terrible place for plex data. /mnt/ is for admin use, like for a few hours as files are being recovered, not for permanent mounts.  Neither should be used for always connected storage. Google will find those standards easily. The wikipedia version is close enough.
* Plan ahead with storage.  I started with /D/, then /D2/, then /D3/, then /D4/.  Wish /D/ was /D1/ now.  
* Also, plan for backup storage.  I use /Backups/bD/ ... bD2 ... bD3 .. bD4.  Simple, clean, easy to understand what matches which primary storage.  I use USB3 storage for backups, but NEVER, EVER, for primary storage.  I have reasons.

Linux Permissions:
* Linux files and directories are multi-user as a core part of system security.  Linux file systems support this.  NTFS does not. Find any Unix permissions tutorial and spend the 45 minutes it takes to learn this stuff. Trivial issues like this one today would take 5 seconds to solve if you understood Unix file permissions. If you use a cell phone, tablet, or any other computers that aren't Windows, this permissions model is what those OSes use too. Hardly a waste of time.
* NTFS permissions can only be controlled at mount time through mount options. Same for owner and groups.  Permissions for all directories and files are the same for everything on that partition when mounted.  That kinda sucks.  Best to use ext4.

To edit system files, use **sudoedit**.

---

### Post by martyyyn on 2020-02-09
Thanks for your replies.

It was formatted something other than Ext4. I'm going to reformat and remount as suggested and see if that helps.

---

### Post by martyyyn on 2020-02-09
The good news is that the HDD is now formatted Ext4 and mounted under /D2/. 
I've also copied a movie onto it so no write/access issues. 

Unfortunatley Plex still can't see any subfolders or files on the drive :/

---

### Post by TheFu on 2020-02-09
What are the permissions for the different subdirectories under /D2/?  Plex has mandatory directory structures for TV, Movies, and Music.  The plex account must also have read access to the media files.  What I need to see is:
**ls -al /D2/**
Please use code tags, so everything lines up.

I'm assuming you added the different media directories to the Plex Server through the Plex web interface, of course.

---

### Post by martyyyn on 2020-02-16
```
martin@Moltres:~$ ls -al /D2/
total 28
drwx------  4 martin martin  4096 Feb  9 21:04 .
drwxr-xr-x 25 root   root    4096 Feb  9 21:48 ..
drwx------  2 root   root   16384 Feb  9 21:03 lost+found
drwxrwxrwx  4 martin martin  4096 Feb  9 21:36 StarWars4k

```

---

### Post by martyyyn on 2020-02-16
Update: @TheFU i took your advice and watched a youtube tutorial on unix permission, and gave relevant permissions so Plex can now see my folders and files. Thank you so much for all your help.

---

### Post by martyyyn on 2020-02-16
For other people with the same issue, my solution was granting read, write and execute permissions to the disk (D2) using the following command line code:

```

chmod o+r /D2/
chmod o+w /D2/
chmod o+x /D2/


```

---

### Post by TheFu on 2020-02-16
You have:
```
martin@Moltres:~$ ls -al /D2/
total 28
drwx------  4 martin martin  4096 Feb  9 21:04 .
drwxr-xr-x 25 root   root    4096 Feb  9 21:48 ..
drwx------  2 root   root   16384 Feb  9 21:03 lost+found
drwxrwxrwx  4 martin martin  4096 Feb  9 21:36 StarWars4k
```

You want:
```
martin@Moltres:~$ ls -al /D2/
total 28
drwxrw**s**r-x  4 martin **plex**  4096 Feb  9 21:04 .
drwxr-xr-x 25 root   root    4096 Feb  9 21:48 ..
drwx------  2 root   root   16384 Feb  9 21:03 lost+found
drwxrw**s**r-x  4 martin **plex**  4096 Feb  9 21:36 StarWars4k
```

Note the plex group, others don't have write and the setgid bit is set on all directories?  That will make any subdirs retain the same permissions AND the same group, plex.

Making the permissions 777 as shown, is almost always a terrible choice.  IMHO, it is a terrible choice for this purpose too.  Let me try to find a "working with others" post in these forums.  

Found one: [https://ubuntuforums.org/showthread.php?t=2382965&p=13731961#post13731961](https://ubuntuforums.org/showthread.php?t=2382965&p=13731961#post13731961)  in that post, "plex" should replace "ourgroup".

---

