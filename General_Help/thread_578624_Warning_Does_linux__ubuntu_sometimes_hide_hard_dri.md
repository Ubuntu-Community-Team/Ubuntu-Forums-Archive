---
title: "Warning? Does linux / ubuntu sometimes hide hard drive faults?"
date: 2007-10-17
forum: General Help
---

### Post by e_james on 2007-10-17
Last week I stumbled over a problem with hard drives in linux and / or ubuntu. At first I was puzzled but I am now 99% confident that a hard drive can fail by progressively developing bad sectors and ubuntu will not tell me about it until it's too late to take any useful remedial action. 

What seems to happen is that at each startup ubuntu (6.10) performs a disk diagnostic and quietly "fences off" any bad sectors from further use. The problem only became noticeable when a 1.6GB partition with 149MB of files ended up with 80KB of free space. The next time it was started there was no free space.

Is there any diagnostic routine (preferably something automatic), which would draw attention to this situation? Is it something that linux users in general should hear about and how should we tell them?

---

### Post by peabody on 2007-10-17
> **e_james said:**
> Last week I stumbled over a problem with hard drives in linux and / or ubuntu. At first I was puzzled but I am now 99% confident that a hard drive can fail by progressively developing bad sectors and ubuntu will not tell me about it until it's too late to take any useful remedial action. 

What seems to happen is that at each startup ubuntu (6.10) performs a disk diagnostic and quietly "fences off" any bad sectors from further use. The problem only became noticeable when a 1.6GB partition with 149MB of files ended up with 80KB of free space. The next time it was started there was no free space.

Is there any diagnostic routine (preferably something automatic), which would draw attention to this situation? Is it something that linux users in general should hear about and how should we tell them?

I agree that there definitely should be something that detects this at startup and informs the user.  The only thing that provides something for the user to take notice with is the fact that if the kernel experiences any i/o errors on a file system it'll remount it read only and there will be a message saying such in /var/log/messages.

If nothing happens while the system is running, I'm not sure the results of e2fsck are logged anywhere, which is a very bad thing.

---

### Post by LanDan on 2007-10-17
well......harddrives can fail....no argue about that, but that has more to do with the drive. you might want to check your hard drive for failure after you make a back-up of all your data

---

### Post by ahaslam on 2007-10-17
I do seem to get a fair amount of filesystem corruption, especially with ext3. I moved to xfs about a year ago & got my first fault last week. I like the xfs tools, for example 'xfs_repair' did what it's name suggests within a minute. For a simple fs diagnostic, xfs_check is also very quick & effective.

To check your hard drive, I recommend SeaToolsDOS, a live cd which is freely available from Seagate.

---

### Post by e_james on 2007-10-17
LanDan

You seem to be missing the point. Why would I test a drive I believe to be good? Maybe I should test it every day, but then what should I use to tell me about bad sectors using up all the space?

---

### Post by LanDan on 2007-10-17
not sure what point to mis here ;)
but if i get to the point that there are so many bad blocks that there is no space left on my drive i would start to question my believe in the sanity of that drive

does your bios have S.M.A.R.T ?

---

### Post by hardyn on 2007-10-17
run a 'badblocks' every now and again?

I don't think this is any different than windows not telling you about your harddisk unless you explicity run a suface check?

---

### Post by e_james on 2007-10-17
hardyn

I am not suggesting Windows would do any better except perhaps that, when I use the file manager, I have the staus bar continually reporting the drive free space. I also have 2.5TB of drive space and I keep filling it up. I have had several drives fail while using Windows. One was a head crash, one just wouldn't start, one would stop working when it warmed up and I have replaced 2 or three because some file transfers suddenly became extremely slow. This is the first time I have noticed accumulating bad sectors.

To further complicate matters the PC in question is not mine. It is one I set up for a friend who is new to computers. He is quite happy with ubuntu but it seems a bit much to expect him to run advanced diagnostics or even to monitor free space regularly. I believe, if my own interests were mainly email, web surfing and photographs, it might be some time before I noticed the lack of space.

---

### Post by hardyn on 2007-10-17
well your friend may right-click, properties the disk device and display the free space just the same as windows.

how small is this disk if he has to keep monitoring hard disk space? maybe you should help your friend purchase a reasonably sized hard disk?

---

