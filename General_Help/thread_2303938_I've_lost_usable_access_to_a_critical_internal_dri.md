---
title: "I've lost usable access to a critical internal drive: i/o errors."
date: 2015-11-23
forum: General Help
---

### Post by David4321 on 2015-11-23
I've lost usable access to a critical internal drive, getting i/o errors. This is not OS drive.


Yesterday I was setting up a VPS and file sharing, all of which worked fine. (I don't know that this had anything to do with problem, it just coincided) But at some point I noticed the drive was appearing twice in drive lists and file explorer. After restarting drive appears only once. I can see all files and folders on the drive as normal. I can navigate anywhere on the drive. Drive properties appear normal. Drive passed GSmartControl test. But I cannot open or play any files on the drive, I get i/o errors. Owner of drive is root.


Thanks for any help!

---

### Post by T.J. on 2015-11-23
Could you please post some examples of the i/o errors?  I'm afraid the above message is a little too vague to help you.

---

### Post by David4321 on 2015-11-23
Thanks for the response. There's really nothing else in the errors, just input-output error. 

Examples from different file types:

[http://bluelight.us/files/Workspace-1_274.png](http://bluelight.us/files/Workspace-1_274.png)
[http://bluelight.us/files/Workspace-1_275.png](http://bluelight.us/files/Workspace-1_275.png)
[http://bluelight.us/files/Workspace-1_276.png](http://bluelight.us/files/Workspace-1_276.png)
[http://bluelight.us/files/Workspace-1_277.png](http://bluelight.us/files/Workspace-1_277.png)
[http://bluelight.us/files/Workspace-1_278.png](http://bluelight.us/files/Workspace-1_278.png)
[http://bluelight.us/files/Workspace-1_279.png](http://bluelight.us/files/Workspace-1_279.png)

---

### Post by T.J. on 2015-11-23
I am not trying to sound condescending.  I simply do not know your skills, so please forgive me if we do this slowly. 

Assuming the disk passes a boot check and scan, I would check the permissions on the file folders to make certain they have not been reset by mistake to root ownership (which could make the files unreadable to non-root accounts).   
Are you able to copy files from the drive to another?  I would assume you get a similar error, but it is worth asking.   

As a rule of thumb, you should never store non-OS files under root permissions.

You can reassign the ownership on a folder and its contents with the chown command e.g*. sudo chown -R myuser Myfolder*

---

### Post by David4321 on 2015-11-23
Thanks, I'll try this. I wondered if the root ownership was the problem, I never set this manually, not sure how this happened, either by default or by accident/error. I notice that all my internal drives are also owned by root and I'm not having that problem with the others. I tried opening nautilus under sudo and the other non-os drives do not appear in list. 

I'm pretty competent, but I always appreciate step-by-step help, thanks. I'm very advanced in windows, but only a year into linux, so especially need detail on terminal commands.

I want to try reassigning entire drive to user ownership, not just a folder. Can you walk me through that fully? Is there a gui tool that can manage this kind of stuff?

OMG ~ I just realized I have full access to all drives again after today's reboot! It just sorted itself out. I'm leaving this post, because I'm still interested in learning about managing permissions and ownership.

I'm reluctant to mess with it now, but what is the reason you'd advise not allowing root ownership on non-os internal drives, and how could that be done? I could try it on a less critical fully backed up drive if justified.

Thanks!

---

### Post by matt_symes on 2015-11-23
Hi

I would check the physical connection to that drive if it just fixed itself. I would also look at syslog to see if there are any drive errors on there.

```
gedit /var/log/syslog
```

I would also backup that drive and run a SMART test on it.

```
sudo apt-get install smartmontools

sudo smartctl -t long /dev/sdX
```

where X above is the drive and not a partition.

Kind regards

---

### Post by bab1 on 2015-11-23
> **David4321 said:**
> ...[ why]  root ownership was [a]  problem, I never set this manually, not sure how this happened, either by default or by accident/error. I notice that all my internal drives are also owned by root and I'm not having that problem with the others. 
Root user ownership in not the reason you have had Disk I/O problems.  This is a hardware problem.  That's why @matt_symes posted what he did. > 
I tried opening nautilus under sudo and the other non-os drives do not appear in list. 

THIS  is is how the directories and files got root ownership.  You should not use the root user (sudo) for GUI applications without understanding the ramifications.  The safest way to use the root user via sudo is at the command line. 
> 
I'm pretty competent, but I always appreciate step-by-step help, thanks. I'm very advanced in windows, but only a year into linux, so especially need detail on terminal commands.


Its well worth learning how to use shell commands from the terminal for administrating the system.> 
I want to try reassigning entire drive to user ownership, not just a folder. Can you walk me through that fully? Is there a gui tool that can manage this kind of stuff?

The basic command to change ownership on an entire file system tree (e.g. /home/<you> is```
sudo chown -R <someone:somegroup> /home/<you> 
```...where <someone:somegroup> is of your choosing (e.g. bill:bill instead of you).  You can try this on a tree that is a subdirectory in your home directory.  Create a small 2 level file system in your home directory```
mkdir -p wee/willie
```
Change the ownership of this to someone else's login using this ```
sudo chown -R wee <user:gorup>
```  If you don't want to change your ownership but want to change the group you just use your login and the new group or user the command ```
sudo chgrp -R <group> wee
```... instead of chown.

All of the commands are in the local machine manual (man pages).  To look at the man page for chown you use this command```
man chown
```
> 
OMG ~ I just realized I have full access to all drives again after today's reboot! It just sorted itself out. I'm leaving this post, because I'm still interested in learning about managing permissions and ownership.

Things don't just fix themselves or magically get better.   The entire file system could have had a file system check (fsck) or intermittent hardware problem.  See  @matt_symes advice. 
> 
I'm reluctant to mess with it now, but what is the reason you'd advise not allowing root ownership on non-os internal drives, and how could that be done? I could try it on a less critical fully backed up drive if justified.

Thanks!
There is no reason you shouldn't have root ownership of non-os directories or files per se.  No hardware has ownership or permissions.  Partitions have no ownership or permissions either. Ownership and permissions are for access control of directories and files.  I have plenty of directories that are owned by root while the group ownership is by a group that a set for multiple users (e.g. staff).

You can start your journey towards command line happiness [**here**]("https://www.google.com/search?client=ubuntu&channel=fs&q=learning+ubuntu+command+line&ie=utf-8&oe=utf-8").

---

### Post by T.J. on 2015-11-24
I'm glad you got it worked out.  What I was referring to was not drives but folders created on them.  Bad permissions on personal folders can cause all kinds of strange errors in GUI apps - Windows or Linux.

---

### Post by T.J. on 2015-11-25
Please mark the thread as SOLVED if the problem is no more.

---

### Post by David4321 on 2015-11-29
Update: I'm still having problems, but only when running VPN. It seems that when I'm running as a different location, the system gets confused and the drives appear to fail and produce i/o errors, but upon clean restart everything is in order and all drives are functioning normally until I go to VPN.

Let's set that aside for now, I'll take it up with the VPN provider first, but before that I want to handle the drive ownership issues.

Now I've installed a brand new internal hard drive, and formatted it to ntfs on gpt table. This one behaves perfectly. It appears inside the /media/ folder, is owned by "me", and I can manage permissions and access freely from properties. OS drive is ext2 ssd, owned by root, no problems. I have 4 other significant partitions, on 3 internal physical drives, all are owned by root, and I cannot manage permissions or access - I want to take user ownership of these. All these partitions are ntfs, 2 on gpt tables and 2 on msdos tables. NONE of these partitions appears inside the /media/ folder, and if I open Nautilus using sudo, they disappear from the device list. ONLY the OS drive and the newly added one appear in /media/. (this is a change, they all used to be there - I don't know how or when that changed) They all appear in terminal under /etc/fstab. I have checked the physical drives using GSmartControl, and they all pass. 

I tried to change ownership using 'sudo chown -Rv username /path-to-partition' and this seemed to succeed, but did not change partition properties. I then tried 'sudo chown -Rv username /path-to-mount-point' and this went through a long sequence appearing to change ownership of each file in partition, but same result, no change to partition properties. These results verified after restart.

How can I take ownership of these partitions? Thanks for suggestions!

---

