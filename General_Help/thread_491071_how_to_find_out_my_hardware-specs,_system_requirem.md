---
title: "how to find out my hardware-specs, system requirements and mp3-tag-editors"
date: 2007-07-03
forum: General Help
---

### Post by aml81 on 2007-07-03
different questions in one post:

I'm working on an used compaq desktop-pc  I got as a present about three years ago. I never got to know the hardware specs for the machine, but right now I'm curious what they are, cause every new (k)ubuntu-release (the first release I put on the machine was hoary in june 2005) the thing works more and more slowly, and right now it takes up to a minute to open firefox/ konqueror...

**question 1: How do I get to know the hardware specs of my machine? (Extra: I'm not afraid to use a shell, if I know the necessary commands!)**

as I told you: after hoary and breezy running smoothly on my machine, the system got more and more slowly between dapper and now.

**question 2: What are the hardware requirements for the different ubuntu-releases? **

I know two specs about my pc: it has 256 MB Ram (maybe it's 384), and a 160 GB HardDisk (my brother gave it to me for my birthday a few years back), I got Kubuntu 7.04 installed mainly to listen to music (amarok), surf the net (firefox), update my website (quanta) without doing  too much graphic stuff (gimp needs two minutes to open!), watch a video  now and then (mplayer!) and write my master thesis (kile and kdissert work together really well: with emacs and vim I always got the feeling to need another college degree to use the editor!). But right now I have to do some sound-work for a radio play  and I don't know what to do: Audacity is really low on features, I'm not willing to install wine just to work with adobe audition and I'm afraid my pc will jump out of the window or hang itself if I even touch ubuntustudio and/ or ardour?

**question 3: What are the system requirements for ardour?**

**question 4: Does anybody know a decent mp3-tag-editor for linux/ kde?**

I'm really lost with this: with EasyTag out of the run for crashing every three minutes and a few others with needing a mysql-database to work and others are incapabe to tag a multi-artist cd, others without establishing cddb-connections I'll never be able to clean up my music-collection.

 If anyone could help me I would be more than grateful. Any help is appreciated!

---

### Post by rainer_hubovsky on 2007-07-03
hi, 


1):

general:
$ dmesg |more

CPU:
$ cat /proc/cpuinfo

RAM:
$ cat /proc/meminfo |head
$ free -m

disks
$ hdparm -i /dev/{hda1,sda1....}

(have a look at your motherboard serial number and try google'ing it)

2):
for the last 3 releases have  a look at:
[http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)
[http://www.ubuntu.com/GetUbuntu/releasenotes/610](http://www.ubuntu.com/GetUbuntu/releasenotes/610)
[http://www.ubuntu.com/GetUbuntu/releasenotes/606](http://www.ubuntu.com/GetUbuntu/releasenotes/606)

3):
[http://ardour.org/system_requirements](http://ardour.org/system_requirements)

best regards
rainer hubovsky

---

