---
title: "I did something wrong with 20.04]"
date: 2021-07-20
forum: General Help
---

### Post by Gnusboy on 2021-07-20
Hey all

In my effort to get my system working after the trouble I had with the suspicious file mentioned earlier
See [https://ubuntuforums.org/showthread.php?t=2464806](https://ubuntuforums.org/showthread.php?t=2464806)

I might have mucked up my file system and lost some important files. It appears that my main root filesystem has a lot wrong. I could sure use help to figure it all out.


The background to this is a mouse the kept freezing, then releasing, etc. but then locked up to the point of having to reboot to make it work. This problem led me to attempt a fix using FSCK. But I didn't read the part where I was supposed to do this from root w/o mounted file systems. I tried that twice and it then came back with "error code 2."
I tried to run fsck again, but then the system came back with the BusyBox v1.30.1 Initramfs errors. I read as much as I could on how to proceed, but didn't see any solution that I thought fit my situation.
Finally, I rebooted with the 20.04 live disk and to "Try Ubuntu" That brought up 2 partitions - one empty and the other with the file systems I had been using.
I checked on my documents - which seemed OK, but I'm not sure I still had all of them.
I don't recall exactly what I did then, but there was a banner showing 
Circle X Access with sys/device/software/subsystem/uevent denied
I hit OK and the banner closed
In the second partition (supposedly empty) There was a file labeled
 "Ubiquity Desktop"name:~desktop/ubiquity.desktop
2[read only] /run/network manager/devices

Failed to start shuts down pre-installed sys cleanly
SystemCTL i status Casper.service for detail
OK Reached Target Final step/finished powered-off
OK Finished reached target power off
[!!!!!!] Failed Execute shutdown binary [40985.213694] blk_update_request] I/O Error
Plus several similar lines.

