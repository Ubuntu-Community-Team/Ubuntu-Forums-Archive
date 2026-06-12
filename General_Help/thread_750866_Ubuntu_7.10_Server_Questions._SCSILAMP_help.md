---
title: "Ubuntu 7.10 Server Questions. SCSI/LAMP help"
date: 2008-04-09
forum: General Help
---

### Post by atvar on 2008-04-09
Okay, First off, I have to admit that I'm a complete newbie when it comes to setting up a server or even operating Linux.. so be gentle.. lol

I've got Ubuntu Server 7.10 installed, and I have the GUI installed so I can have at least some level of familiarity with the computer. My first problem is, I can't seem to figure out how to make linux detect all my hardware. So, before I say anymore, heres my system specs as I know them:

2x 1.8ghz Xeon Processors
2x 500gb SCSI drives.
1x 40gb IDE drive. (Has the OS on it.)
1x CD/DVD RW Drive
1x Zip drive
1x Floppy drive
Video card doesn't matter.
And yes, it is an actual server computer. lol

So, my main issues are these:
1.) I cannot get Linux to detect and/or use the 2x 500gb SCSI Drives... This is a big problem, as 40gb will not be nearly enough storage for what I plan to do with this computer.
2.) It is not detecting that I have two 1.8 processors.. It only sees one Intel Pentium 4 1.8ghz.

If I can get these figured out, all should be much easier.

Also, while I'm here...

I initially set the OS to be a LAMP server when I installed Ubuntu 7.10 Server... However I can't seem to find any of the packages associated with Apache/MySQL as I had assumed would be included in the install.

I plan on using this computer to do many things.
a.) It will be serving as a server for a game.
b.) It will be serving as a web host for pages of mine and my friends.
c.) It will be serving as the in-home file server for me and my room-mate.

I don't believe this thing will see much outside traffic, so doing all three of these things shouldn't be too much of a problem.

All help would be appreciated! Thanks!

--Corey

---

### Post by Belak on 2008-04-09
Which linux kernel do you have?
Generic, or server, or something else?

This command should tell you:
```
cat /proc/version_signature

```

---

### Post by atvar on 2008-04-10
Ubuntu 2.6.22-14.52-server

---

### Post by atvar on 2008-04-27
bump:confused:

---

