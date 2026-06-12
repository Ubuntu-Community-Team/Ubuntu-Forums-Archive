---
title: "[SOLVED] Serious Xubuntu/Thunar problems: crash/freeze; generally works slow"
date: 2007-12-10
forum: General Help
---

### Post by ManWithNoOS on 2007-12-10
*Please I need help with this, I can't work with Xubuntu if it keeps freezing up/slowing down...*

**Env:** PC, ~1,2GHz (AMD Athlon), 768 SDRAM; file system ~8GB ext3 (media/hda4), swap ~1GB, c: (media/hda1) ~8GB ntfs, d: (media/hdb5) ~120GB ntfs, e: (media/<the actual drive name>) ~40GB ntfs.

**OS:** Xubuntu/Win2k
**User:** new to linux.
**Misc.:** Linux mounts c: and d: on startup.

**My problem(s): **

**1)** Thunar keeps freezing up, and the system generally works slow. I do not know what starts this, sometimes by simple opening the Thunar file manager (or so it feels,,,), the problem generally starts with Thunar, on opening a folder either it will take a *very* long time, or it will completely freeze up. 

**2)** I think this problem is related to 1). When I restarted the system and looged in win2k I found that there was a folder in the e: root, with the name hda1 (i.e. my c: ), in that folder I found my document & settings folder and the .sys file; if Tunar had been copying that to my e: (media/hdb5) then no wonder why things went slow. 

Why did this happen?!

And why does these problems appear?

Someone suggested that my ntfs drives are causing this, but I'm not sure, anymore. 

And Xubuntu generally works slow. 