Earlier today the screen was frozen and I did a soft reboot and got 
Begin: running/scripts/local-premount ... done
Begin: Will now check root file system ... fsck from util-linux 2.34 [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck,ext4 -a -C0 /dev/sda5 /dev/sda5 contains a file system with errors, check forced
[    10.326632] random: crng init done ==== \54.4% /dev/sda5:
Inode 35401772 extent tree (at level 1) could be shorter. IGNORED. /dev/sda5: Inodeds that were part of a corrupted orphan linked list found.
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -A OR -P OPTIONS
fsck exited with status code 4 done.
FAILURE: file system check of the root filesystem failed 
the root filesystem on /dev/sda5 requires a manual fsck

BusyBox /  
(initramfs)

Thanks

---

### Post by yancek on 2021-07-20
What happened when you did the manual fsck recommended?  Should be able to find lots of sites explaining how to do this on Linux/Ubuntu.

---

### Post by TheFu on 2021-07-20
To manually do an fsck, there are a few different ways.  In the boot menu, there's an "Advance .... " something on the list of kernels. Select that. Then pick one of the "Recovery Mode" choices.  That will boot a RAM-only environment and I think it brings up a blue/red screen with a menu of options.  One of the options is "Run fsck on all file systems" or perhaps "Check all file systems" - pick that.

The other easy way is to boot from any Ubuntu Desktop flavor ISO (usually a flash drive), go into "Try Ubuntu" mode, then open a terminal and run fsck manually on all the partitions and LVs with file systems.  Not all partitions will have file systems, so it would be good to know the size and device names of those that do.  Don't run fsck on any swap, for example.  Also, if you use LVM or chose an encrypted system at install time, then there are more details since the sda3 partition (the usual device where LVM stuff gets placed) doesn't have a file system to check.

If you get stuck, run 
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
inside the Live-Boot/Try Ubuntu environment and post the results here with the command AND results wrapped in code-tags. [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains code-tags.

---

### Post by Gnusboy on 2021-07-21
I didn't want to run an fsck until I was sure I wouldn't do the wrong thing. When I saw corrupted orphan and the root filesystem failed. etc. 
I have the 20.04 on a disk. So I start that until I get to Try Ubuntu, click that and let it load, run fsck. Right?
Is the recovery fsck on all filesystems, if that option is available, the same as running manual fsck individually?
Then I'll post whatever shows on the results, OK?
I only have 2 partitions on the drive and one of those is empty. I believe /dev/sda5 is where everything is inside.the so it should be pretty quit. My main concern is whether I have lost any documents. I have a lot of time and work sitting inside those 
files. 
BTW what is LVM?

---

### Post by TheFu on 2021-07-21
Try it. See what happens.   The maintenance mode version takes the guesswork away, so that would be much easier for most people to use.

If you are worried about lost documents, then clearly your backup process needs work. Fix that ASAP.

---

### Post by Gnusboy on 2021-07-23
Yeah, I'm always behind on backups. Until recently, I backup most of my work on an external drive. I disconnected it a couple of months ago - I don't recall why.  I may have paid the price for that. 
Given the status of my current system, is there a way to copy my existing files over to the external drive?
Or, do I need to wait it out until its repaired?

I didn't want to run an fsck until I was sure I wouldn't do the wrong  thing. When I saw corrupted orphan and the root filesystem failed. etc. 

I have the 20.04 on a disk. So I start that until I get to Try Ubuntu, click that and let it load, run fsck. Right?
Is the recovery fsck on all filesystems, if that option is available, the same as running manual fsck individually?
Then I'll post whatever shows on the results, OK?
I only have 2 partitions on the drive and one of those is empty. I  believe /dev/sda5 is where everything is inside.the so it should be  pretty quit. My main concern is whether I have lost any documents. I  have a lot of time and work sitting inside those 
files. 
BTW what is LVM?

OK.As soon as I hit EXIT from initramfs, it ran  fsck manually on the root file system, it showed [/user/sbin/fsck.ext4  (1) --/dev/dev/sda5]  fsck.ext4 -a -CO ./dev/sda5 contains the file  system with errors, check forced.
I will let you know what happens.
And thank you for your help.

---

### Post by ActionParsnip on 2021-07-23
If your documents are important... You have made a backup of them.... Right?

---

### Post by TheFu on 2021-07-23
If you get stuck, run the command in #3 above and post the outputs.  Then we can easily tell if you need to care about LVM or not.  Either you have it or your don't.  Most of the time, people would absolutely KNOW they picked to use LVM for storage management.  But sometimes people don't read the monitor and get it without understanding.  

I bet there's a wikipedia article on LVM if you want an overview.  In LVM, partitions aren't where file systems get placed, so you will see partitions, but won't be able to click to open them directly.

I like LVM for flexibility. But it does add some complexity to storage management. Most people who don't do enterprise storage would probably not choose LVM. However, in the Ubuntu installers, if encrypted storage is picked, then they use LVM as well. This isn't mandatory, but it is smart, IMHO.

---

### Post by Gnusboy on 2021-07-23
thanks for getting rid of those extra paragraphs. I didn't see them until later.

---

### Post by Gnusboy on 2021-07-23
The difference between, I know I should, and yeah I did, is vast. 
I kept having problems with Deja-Dup. Sometimes it worked and other times not. I kept telling myself to get a different
backup program, but it was a low priority. However,  when I get my system back up, I'll get one asap
I did have some backups. I don't recall from when.
 So if I don't have the most recent, I can probably rework them.

---

### Post by Gnusboy on 2021-07-23
I was able to get to get into fsck. I did a soft reboot, found the recovery mode and booted into it.
The results are what I posted a few minutes ago.
The fsck output I did seems very short and limited to sda5.  There is a second partition, but I didn't use it. I planned on using it for my most important files.
I also have a 1 TB external drive that I used for important stuff. For some reason I disconnected it a month or two ago. 
My old brain is filled with "I was gonna ... "

---

### Post by ActionParsnip on 2021-07-24
Try an fsck from live CD / USB. You don't need to use a fancy backup software to make a backup. Just copy import data to another drive (preferably external) or external storage system when you need to. I use a cron'd cp command which runs weekly. It's crude but absolutely works.

---

### Post by TheFu on 2021-07-24
> **ActionParsnip said:**
> Try an fsck from live CD / USB. You don't need to use a fancy backup software to make a backup. Just copy import data to another drive (preferably external) or external storage system when you need to. I use a cron'd cp command which runs weekly. It's crude but absolutely works.

For most end-user data, this is absolutely, 100%, truth.  Only a small number of exceptions exist. Cannot say whether any user would be impacted or not. If they use ssh, scp, sftp, rsync, or any of the 50 other ssh-based connection tools, then the answer is likely yes and a cp will break those.

For some end-user files in $HOME, a cp to NTFS will drop the permissions, so at restore time, things will be broke.

For all system files, cp will drop owner, group, permissions, and probably miss some files do to access which prevents end-users from access - even if native Linux file systems are on the target disk.

Having 1 copy, no versions, of files is about 80% of what we need backups for.  But if you can script a cp to run weekly, then you can script an rsync, which will be much quicker.  And if you can script an rsync, you've just gotten to where scripting rdiff-backup is basically the same thing, for an single end-user.

```
# a cp backup script:
cp -rp  $HOME /mnt/backup/

# a simple rsync backup script:
rsync -avz  $HOME /mnt/backup/

# an simple, single-user, rdiff-backup script w/ 90days of versioned backups (if run daily):
rdiff-backup  --exclude-special-files  $HOME /mnt/backup/
rdiff-backup --remove-older-than 90d --force /mnt/backup/
```

The first 2 scripts create a single copy and always add new files, never delete old files. That can be a problem.
The rdiff-backup will create versioned backups, efficiently.  The 2nd - 90th runs will be faster than rsync. You'll have 90d of versioned backups, probably using 1.3x the original amount of storage.  Say your $HOME has 20G, then the 90 days of backups will have about 26G.  Seems like a bargain to me.  The --force option is there to remove all the backups made 90 days ago, even if we did 5 backups in 1 day.

All the scripts aren't too careful in excluding files that nobody needs in their backups. Things like Firefox or Chromium cache files, for example. Best to start and get too much than not enough.
All of those backup methods above create a mirror directory system, so to restore the last backup made we don't need any fancy tools. cp or nautilus or caja or any other file manager can be used - that includes the rdiff-backup areas.  Just don't change any files or directories manually in the /mnt/backup/.   Checksums for each file/directory are maintained. Wouldn't want to break those.

**Anyway, good, versioned, backups of a single end-user's data aren't really THAT hard.**

System backups require more thought and must be run as root/sudo to have access to protected files. What needs to be included and what absolutely must be excluded is a little different too. In rdiff-backup, the  --exclude-special-files option prevents trying to backup a fifo, named pipe, or other special device files that would always provide never-ending data.  rsync has options for that too - rsync has hundreds of options.

---

### Post by Gnusboy on 2021-07-24
It looks like the output from the fsck I ran did not post where I  expected. I thought it would show as a response to THE FU's  recommendations. 

 When I looked through the fsck output, there  are a couple of things look important. I'm not sure how they affect  restoring my system. 

"Inodes that were part of a corrupted  orphan linked list found"

"/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck manually"

"Failure: File system check of the root filesystem failed."


The total readable output of the test is only 16 lines. Is that a usual result of a fsck?

There were lines of data that scrolled down the monitor too fast for me to read. I'm looking for a way to stop the scroll.
 At the bottom, all I could see was 16 lines. I couldn't page up to see  what they were and I might have missed something in the readout. 

I did the fsck from a soft reboot of 20.04
There were 4 kernels listed; the first was a generic OS and the next was a recovery mode, which is what I used.
Is there another fsck that would return different information?
When  the output stopped scrolling, there were 16 lines showing on the  screen. I don't know if what is visible is on the screen is everything  that's important.

Here's the viewable output:

Begin: running/scripts/local-premount ... done.
Begin: mounting root file system ... Begin: Running /scripts/local-top ...Done.
 Begin: Running /scripts/local-premount...Done.
Begin: Will now check root file system ... fsck from util-linux 2.34  
         [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck.ext4 -a -C0 /dev/sda5  
         /dev/sda5 contains a file system with errors, check forced.
[ 6.959270] random: crng init done ==== \54.9% 
/dev/sda5:
Inode 35401772 extent tree (at level 1) could be shorter. IGNORED.  /dev/sda5: Inodes that were part of a corrupted orphan linked list  found.
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -a OR -p OPTIONS
fsck exited with status code 4 done.
FAILURE: file system check of the root filesystem failed 
the root filesystem on /dev/sda5 requires a manual fsck

BusyBox /  
(initramfs)


Looking through the comments y'all were good enough to help me with,
I see the recommendations on how to do backups, which I need, but don't I have
to restore the operation of my system first?

Thank you all

---

### Post by Gnusboy on 2021-07-24
Uh, FU
Can you repeat that in ancient Greek? I might understand it better.

---

### Post by TheFu on 2021-07-24
> **Gnusboy said:**
> Uh, FU
Can you repeat that in ancient Greek? I might understand it better.
I'll try.  I don't speak Greek, so it is probably a little off. ;)   This is an English forum. If you really need Greek, there's probably a Greek language forum.

&#942; &#964;&#945; &#960;&#949;&#961;&#953;&#963;&#963;&#972;&#964;&#949;&#961;&#945; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#945; &#964;&#949;&#955;&#953;&#954;&#974;&#957; &#967;&#961;&#951;&#963;&#964;&#974;&#957;, &#945;&#965;&#964;&#972; &#949;&#943;&#957;&#945;&#953; &#945;&#960;&#959;&#955;&#973;&#964;&#969;&#962;, 100%, &#945;&#955;&#942;&#952;&#949;&#953;&#945;. &#933;&#960;&#940;&#961;&#967;&#949;&#953; &#956;&#972;&#957;&#959; &#941;&#957;&#945;&#962; &#956;&#953;&#954;&#961;&#972;&#962; &#945;&#961;&#953;&#952;&#956;&#972;&#962; &#949;&#958;&#945;&#953;&#961;&#941;&#963;&#949;&#969;&#957;. &#916;&#949;&#957; &#956;&#960;&#959;&#961;&#974; &#957;&#945; &#960;&#969; &#945;&#957; &#954;&#940;&#960;&#959;&#953;&#959;&#962; &#967;&#961;&#942;&#963;&#964;&#951;&#962; &#952;&#945; &#949;&#960;&#951;&#961;&#949;&#945;&#963;&#964;&#949;&#943; &#942; &#972;&#967;&#953;. &#917;&#940;&#957; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#959;&#973;&#957; ssh, scp, sftp, rsync &#942; &#959;&#960;&#959;&#953;&#959;&#948;&#942;&#960;&#959;&#964;&#949; &#945;&#960;&#972; &#964;&#945; 50 &#940;&#955;&#955;&#945; &#949;&#961;&#947;&#945;&#955;&#949;&#943;&#945; &#963;&#973;&#957;&#948;&#949;&#963;&#951;&#962; &#960;&#959;&#965; &#946;&#945;&#963;&#943;&#950;&#959;&#957;&#964;&#945;&#953; &#963;&#949; ssh, &#964;&#972;&#964;&#949; &#951; &#945;&#960;&#940;&#957;&#964;&#951;&#963;&#951; &#949;&#943;&#957;&#945;&#953; &#960;&#953;&#952;&#945;&#957;&#972; &#957;&#945;&#953; &#954;&#945;&#953; &#941;&#957;&#945; cp &#952;&#945; &#964;&#945; &#963;&#960;&#940;&#963;&#949;&#953;.

&#915;&#953;&#945; &#959;&#961;&#953;&#963;&#956;&#941;&#957;&#945; &#945;&#961;&#967;&#949;&#943;&#945; &#964;&#949;&#955;&#953;&#954;&#959;&#973; &#967;&#961;&#942;&#963;&#964;&#951; &#963;&#964;&#959; $ HOME, &#941;&#957;&#945; cp &#963;&#964;&#959; NTFS &#952;&#945; &#945;&#966;&#942;&#963;&#949;&#953; &#964;&#945; &#948;&#953;&#954;&#945;&#953;&#974;&#956;&#945;&#964;&#945;, &#959;&#960;&#972;&#964;&#949; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#945;&#957;&#945;&#966;&#959;&#961;&#940;, &#964;&#945; &#960;&#961;&#940;&#947;&#956;&#945;&#964;&#945; &#952;&#945; &#967;&#945;&#955;&#940;&#963;&#959;&#965;&#957;.

&#915;&#953;&#945; &#972;&#955;&#945; &#964;&#945; &#945;&#961;&#967;&#949;&#943;&#945; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962;, &#964;&#959; cp &#952;&#945; &#945;&#966;&#942;&#963;&#949;&#953; &#964;&#959;&#957; &#954;&#940;&#964;&#959;&#967;&#959;, &#964;&#951;&#957; &#959;&#956;&#940;&#948;&#945;, &#964;&#945; &#948;&#953;&#954;&#945;&#953;&#974;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#960;&#953;&#952;&#945;&#957;&#974;&#962; &#952;&#945; &#967;&#940;&#963;&#949;&#953; &#954;&#940;&#960;&#959;&#953;&#945; &#945;&#961;&#967;&#949;&#943;&#945; &#960;&#959;&#965; &#952;&#945; &#941;&#967;&#959;&#965;&#957; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;, &#947;&#949;&#947;&#959;&#957;&#972;&#962; &#960;&#959;&#965; &#949;&#956;&#960;&#959;&#948;&#943;&#950;&#949;&#953; &#964;&#951;&#957; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951; &#964;&#969;&#957; &#964;&#949;&#955;&#953;&#954;&#974;&#957; &#967;&#961;&#951;&#963;&#964;&#974;&#957; - &#945;&#954;&#972;&#956;&#945; &#954;&#945;&#953; &#945;&#957; &#964;&#945; &#949;&#947;&#947;&#949;&#957;&#942; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#945; &#945;&#961;&#967;&#949;&#943;&#969;&#957; Linux &#946;&#961;&#943;&#963;&#954;&#959;&#957;&#964;&#945;&#953; &#963;&#964;&#959; &#948;&#943;&#963;&#954;&#959; &#960;&#961;&#959;&#959;&#961;&#953;&#963;&#956;&#959;&#973;.

&#904;&#967;&#959;&#957;&#964;&#945;&#962; 1 &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#959;, &#967;&#969;&#961;&#943;&#962; &#949;&#954;&#948;&#972;&#963;&#949;&#953;&#962;, &#964;&#969;&#957; &#945;&#961;&#967;&#949;&#943;&#969;&#957; &#949;&#943;&#957;&#945;&#953; &#960;&#949;&#961;&#943;&#960;&#959;&#965; &#964;&#959; 80% &#945;&#965;&#964;&#959;&#973; &#960;&#959;&#965; &#967;&#961;&#949;&#953;&#945;&#950;&#972;&#956;&#945;&#963;&#964;&#949; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962;. &#913;&#955;&#955;&#940; &#945;&#957; &#956;&#960;&#959;&#961;&#949;&#943;&#964;&#949; &#957;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#942;&#963;&#949;&#964;&#949; &#963;&#949;&#957;&#940;&#961;&#953;&#959; &#941;&#957;&#945; cp &#947;&#953;&#945; &#957;&#945; &#949;&#954;&#964;&#949;&#955;&#949;&#943;&#964;&#945;&#953; &#949;&#946;&#948;&#959;&#956;&#945;&#948;&#953;&#945;&#943;&#945;, &#964;&#972;&#964;&#949; &#956;&#960;&#959;&#961;&#949;&#943;&#964;&#949; &#957;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#942;&#963;&#949;&#964;&#949; &#963;&#949;&#957;&#940;&#961;&#953;&#959; &#941;&#957;&#945; rsync, &#964;&#959; &#959;&#960;&#959;&#943;&#959; &#952;&#945; &#949;&#943;&#957;&#945;&#953; &#960;&#959;&#955;&#973; &#960;&#953;&#959; &#947;&#961;&#942;&#947;&#959;&#961;&#959;. &#922;&#945;&#953; &#945;&#957; &#956;&#960;&#959;&#961;&#949;&#943;&#964;&#949; &#957;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#942;&#963;&#949;&#964;&#949; &#963;&#949;&#957;&#940;&#961;&#953;&#959; &#941;&#957;&#945; rsync, &#956;&#972;&#955;&#953;&#962; &#966;&#964;&#940;&#963;&#945;&#964;&#949; &#963;&#964;&#959; &#963;&#951;&#956;&#949;&#943;&#959; &#972;&#960;&#959;&#965; &#964;&#959; scripting rdiff-backup &#949;&#943;&#957;&#945;&#953; &#946;&#945;&#963;&#953;&#954;&#940; &#964;&#959; &#943;&#948;&#953;&#959; &#960;&#961;&#940;&#947;&#956;&#945;, &#947;&#953;&#945; &#941;&#957;&#945;&#957; &#956;&#972;&#957;&#959; &#964;&#949;&#955;&#953;&#954;&#972; &#967;&#961;&#942;&#963;&#964;&#951;.

```

# &#949;&#966;&#949;&#948;&#961;&#953;&#954;&#972; &#963;&#949;&#957;&#940;&#961;&#953;&#959; cp:
cp -rp $HOME /mnt/backup/

# &#941;&#957;&#945; &#945;&#960;&#955;&#972; &#949;&#966;&#949;&#948;&#961;&#953;&#954;&#972; &#963;&#949;&#957;&#940;&#961;&#953;&#959; rsync:
rsync -avz $HOME /mnt/&#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#959; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962;/

# &#941;&#957;&#945; &#945;&#960;&#955;&#972; &#963;&#949;&#957;&#940;&#961;&#953;&#959; &#949;&#957;&#972;&#962; &#967;&#961;&#942;&#963;&#964;&#951;, rdiff-backup &#956;&#949; 90 &#951;&#956;&#941;&#961;&#949;&#962; &#949;&#954;&#948;&#972;&#963;&#949;&#969;&#957; (&#949;&#940;&#957; &#949;&#954;&#964;&#949;&#955;&#959;&#973;&#957;&#964;&#945;&#953; &#954;&#945;&#952;&#951;&#956;&#949;&#961;&#953;&#957;&#940;):
rdiff-backup --exclude-special-files $ HOME   /mnt/backup/
rdiff-backup - Remove-old-than 90d --force   /mnt/backup/
```

&#932;&#945; &#960;&#961;&#974;&#964;&#945; 2 &#963;&#949;&#957;&#940;&#961;&#953;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#959;&#973;&#957; &#941;&#957;&#945; &#956;&#972;&#957;&#959; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#959; &#954;&#945;&#953; &#960;&#961;&#959;&#963;&#952;&#941;&#964;&#959;&#965;&#957; &#960;&#940;&#957;&#964;&#945; &#957;&#941;&#945; &#945;&#961;&#967;&#949;&#943;&#945;, &#956;&#951;&#957; &#948;&#953;&#945;&#947;&#961;&#940;&#966;&#949;&#964;&#949; &#960;&#959;&#964;&#941; &#960;&#945;&#955;&#953;&#940; &#945;&#961;&#967;&#949;&#943;&#945;. &#913;&#965;&#964;&#972; &#956;&#960;&#959;&#961;&#949;&#943; &#957;&#945; &#949;&#943;&#957;&#945;&#953; &#941;&#957;&#945; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945;.
&#932;&#959; rdiff-backup &#952;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#942;&#963;&#949;&#953; &#945;&#960;&#959;&#964;&#949;&#955;&#949;&#963;&#956;&#945;&#964;&#953;&#954;&#940; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962;. &#932;&#959; 2&#959; - 90&#959; &#964;&#961;&#941;&#958;&#953;&#956;&#959; &#952;&#945; &#949;&#943;&#957;&#945;&#953; &#960;&#953;&#959; &#947;&#961;&#942;&#947;&#959;&#961;&#959; &#945;&#960;&#972; &#964;&#959; rsync. &#920;&#945; &#941;&#967;&#949;&#964;&#949; 90d &#949;&#966;&#949;&#948;&#961;&#953;&#954;&#974;&#957; &#945;&#957;&#964;&#953;&#947;&#961;&#940;&#966;&#969;&#957; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962;, &#960;&#953;&#952;&#945;&#957;&#972;&#964;&#945;&#964;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; 1,3 &#966;&#959;&#961;&#941;&#962; &#964;&#959;&#957; &#945;&#961;&#967;&#953;&#954;&#972; &#945;&#960;&#959;&#952;&#951;&#954;&#949;&#965;&#964;&#953;&#954;&#972; &#967;&#974;&#961;&#959;. &#913;&#962; &#965;&#960;&#959;&#952;&#941;&#963;&#959;&#965;&#956;&#949; &#972;&#964;&#953; &#964;&#959; $ HOME &#963;&#945;&#962; &#941;&#967;&#949;&#953; 20G &#954;&#945;&#953;, &#963;&#964;&#951; &#963;&#965;&#957;&#941;&#967;&#949;&#953;&#945;, &#964;&#945; &#949;&#966;&#949;&#948;&#961;&#953;&#954;&#940; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#964;&#969;&#957; 90 &#951;&#956;&#949;&#961;&#974;&#957; &#952;&#945; &#941;&#967;&#959;&#965;&#957; &#960;&#949;&#961;&#943;&#960;&#959;&#965; 26G. &#934;&#945;&#943;&#957;&#949;&#964;&#945;&#953; &#963;&#945;&#957; &#956;&#953;&#945; &#963;&#965;&#956;&#966;&#969;&#957;&#943;&#945; &#947;&#953;&#945; &#956;&#941;&#957;&#945;. &#919; &#949;&#960;&#953;&#955;&#959;&#947;&#942; --force &#949;&#943;&#957;&#945;&#953; &#949;&#954;&#949;&#943; &#947;&#953;&#945; &#957;&#945; &#954;&#945;&#964;&#945;&#961;&#947;&#942;&#963;&#949;&#964;&#949; &#972;&#955;&#945; &#964;&#945; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#960;&#959;&#965; &#941;&#947;&#953;&#957;&#945;&#957; &#960;&#961;&#953;&#957; &#945;&#960;&#972; 90 &#951;&#956;&#941;&#961;&#949;&#962;, &#945;&#954;&#972;&#956;&#945; &#954;&#953; &#945;&#957; &#954;&#940;&#957;&#945;&#956;&#949; 5 &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#963;&#949; 1 &#951;&#956;&#941;&#961;&#945;.

&#908;&#955;&#945; &#964;&#945; &#963;&#949;&#957;&#940;&#961;&#953;&#945; &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#960;&#959;&#955;&#973; &#960;&#961;&#959;&#963;&#949;&#954;&#964;&#953;&#954;&#940; &#949;&#958;&#945;&#953;&#961;&#974;&#957;&#964;&#945;&#962; &#945;&#961;&#967;&#949;&#943;&#945; &#960;&#959;&#965; &#954;&#945;&#957;&#949;&#943;&#962; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#963;&#964;&#945; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#964;&#959;&#965;. &#915;&#953;&#945; &#960;&#945;&#961;&#940;&#948;&#949;&#953;&#947;&#956;&#945;, &#972;&#960;&#969;&#962; Firefox &#942; Chromium cache &#945;&#961;&#967;&#949;&#943;&#945;. &#922;&#945;&#955;&#973;&#964;&#949;&#961;&#945; &#957;&#945; &#958;&#949;&#954;&#953;&#957;&#942;&#963;&#949;&#964;&#949; &#954;&#945;&#953; &#957;&#945; &#960;&#940;&#961;&#949;&#964;&#949; &#960;&#940;&#961;&#945; &#960;&#959;&#955;&#955;&#940; &#945;&#960;&#972; &#972;, &#964;&#953; &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#945;&#961;&#954;&#949;&#964;&#972;.
&#908;&#955;&#949;&#962; &#945;&#965;&#964;&#941;&#962; &#959;&#953; &#960;&#945;&#961;&#945;&#960;&#940;&#957;&#969; &#956;&#941;&#952;&#959;&#948;&#959;&#953; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945;&#962; &#945;&#957;&#964;&#953;&#947;&#961;&#940;&#966;&#969;&#957; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#959;&#973;&#957; &#941;&#957;&#945; &#963;&#973;&#963;&#964;&#951;&#956;&#945; &#954;&#945;&#964;&#945;&#955;&#972;&#947;&#959;&#965; &#954;&#945;&#952;&#961;&#949;&#966;&#964;&#974;&#957;, &#959;&#960;&#972;&#964;&#949; &#947;&#953;&#945; &#964;&#951;&#957; &#949;&#960;&#945;&#957;&#945;&#966;&#959;&#961;&#940; &#964;&#959;&#965; &#964;&#949;&#955;&#949;&#965;&#964;&#945;&#943;&#959;&#965; &#945;&#957;&#964;&#953;&#947;&#961;&#940;&#966;&#959;&#965; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#945;&#950;&#972;&#956;&#945;&#963;&#964;&#949; &#954;&#945;&#957;&#941;&#957;&#945; &#966;&#945;&#957;&#964;&#945;&#967;&#964;&#949;&#961;&#972; &#949;&#961;&#947;&#945;&#955;&#949;&#943;&#959; cp &#942; nautilus &#942; caja &#942; &#959;&#960;&#959;&#953;&#959;&#963;&#948;&#942;&#960;&#959;&#964;&#949; &#940;&#955;&#955;&#959;&#962; &#948;&#953;&#945;&#967;&#949;&#953;&#961;&#953;&#963;&#964;&#942;&#962; &#945;&#961;&#967;&#949;&#943;&#969;&#957; &#956;&#960;&#959;&#961;&#949;&#943; &#957;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#949;&#943; - &#960;&#959;&#965; &#960;&#949;&#961;&#953;&#955;&#945;&#956;&#946;&#940;&#957;&#949;&#953; &#964;&#953;&#962; &#960;&#949;&#961;&#953;&#959;&#967;&#941;&#962; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945;&#962; &#945;&#957;&#964;&#953;&#947;&#961;&#940;&#966;&#969;&#957; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; rdiff. &#913;&#960;&#955;&#974;&#962; &#956;&#951;&#957; &#945;&#955;&#955;&#940;&#950;&#949;&#964;&#949; &#967;&#949;&#953;&#961;&#959;&#954;&#943;&#957;&#951;&#964;&#945; &#945;&#961;&#967;&#949;&#943;&#945; &#942; &#954;&#945;&#964;&#945;&#955;&#972;&#947;&#959;&#965;&#962; &#963;&#964;&#959; / mnt / backup /. &#932;&#945; Checksums &#947;&#953;&#945; &#954;&#940;&#952;&#949; &#945;&#961;&#967;&#949;&#943;&#959; / &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959; &#948;&#953;&#945;&#964;&#951;&#961;&#959;&#973;&#957;&#964;&#945;&#953;. &#916;&#949;&#957; &#952;&#945; &#942;&#952;&#949;&#955;&#945; &#957;&#945; &#964;&#945; &#963;&#960;&#940;&#963;&#969;.

&#932;&#941;&#955;&#959;&#962; &#960;&#940;&#957;&#964;&#969;&#957;, &#964;&#945; &#954;&#945;&#955;&#940;, &#949;&#954;&#948;&#959;&#956;&#941;&#957;&#945;, &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#964;&#969;&#957; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; &#949;&#957;&#972;&#962; &#956;&#949;&#956;&#959;&#957;&#969;&#956;&#941;&#957;&#959;&#965; &#964;&#949;&#955;&#953;&#954;&#959;&#973; &#967;&#961;&#942;&#963;&#964;&#951; &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#960;&#961;&#945;&#947;&#956;&#945;&#964;&#953;&#954;&#940; &#964;&#972;&#963;&#959; &#948;&#973;&#963;&#954;&#959;&#955;&#945;.

&#932;&#945; &#945;&#957;&#964;&#943;&#947;&#961;&#945;&#966;&#945; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#964;&#959;&#965; &#963;&#965;&#963;&#964;&#942;&#956;&#945;&#964;&#959;&#962; &#945;&#960;&#945;&#953;&#964;&#959;&#973;&#957; &#960;&#949;&#961;&#953;&#963;&#963;&#972;&#964;&#949;&#961;&#951; &#963;&#954;&#941;&#968;&#951; &#954;&#945;&#953; &#960;&#961;&#941;&#960;&#949;&#953; &#957;&#945; &#949;&#954;&#964;&#949;&#955;&#959;&#973;&#957;&#964;&#945;&#953; &#969;&#962; root / sudo &#947;&#953;&#945; &#957;&#945; &#941;&#967;&#959;&#965;&#957; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951; &#963;&#949; &#960;&#961;&#959;&#963;&#964;&#945;&#964;&#949;&#965;&#956;&#941;&#957;&#945; &#945;&#961;&#967;&#949;&#943;&#945;. &#913;&#965;&#964;&#972; &#960;&#959;&#965; &#960;&#961;&#941;&#960;&#949;&#953; &#957;&#945; &#963;&#965;&#956;&#960;&#949;&#961;&#953;&#955;&#951;&#966;&#952;&#949;&#943; &#954;&#945;&#953; &#945;&#965;&#964;&#972; &#960;&#959;&#965; &#960;&#961;&#941;&#960;&#949;&#953; &#957;&#945; &#945;&#960;&#959;&#954;&#955;&#949;&#953;&#963;&#964;&#949;&#943; &#949;&#943;&#957;&#945;&#953; &#955;&#943;&#947;&#959; &#948;&#953;&#945;&#966;&#959;&#961;&#949;&#964;&#953;&#954;&#972;. &#931;&#964;&#959; rdiff-backup, &#951; &#949;&#960;&#953;&#955;&#959;&#947;&#942; --exclude-special-files &#945;&#960;&#959;&#964;&#961;&#941;&#960;&#949;&#953; &#964;&#951;&#957; &#960;&#961;&#959;&#963;&#960;&#940;&#952;&#949;&#953;&#945; &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#943;&#945;&#962; &#945;&#957;&#964;&#953;&#947;&#961;&#940;&#966;&#969;&#957; &#945;&#963;&#966;&#945;&#955;&#949;&#943;&#945;&#962; &#949;&#957;&#972;&#962; fifo, &#959;&#957;&#959;&#956;&#945;&#963;&#956;&#941;&#957;&#959;&#965; &#963;&#969;&#955;&#942;&#957;&#945; &#942; &#940;&#955;&#955;&#969;&#957; &#949;&#953;&#948;&#953;&#954;&#974;&#957; &#945;&#961;&#967;&#949;&#943;&#969;&#957; &#963;&#965;&#963;&#954;&#949;&#965;&#974;&#957; &#960;&#959;&#965; &#952;&#945; &#960;&#945;&#961;&#941;&#967;&#959;&#965;&#957; &#960;&#940;&#957;&#964;&#945; &#945;&#964;&#949;&#955;&#949;&#943;&#969;&#964;&#945; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#945;. &#932;&#959; rsync &#941;&#967;&#949;&#953; &#949;&#960;&#953;&#955;&#959;&#947;&#941;&#962; &#947;&#953;&#945; &#945;&#965;&#964;&#972; - rsync &#941;&#967;&#949;&#953; &#949;&#954;&#945;&#964;&#959;&#957;&#964;&#940;&#948;&#949;&#962; &#949;&#960;&#953;&#955;&#959;&#947;&#941;&#962;.

---

### Post by Gnusboy on 2021-07-25
It looks like the output from the fsck I ran did not post where I expected. I thought it would show as a response to THE FU's recommendations. 

 When I looked through the fsck output, there are a couple of things look important. I'm not sure how they affect restoring my system. 

"Inodes that were part of a corrupted  orphan linked list found"

"/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck manually"

"Failure: File system check of the root filesystem failed."


The total readable output of the test is only 16 lines. Is that a usual result of a fsck?

There were lines of data that scrolled down the monitor too fast for me to read. I'm looking for a way to stop the scroll.
 At the bottom, all I could see was 16 lines. I couldn't page up to see what they were and I might have missed something in the readout. 

I did the fsck from a soft reboot of 20.04
There were 4 kernels listed; the first was a generic OS and the next was a recovery mode, which is what I used.
Is there another fsck that would return different information?
When the output stopped scrolling, there were 16 lines showing on the screen. I don't know if what is visible is on the screen is everything that's important.

Here's the viewable output:

Begin: running/scripts/local-premount ... done.
Begin: mounting root file system ... Begin: Running /scripts/local-top ...Done.
 Begin: Running /scripts/local-premount...Done.
Begin: Will now check root file system ... fsck from util-linux 2.34  
         [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck.ext4 -a -C0 /dev/sda5  
         /dev/sda5 contains a file system with errors, check forced.
[ 6.959270] random: crng init done ==== \54.9% 
/dev/sda5:
Inode 35401772 extent tree (at level 1) could be shorter. IGNORED.  /dev/sda5: Inodes that were part of a corrupted orphan linked list  found.
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -a OR -p OPTIONS
fsck exited with status code 4 done.
FAILURE: file system check of the root filesystem failed 
the root filesystem on /dev/sda5 requires a manual fsck

BusyBox /  
(initramfs)


Looking through the comments y'all were good enough to help me with,
I see the recommendations on how to do backups, which I need, but don't I have
to restore the operation of my system first?

Thank you all

---

### Post by Gnusboy on 2021-07-25
I'm a little rusty. I'll have to break out my old stone tablets

---

### Post by tea for one on 2021-07-25
@TheFu

 Post 16 - Classic reply but somewhat Spartan ;)

---

### Post by Gnusboy on 2021-07-26
This is a little known tale of war. To the victors go the spoils.

After the last skirmish between Sparta and Troy, exhausted Spartans, backs turned in defeat, were captured before the trek home.
Seeing  an undefended opening in the ranks, the Trojan's took hold of their  spears, sheathed themselves tightly in armor and then lunged forcefully,  penetrating again and again, deeply into the Spartan ranks. The Trojan  warriors, formerly engorged with hard fought victory, felt their initial  stiffness flagging. With the battleground awash with the spoils of war,  each of them finally dropped onto the spoils of war to sleep.

---

### Post by Gnusboy on 2021-07-26
I booted from the 20.04 disk and the full system check came up with no errors.

I'm currently logged in with the live disk. If reboot without it should I do another fsck? 
Are there other tests that might show useful things
Gparted has other tests. Would that info be useful now, or can I wait and do it later?
There are only 2 partitions. One is empty, except for a file labeled

 "Ubiquity.desktop" Its property shows 8.3 kb

When I got into the system, I found part of the problem was it was booting into the "empty" partition with **535.8 MB**
The primary partition is 640 GB. 

I just ran the Disks & Storage test. It shows The HDD partition 15.7 GB is being used (With some contents unreadable)
Under the disk measurement, there is a 20.3 GB used. 
Yet it looks like the difference between the two - is about 4.6 GB that is somewhere else. Is this significant? 

For some reason, when I set up this hard drive about a year ago, I set it up under a sub-folder. If that's what it's called.
I'd like to change it to make it my boot partition.

---

### Post by TheFu on 2021-07-27
For disks, there are lots of tools.
smartctl, fdisk, badblocks are the main ones.  Avoid GUIs. They lie. They often oversimplify way too much and provide misleading output.

> For some reason, when I set up this hard drive about a year ago, I set it up under a sub-folder. If that's what it's called.
I'd like to change it to make it my boot partition. 
Don't understand this. Sorry.

Booting on UEFI systems has a specific standard that must be followed. Attempt to change that if you'd like a dead box that only boots from flash storage.

---

### Post by Gnusboy on 2021-07-28
FU
[QUOTE]
Three days ago I got email bombed. In less than 24 hours, spanning 2 days,  I was sent about 300 emails. Most were repetitive and the time stamps showed they came within seconds of each other.. I read that this was probably a denial of service attack. But I can't understand why it would hit me. If they were after $$ they were far, far off base. 
Blood from a stone, etc.
How would I be able to find out who sent this and what the damage  (assuming they are not running under TOR)
I've been using my old Windows XP system until I get straightened out. Does an out-of-date operating system make it easier crack over all ? Or, since it was an via  gmail attack, neither Linux or Windows make a difference?
I did go through my gmail account and deleted all of the suspicious messages and I have not opened any of my important links.
Have you heard of any other on-going attacks?]

Also:

Do you know what these symbols mean or are used for?

&#9888;&#65039;&#55349;&#56789;&#55349;&#56814;&#55349;&#56827;&#55349;&#56824;_&#55349;&#56790;&#55349;&#56821;&#55349;&#56818;&#55349;&#56816;&#55349;&#56824;&#55357;&#56504;

---

### Post by TheFu on 2021-07-28
300 emails isn't a DoS attack.  30,000 wouldn't be a DoS attack, unless you are on a 2400 baud modem.

Probably want to open a new thread for these questions, since they aren't related to fsck.

---

### Post by Gnusboy on 2021-07-28
Got it. Thanks, 
Gawd, I remember 2400 Baud. The first time I used a computer was on a trash 80. We used it to file stories at the newspaper where I worked '86. It was a on a blazing fast 300 baud connection. When I went to work at a bigger paper, they ran the entire system on a 20 MB server. 
The I.T. got himself "god's own computer" it was a 286 with 2, count 'em, 2 MB of memory.
Thanks for all your help. I appreciate it.
P.S.
Granny's on the CB waitin' to hear from you.

---

### Post by Gnusboy on 2021-07-31
Touche'

---

### Post by Gnusboy on 2021-08-01
I hope there is someone to answer a question before I do something stupid.

I've been working through a series of issues with 20.04 and my system. I've had many starts and stops during this process - Life gets in my way - a lot.
 
I used the Live disk to get into home / documents, then did a copy/paste of the entire home folder
and dropped it onto the 1 TB external drive. I saw the folder was there, but I did not have the time to check if it was complete.

So, that brings us to this day. I booted the Live disk, The HDD is a 650 GB main partition - with a 530 MB partition. 
and opened a terminal and entered  
```

sudo fsck /dev/sda5 and came up with
e2fsck 1.45.5  (07-Jan-2020)
/dev/sda5 contains a file system with errors, check forced.
Pass 1:Checking inodes, blocks and sizes
Inode 25401772 extent tree (at level 1) could be shorter. Optimize<y>? no
Inodes that were part of a corrupt orphan linked list found.  Fix<y>? 
```

My panic comes from the potential loss of several very important documents. Although the odds of keeping them
are probably in my favor ... I do not want to lose any of them.
At the moment, I still have the terminal open to the fsck I started, but discontinued when I remembered I hadn't finished the backup. I tried to use the exit command to end today's process, but it didn't work. I didn't want to mess with it, until I get some advice weather I need to just shut the terminal and finish the backup. Since it's mid-way into the process, can it cause another problem. 
 
This is the message I saw after my previous fsck. I'm not certain, but I might have done the fsck on a mounted partition. It shows some potentially worrisome issues. This is the output from the fsck

```

[COLOR=#000000]Failed to start shuts down pre-installed sys cleanly[/COLOR]
[COLOR=#000000]SystemCTL i status Casper.service for detail[/COLOR]
[COLOR=#000000]OK Reached Target Final step/finished powered-off[/COLOR]
[COLOR=#000000]OK Finished reached target power off 
[/COLOR]
[COLOR=#000000]**[!!!!!!] Failed Execute** shutdown binary [40985.213694] blk_update_request] I/O Error[/COLOR]
[COLOR=#000000]Plus several similar lines.[/COLOR][COLOR=#000000]
I had done a soft reboot e[/COLOR][COLOR=#000000]arlier to exit the "BusyBox ... Initramfs" screen.
```[/COLOR]
[COLOR=#000000]```
[/COLOR]
[COLOR=#000000]Begin: running/scripts/local-premount ... done[/COLOR]
[COLOR=#000000]Begin: Will now check root file system ... fsck from util-linux 2.34 [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck,ext4 -a -C0 /dev/sda5 /dev/sda5 contains a file system with errors, check forced[/COLOR]
[COLOR=#000000][ 10.326632] random: crng init done ==== \54.4% /dev/sda5:[/COLOR]
[COLOR=#000000]Inode 35401772 extent tree (at level 1) could be shorter. IGNORED. /dev/sda5: Inodeds that were part of a corrupted orphan linked list found.
```
[/COLOR]```

[COLOR=#000000]/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -A OR -P OPTIONS[/COLOR]
[COLOR=#000000]fsck exited with status code 4 done.[/COLOR]
[COLOR=#000000]FAILURE: file system check of the root filesystem failed [/COLOR]
[COLOR=#000000]the root filesystem on /dev/sda5 requires a manual fsck 
```

Thanks.


[/COLOR]

---

### Post by Gnusboy on 2021-08-03
Hey all,

My attempts to get my system working are progressing well, but I've got a couple of questions I need to finish the job.
I  decided to make this a new thread that I hope can help me understand the system issues and what to do the next time. 
The previous posters  helped me get this far and I am grateful for everyone's help.
Hopefully,  I can get this issue fixed and what to do the next time.
It will help me to better understand how my system works and to make it better.  
What does "FILE SYSTEM WAS MODIFIED" mean in my situation and how do I get it taken care of?

[COLOR=#000000]```


```[/COLOR]```
[URL="https://ubuntuforums.org/showthread.php?t=2464806"][COLOR=#000000]dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes[U]
   Where says "passed" does it mean it's retaining the item (s) in the line is working as it should?[/U][U]

Inode 35401772 extent tree (at level 1) could be shorter.  Optimize<y>? yes
   Could be shorter than ? How was it Optimized?
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes
    From my [/U]_understanding, Inodes keep track of numerous data items, such as -_
[/COLOR][/URL]
[LIST]
[*]Owner ID
[*]Group ID
[*]Size of file
[*]Number of hard links to the file
[*]Time last accessed
[*]Time last modified
[/LIST]
Inodes have dedicated space that is allocated. And Inodes can get used up before their allocated data space is gone.
```

```

Deleted inode 35409210 has zero dtime.  Fix<y>? yes
Pass 1E: Optimizing extent trees
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 259707/39043072 files (1.5% non-contiguous), 7676803/156151296 blocks 
```

Is there a way to find out how the file system was modified and what it means?
 don't know much - it might be good to know more.[/code]
Sorry about the underline. I tried to get rid of it using the options shown, but that didn't work. [/code]

This is what the fsck showed initially. 

Fsck found some issues with my system. It also looks like most of them were fixed. 

Thanks

[URL="https://ubuntuforums.org/showthread.php?t=2464806"][COLOR=#000000]
[https://ubuntuforums.org/showthread.php?t=2464806](https://ubuntuforums.org/showthread.php?t=2464806)

[/COLOR][/URL] [U][URL="https://ubuntuforums.org/showthread.php?t=2464806"][COLOR=#000000]My system is an AMD 9850
650 HDD - with one 650GB HDD partition 
And another [/COLOR][/URL][[COLOR=#000000]partition with 535.8 MB[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2464806")[/U][U] [URL="https://ubuntuforums.org/showthread.php?t=2464806"][COLOR=#000000]
[/COLOR][/URL][[COLOR=#000000]The Disks & Storage test. It shows The HDD partition 15.7 GB is being used (With some contents unreadable)[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2464806")[/U][URL="https://ubuntuforums.org/showthread.php?t=2464806"][COLOR=#000000]

[/COLOR][/URL]

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[B]
```
 
The background: 

```[/B]```
[B][[COLOR=#000000]I did the first fsck[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2464806")[COLOR=#000000] with a mounted partition. I did not realize that the partition was supposed to be unmounted. [/COLOR]After I unmounted the partition, I did the recommended fsck, this what it returned this information:

t[/B]his is a mouse the kept freezing, then releasing,  etc. but  then locked up to the point of having to reboot to make it  work. This  problem led me to attempt a fix using FSCK. But I didn't read  the part  where I was supposed to do this from root w/o mounted file  systems. I  tried that twice and it then came back with "error code 2."
I tried to run fsck again, but then the system came back with the   BusyBox v1.30.1 Initramfs errors. I read as much as I could on how to   proceed, but didn't see any solution that I thought fit my situation.

Finally, I rebooted with the 20.04 live disk and to "Try Ubuntu" That   brought up 2 partitions - one empty and the other with the file systems  I  had been using.
I checked on my documents - which seemed OK, but I'm not sure I still had all of them.
I don't recall exactly what I did then, but there was a banner showing 

Circle X Access with sys/device/software/subsystem/uevent denied
I hit OK and the banner closed
In the second partition (supposedly empty) There was a file labeled
 "Ubiquity Desktop"name:~desktop/ubiquity.desktop
2[read only] /run/network manager/devices

```

```

Failed to start shuts down pre-installed sys cleanly
SystemCTL i status Casper.service for detail
OK Reached Target Final step/finished powered-off
OK Finished reached target power off
[!!!!!!] Failed Execute shutdown binary [40985.213694] blk_update_request] I/O Error

Earlier today the screen was frozen and I did a soft reboot and got 
Begin: running/scripts/local-premount ... done
Begin: Will now check root file system ... fsck from util-linux 2.34   [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck,ext4 -a -C0 /dev/sda5   /dev/sda5 contains a file system with errors, check forced
[    10.326632] random: crng init done ==== \54.4% /dev/sda5:
Inode 35401772 extent tree (at level 1) could be shorter. IGNORED.   /dev/sda5: Inodeds that were part of a corrupted orphan linked list   found.
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -A OR -P OPTIONS
fsck exited with status code 4 done.
FAILURE: file system check of the root filesystem failed 
the root filesystem on /dev/sda5 requires a manual fsck

```
  
```
 
$ sudo fsck /dev/sda5
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 35401772 extent tree (at level 1) could be shorter.  Optimize<y>? yes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

The worrisome item is:
dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 259707/39043072 files (1.5% non-contiguous), 7676803/156151296 blocks 

```

---

### Post by Gnusboy on 2021-08-04
Sorry to bother y'all again, but my system is locked up - again. I had the system on all night and this morning I saw a big red circle
with an exclamation mark. When I opened it, it showed "Sorry, Ubuntu 20.04 has experienced an internal error." I clicked into it and saw:I was AFK for 20 minutes and came back to a new error screen, but the curser was released and working:

At the moment I'm undecided weather to reboot to see what happens, or see if I can find what all these errors are about.
Any ideas?

"THE APPLICATION Passwords and keys has closed unexpectedly
send problem to the developers 
  X Remember in future
  X Relaunch this application

I opened this and got 40 lines including:These lines will not copy/paste, so I have not copied 
I have not copied all the lines showing.
If you think it's necessary, I can.

------------------------------------------

ExecutablePath
/user/bin/seahorse

Package Seahorse 3.36-1

ProblemType
Crash

CoreDump

CurrentDesktop
Ubuntu:Gnome

Date
Wed Aug 4 21:00:51 2021


dDndendencies
Distro
PackeageArchitecture
ProcCmdline
  usr/bin/seahorse-gapplication-service

UnreportableReason
   You have some obsolete package versions installed.Please upgrade the following packages and check if the problem still occurs


And other lines of code

Unfortunately, this group of items will not copy and post,  but if you think it's necessary, I can hand write them.

------------------------------------------------------

This is all the messages referring to earlier info from fscks; from the fsck I made with the partition probably mounted. I'm not certain
And the others that were not mounted

ExecutablePath
"/usr/lib/libreoffice/program/soffice.bin"
Then the curser locked up and wouldn't move. I can hear the HD constantly working - the curser will be stuck in one place on the screen, lock up for several minutes, then will jump to another area, but still won't respond to my input.
This the same problem I started with 2 weeks ago. Everything seemed fine yesterday. I didn't do much except research
 how to figure out what the post was referring to. Here is what shows after an fsck from the 20.04 live disk

```

Failed to start shuts down pre-installed sys cleanly
SystemCTL i status Casper.service for detail
OK Reached Target Final step/finished powered-off
OK Finished reached target power off
[!!!!!!] Failed Execute shutdown binary [40985.213694] blk_update_request] I/O Error 
```

Three days ago, the curser on screen was again frozen and I did a soft reboot and got: 

```

Begin: running/scripts/local-premount ... done
Begin: Will now check root file system ... fsck from util-linux 2.34    [/usr/sbin/fsck.ext4 (1) --/dev/sda5] fsck,ext4 -a -C0 /dev/sda5    /dev/sda5 contains a file system with errors, check forced
[    10.326632] random: crng init done ==== \54.4% /dev/sda5:
Inode 35401772 extent tree (at level 1) could be shorter. IGNORED.    /dev/sda5: Inodes that were part of a corrupted orphan linked list    found.
/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (I.E., WITHOUT -A OR -P OPTIONS
fsck exited with status code 4 done.
FAILURE: file system check of the root filesystem failed 
the root filesystem on /dev/sda5 requires a manual fsck

```
  
I rebooted again, ran the fsck and this the result:

```
 
$ sudo fsck /dev/sda5
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 35401772 extent tree (at level 1) could be shorter.  Optimize<y>? yes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

The worrisome item is:
dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda5: 259707/39043072 files (1.5% non-contiguous), 7676803/156151296 blocks 

```

And that's where I am now

---

