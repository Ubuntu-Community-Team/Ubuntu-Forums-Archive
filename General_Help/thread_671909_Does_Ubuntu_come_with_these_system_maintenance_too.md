---
title: "Does Ubuntu come with these system maintenance tools?"
date: 2008-01-19
forum: General Help
---

### Post by Will Pittenger on 2008-01-19
Does Ubuntu come with any of the following?  If so, do you trust them?  Even though there are very few threats specific to Linux, don't tell me they don't exist.  Some Mac specific threats are showing up.  Even the iPhone was hacked into (and no, I don't mean AT&T vs. no AT&T).
[LIST=1]
[*]Firewall
[*]Virus/threat scanner
[*]Disk Defragmenter
[*]Disk checker
[*]reg cleaner -- I see that Ubuntu includes something similar to REGEDIT.  It must have a registry of some sort.[/LIST]

---

### Post by comandrei on 2008-01-19
Linux dosen't need 3/5 programs you mentioned there. If has a disk checker called fsck, and a firewall (iptables)

---

### Post by samosamo on 2008-01-19
yes it must have a registry of some sort.

check out the absolute beginner forum.  or if they have anything even noobier than that, check that out too

---

### Post by kostkon on 2008-01-19
> **Will Pittenger said:**
> Does Ubuntu come with any of the following?  If so, do you trust them?  Even though there are very few threats specific to Linux, don't tell me they don't exist.  Some Mac specific threats are showing up.  Even the iPhone was hacked into (and no, I don't mean AT&T vs. no AT&T).
[LIST=1]
[*]Firewall
[*]Virus/threat scanner
[*]Disk Defragmenter
[*]Disk checker
[*]reg cleaner -- I see that Ubuntu includes something similar to REGEDIT.  It must have a registry of some sort.[/LIST]

1. Yes
2. Yes, if you want to scan windows machines
3. Not needed
4. Yes
5. Not needed. In Ubuntu (and Linux) any configurations are saved as files.

---

### Post by 3rdalbum on 2008-01-19
> **Will Pittenger said:**
> Some Mac specific threats are showing up.  Even the iPhone was hacked into (and no, I don't mean AT&T vs. no AT&T).

Difference: Apple takes a "she'll be right" attitude toward security. The iPhone shipped with security flaws that had been discovered and fixed already in Mac OS X a while ago, and that had been fixed in MS Internet Explorer 6 years ago. Linux programmers tend to have a better idea of how to secure an operating system and write high-quality, secure programs.

> [LIST=1]
[*]Firewall
[*]Virus/threat scanner
[*]Disk Defragmenter
[*]Disk checker
[*]reg cleaner -- I see that Ubuntu includes something similar to REGEDIT.  It must have a registry of some sort.[/LIST]

1. Ubuntu comes with a firewall - it's built into the kernel. It's not necessary unless you're running server applications. Most home users have an embedded firewall in their broadband modems already anyway!

2. Virus scanner - No viruses for Linux. Adoption of Linux on the desktop goes up and up, and adoption of Linux on the server continues to increase, yet there hasn't been a Linux virus for years. I won't say that it won't happen, but I *will* say that the good guys are doing a great job in keeping track of security flaws and writing secure code to begin with.

Rootkits are a minor concern, but you can download software for that (or manually check for rootkits).

3. Disk defragmenter - simply no need for it.

4. Disk checker: Fsck has always worked well for everyone. That's included and runs automatically every 30th mount.

5. It's not a "registry" - that's a Windows invention. (to answer a later poster, no, it's not a characteristic of all operating systems). It's merely a set of XML files that Gnome uses to keep track of each user's settings. I don't see why it would need to be cleaned out - it's only got settings in there.

---

### Post by nick_h on 2008-01-19
You may also wish to read the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=510812) thread if you need more details.

---

### Post by Sidewinder1 on 2008-01-19
Will, just so you know, I was advised by someone alot more knowledgeable than I to NEVER, NEVER, run fsck on a MOUNTED file system!

---

### Post by Will Pittenger on 2008-01-19
[LIST]
[*]There are Linux based virus scanners that can recognize Windows threats?
[*]I have difficulty believing that no disk defragmenter is needed with ext3.  You might be able to make the file system resistant to fragmentation, but I still think it would happen unless the OS actively rearranges the hard drive like [Diskeeper]("http://en.wikipedia.org/wiki/Diskeeper") does.
[*]So how do you check for disk problems if you can run the program on mounted volumes?[/LIST]
I also have yet to see how to schedule programs.

---

### Post by Steveway on 2008-01-19
> **Will Pittenger said:**
> [LIST]
[*]There are Linux based virus scanners that can recognize Windows threats?
[*]I have difficulty believing that no disk defragmenter is needed with ext3.  You might be able to make the file system resistant to fragmentation, but I still think it would happen unless the OS actively rearranges the hard drive like [Diskeeper]("http://en.wikipedia.org/wiki/Diskeeper") does.
[*]So how do you check for disk problems if you can run the program on mounted volumes?[/LIST]
I also have yet to see how to schedule programs.

All virus-scanners that are avaiable for Linux are searching for Windows-viruses, but you won't need one for yourself only maybe if you want to check files prior to sending them to a Windows-user.
Most Linux-filesystems like ext3 don't fragment untill they get filled up at about 95% but even then you won't have big fragmentation and you should think about freeing space instead of defragmenting.
Don't worry, your system will check every 30 boots, you can set that to another intervall if you want it to be checked more frequently.

---

### Post by oldos2er on 2008-01-19
Most Linux AV software checks for Win* viruses.

 See [http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3) for info on fragmentation.

You DON'T run fsck on mounted volumes. The system will automatically run fsck at startup after 20 - 30 boots.

 cron or anacron can be used to schedule programs.

---

### Post by PeterJS on 2008-01-19
> **Will Pittenger said:**
> 
There are Linux based virus scanners that can recognize Windows threats?

Yep that's what all the linux AV tools are for, there are no defs for linux, as there are no known viruses to create defs for.
> 
I have difficulty believing that no disk defragmenter is needed with ext3.  You might be able to make the file system resistant to fragmentation, but I still think it would happen unless the OS actively rearranges the hard drive like [Diskeeper]("http://en.wikipedia.org/wiki/Diskeeper") does.

Ext3 is journaled, so rather than doing the writes as they happen, instead metadata is written to the journal. After the journal fills up it's written out in a way that minimizes the number of writes needed and fragmentation. Fsck is automatically run every 26 reboots as well to clean up any fragmentation that journaling can't handle. In 4 years I've only ever seen the fragmentation get above 10% once, and that was after a crash and that disk had bigger issues.
> 
So how do you check for disk problems if you can run the program on mounted volumes?

Let fsck during the boot process do it's thing, if you must fsck more often you can do so from a live cd. There's no way of checking the integrity of something that can change at any time.
> 
I also have yet to see how to schedule programs.
The scheduling tool is called cron.

---

### Post by nick_h on 2008-01-19
> if you must fsck more often you can do so from a live cd.
Or if you want to force a check on the next re-boot you can create the file forcefsck in the root filesystem.
```
touch /forcefsck
```

---