**Note:** The Ubuntu forums "Here are the similar threads we found:" recommended, among other threads, this thread: [http://ubuntuforums.org/showthread.php?t=112200](http://ubuntuforums.org/showthread.php?t=112200) (with the follow up thread [http://ubuntuforums.org/showthread.php?t=76266&highlight=6000](http://ubuntuforums.org/showthread.php?t=76266&highlight=6000)) regarding the slow performance, however I don't understand how to find out my CPU limits on Xubuntu and how to change it.


Thanks in advance for your time.

---

### Post by Nano Geek on 2007-12-10
Hmm. It shouldn't be freezing on a system like that, but try this.
Try running Thunar in the terminal, and when it crashes, post what it says in the terminal here.

---

### Post by carlos1992 on 2007-12-10
and thunar is the only apps that freezes and are you really sure linux is on a separted HD (partition!)

---

### Post by ManWithNoOS on 2007-12-10
*"Try running Thunar in the terminal,"*

I'm not quite sure what you mean, but I opened the terminal and printed "thunar" and the file manager opened (no problems).

*"and thunar is the only apps that freezes"*

You are quite right, it is not the only application that freezes, but all other application tend to freeze after thunder freezes (that includes the system monitor), and they work when thunder is killed.

Generally the other applications (if thuner isn't the culprit) tend to just be sluggish.

*"and are you really sure linux is on a separted HD (partition!)"*

Well, yes? I used the linux built in partition tool and made sure there were 4 partitions on my hard drive, all were made primary after recommendation from other linux users. (ps. the partition were created fresh before install using the liveCD)

PS.2 This is wierd. In my media folder it states that hda4 has 5.3 GB free. In the SysMon it says that hda2 has 5.3 GB free (this drive with the 5.3GB free is the partition that holds Xubuntu) and that hda4 has 32 GB free (i.e. the same as "my media/<the actual drive name>" folder. I do not know what this is about...

---

### Post by Nano Geek on 2007-12-11
> **ManWithNoOS said:**
> *"Try running Thunar in the terminal,"*

I'm not quite sure what you mean, but I opened the terminal and printed "thunar" and the file manager opened (no problems).Yes, just leave it like that for awhile, and when it crashes, post here what the terminal said after you entered **thunar**.

---

### Post by ManWithNoOS on 2007-12-11
I'll make sure to post that.

**A different approach?**

But have been investigating other possible problems, and have come up with the following:
The computer generally runs slow and sluggish, like running a old computer. In comaprison my win2k install, runs extremly fast -- Xbuntu should be at leats equally fast.

Maybe something else is wrong, and maybe that, in turn, effects thunar?

One aspect I'm currently investigating is the graphic card: I have a ASUS Nvidia N6200 128DDR.

Curently I run Xubuntu at 1600x1200 (I do not know the depth) and it runs very sluggishly. The graphics lags when I move the windws, and the CPU goes nuts. I'm currently playing with "sudo dpkg-reconfigure xserver-xorg"

"Configuring xserver-xorg"

> 
"Typically, the amount of dedicated memory used by the video card is autodetected by the X server, but some integrated video chips (such as the Intel i810) have little or no video memory of their own, and instead borrow main system memory for their needs.
This parameter should usually be left blank and specified only if the video card lacks RAM, or if the X server has trouble autodetecting the RAM size."

Amount of memory (kB) to be used by the video card: 
I changed the following: 128000. 

And chanegd the bit default to 16.

Let's see what this does :)

---

### Post by ManWithNoOS on 2007-12-11
**OK, this is the situation:**

I had two instances of Thunar opened. One in the Xubuntu partition, and the other on my munted ntfs partition.

Thunar freezed (both instances) when I tried to create a folder on the ntfs partition. 

When I ran thunar in the terminal, it took a while, but it opened!

But the other two instances remained frozen. 

I repeated the process, and the same; thunar opened after a long time, and after I closed it the two first instances remaind frozen.

Now, I reopened thunar for the third time and explored the folders.

I recieved tis error,
Reason: There is no plugin to handle this movie..
totem-video-thumbnailer couln't open file 'file:///media/<drive>/raidenii2%5B1%5D.swf'

But otherwise no problems, created two folders, and everything was fine.

I reopened thunar through the terminal (for the forth time) and killed the frozen instances. I recieved no messages in the terminal window.

Also, the computer runs alot faster after my graphic card changes, I htink it was related to the colour depth.

Ok, now opened thunar again; one from the xfce menu, and one from the terminal. Both instances are very slow, it takes around a minute to open them. When open it seems to run at normal speed.

Other programs open normally.

When I launch thunar, the CPU tops once or twice, but otherwise do not "overload".

The problem seem to be related to thunar, no?

---

### Post by ManWithNoOS on 2007-12-11
**There seems to be two scenarios:**

**A) **
As long as the first instances of Thunar are frozen I can launch infinite other instances of Thunar and do pretty much what I want without any problem... The new instances do not seem to cause any problem.

**B)**
Thunar crashes, or I kill it. After that I pretty much could go at it. For a while at least.

//
In both cases I'm not sure what is causing this. I'm going to google around for the mount ntfs services. I'm going to presume that they are the culprits behind this mess.

While writing this I notice something else: the service gam_server seem to do alot of working also. After I viewed "open files" in system monitor it showed that the service is going through some files on one of the mount.ntfs drives. I will do some googling after that too.

---

### Post by Nano Geek on 2007-12-11
Let me ask you something, when you play a video file, what player does it open in?

---

### Post by ManWithNoOS on 2007-12-19
Hi, thanks for your reply, 

My problem is solved, I think. I was waiting to see if the problem still persisted before marking this thread as resolved, but I have been so busy that I haven't had a chance to work with Xubuntu again.

**To answer your question**
*"Let me ask you something, when you play a video file, what player does it open in?"*

The standard movie player that comes with Xubuntu; it's Totem if I'm not misstaken.

**The solution to my problem**
I found this thread regarding "gam_server", and the fix in that thread seem to do the trick.
[http://ubuntuforums.org/showthread.php?t=210329&highlight=gam_server]("http://ubuntuforums.org/showthread.php?t=210329&highlight=gam_server")

I haven't been using Xubuntu so much, but I think the problem is gone now.

However, the computer still runs slow, but I'll have to look into to that later.


Thanks, those of you that tried to help me!

---

### Post by Nano Geek on 2007-12-19
I'm glad you found a solution.

---

