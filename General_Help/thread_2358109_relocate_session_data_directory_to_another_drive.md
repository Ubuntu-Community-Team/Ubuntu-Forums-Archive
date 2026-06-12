---
title: "relocate session data directory to another drive"
date: 2017-04-09
forum: General Help
---

### Post by jjbabydarling on 2017-04-09
Hi,

First time Linux user, first forum post.

Just built my first PC (lotta firsts!).

Using Ubuntu Studio distro with Xfce desktop environment.

I have two internal drives.

Boot, root and home on a 275gb SSD plus a 2tb HDD mounted at /media/jjbabydarling/2.0 TB File System/

Now I really like the feature "Save session for future logins" tickbox on the log out dialogue.

But I read this article that said using such a feature is a good way to wear out your SSD faster than otherwise:

[https://www.cnet.com/how-to/how-ssds-solid-state-drives-work-increase-lifespan/](https://www.cnet.com/how-to/how-ssds-solid-state-drives-work-increase-lifespan/)

So I thought it would be a fun challenge and a good way to get to know the system I am now working with to try and get the Xfce Session Manager to save those files to my HDD instead. (Realise this will make the log in and out process slower with the feature enabled but I don't care too much and well... I can always move it back).

I found this article:

[http://docs.xfce.org/xfce/xfce4-session/advanced](http://docs.xfce.org/xfce/xfce4-session/advanced)

which suggests that "${XDG_CACHE_HOME}/sessions/" represents "The directory where xfce4-session and xfwm4 store the session data to."

I've figured out that it's currently set to here: "/home/jjbabydarling/.cache/sessions/" and I'd like to set it to here: "/media/jjbabydarling/2.0 TB File System/.sessions" or some such similar directory.

I have no idea whatsoever how to change which directory it's set to.

Any takers?

Thanks.

---

### Post by TheFu on 2017-04-10
Welcome to the forums.

So, with Unix systems, there are usually 500 different ways to accomplish the same thing.  The way we often think is a good solution is not, when someone with more expertise comes along and understands the real reason for wanting something, often a better option will be suggested.  Happens to everyone, since someone always knows more, right?

So - first thing is that all HDDs/SSDs are going to fail.  That is their goal in life, failure.  I have HDDs that died after 90 days and 1.1 yrs and I have some that are still spinning 24/7/365 after over 10 yrs.  For SSDs, the early models didn't have much longevity, but as the makers learned more, they addressed those issues. 

However, SSDs are like HDDs in that their goal in life is to fail.  I've had an SSD in a chromebook fail after 9 months and have others that are 4 yrs old and going strong. These aren't "enterprise" level SSDs either. They are fairly cheap, relatively slow, consumer SSDs.  IMHO, an SSD that isn't being used in a convenient way isn't useful.  After all, SSDs are all about being a little more convenient than HDDs. They are faster, quieter, use less power, but also come in smaller sizes and cost much, much, more.

I read that SSDs are designed for a 10 yr average life.  If you have a laptop for more than 5 yrs, you are strange. If you haven't upgraded/increased the on-board storage in that time, usually there are other issues, perhaps bit rot.

So ... as a 20+ yr professional, I have to ask, is this really worth the effort?  I'm not a huge SSD user. Only have them installed in 1 chromebook (using it now) and don't do anything special to use HDDs over SSDs.  An older SSD from a prior chromebook has been put into an external enclosure to make that 128G of fast, encrypted, storage available. It is handy for travel. Also have a few external HDDs in 2.5in enclosures for extra storage. Usually don't travel with them anymore.

Ok - let's assume it **is** worth the effort.  Do you just want to move only those specific files or should you move your entire HOME?  What about all the log files in /var/ which are constantly written?  

The good news is that pretty much anything can be relocated on any Unix system, provided the storage "appears" to be in the same place or settings can be modified to tell the OS where the new location is.

The simple way is to use symbolic links at a directory level to redirect from the SSD to the HDD. You'll want to move the data and create the symlink quickly - don't use any other programs at the time.  For example, you can move ~/.config/ to the HDD, if you like.  First of all, the HDD storage **must** be a Linux file system. Not NTFS, not FAT-anything.  It should support normal, Unix owners, groups, permissions, ACLs and whatever else you need.

The other thing is that /media/jjbabydarling/2.0 TB File System/ is probably an external disk and probably automatically mounted to that location by Linux.  You don't want that for a number of reasons.  There are 500 different ways to solve this. After verifying that the external disk is using some Linux file system - ext4 would be a reasonable choice - then you could mount it as the /home or the /home/jjbabydarling or the /home/jjbabydarling/.config/ - which is completely up to you.  Or you could mount it to /u and relocate your HOME under /u/ using the **usermod** command. That would have the effect of modifying the passwd (userid) database AND with the correct options, it will move all files in your $HOME (/home/jjbabydarling --> /u/jjbabydarling ). It is a fairly simple thing.

To control the mounts for permanently connected storage, hopefully, NOT USB, but SATA or SAS connected storage, you'll need to edit the /etc/fstab file. This is a basic skill that all Linux users should have, IMHO.  There's a how-to for it: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) - use **sudoedit**. Be VERY careful using any GUI program with sudo. There can be unintended outcomes doing that.

So, really the first question to answer is whether the other HDD has a Linux file system on it.  The output from the 'mount' command will show that. Please check it.

Most of these things are best performed when not actually using the same userid you plan to relocate.  In fact, it would be best to boot from alternate media or use a different sudo-capable account to perform these actions.  I would ssh into the machine and create a small script that did everything quickly.  Just beware that if the location in the /etc/passwd file and the actual HOME aren't matched, unexpected things can happen. If the new HOME isn't mounted with the correct permissions, it could make logging in as that userid difficult.  

Also, moving the ~/.config/ directory impacts many other programs, so if a mistake is made, those other programs could be negatively impacted.  It isn't hard, but someone new to multi-user operating systems could easily become confused.  It isn't brain surgery or rocket science, but is it a little more challenging than replacing a gas tank on a vehicle.

Make sense?

---

### Post by jjbabydarling on 2017-04-12
Hi I really appreciate your detailed and reasoned answer. I have decided it's not worth it. Certainly not worth relocating my entire home to the other drive. I'm just guna get stuck in to learning to basics of how Linux works and then optimise my system more later. Defo checking out that link you gave me on fstab! Thanks. And thanks for taking the time to indulge me. Fyi it's formatted to ext4 and connected via SATA 6gb/s.

---

### Post by TheFu on 2017-04-12
A little tip - don't have strange characters in filenames or directories - that includes spaces. Sure, the file systems all handle it, but scripting is harder and certain script writers don't bother to handle spaces well.  I don't.  Just isn't worth my time when I want to feed lots of files into a script to be processed one at a time.  Spacing is a common delimiter and most of my scripts assume that a space means the next filename.

So - when you mount that storage somewhere else, it is recommended that you remove all the spaces - also, making it shorter wouldn't hurt - save a little typing.

---

