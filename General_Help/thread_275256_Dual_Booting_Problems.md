---
title: "Dual Booting Problems"
date: 2006-10-11
forum: General Help
---

### Post by TrendyDark on 2006-10-11
I often switch back and forth between just using Windows and dual booting with Ubuntu, and I've noticed a recurring problem with dual booting. . Windows (or NTFS most likely) seems to have a problem with sharing the disk with a Ext3 file system or something to this effect.

My problem is that all my setting in applications such as Firefox, AIM, TeamSpeak, Xfire, etc. on Windows seem to constantly reset themselves. 

I'm a social bookmarker for Netscape.com and I use RSS avidly, I can't have to keep going through and re-bookmarking my RSS feeds every other day.

Is there any suggestions one may have to fix this problem? Maybe running chkdsk /r /f will help out?](*,)

---

### Post by ajgreeny on 2006-10-11
No problem here.  Do you use (or try to) the same profile for both windows in ntfs and ubuntu in ext3 file systems or are they separate profiles on each system?  Don't forget, windows can read ext3 file systems only if you have an appropriate windows utility on that ntfs partition.  Ubuntu can read but not write to your ntfs wondows partition, so that may be the source of the problem if you are trying to use one profile for firefox.

If you want to share the same files between the two systems you will need a separate /home partition inubuntu formatted as fat32, which is read and write enabled in both file systems (ntfs and ext3).

It is a bot complicated to do it now when you seem already to have your home files all set up but it is not impossible.  There is a wiki on the subject if you go to:-
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

Good luck, and don't give up on ubuntu, it's really great!

---

### Post by TrendyDark on 2006-10-11
No sir, not sharing at all. The Ubuntu installation always stays nice and clean, but for some reason when I have Windows and Ubuntu on the same drive all my Windows profiles disappear at random times.

Most recently my Firefox profile reset itself, deleting over 100+ RSS feeds and bookmarks, etc. I wasn't happy -_- :P

---

### Post by ajgreeny on 2006-10-11
OK. Sorry, then, but I'm baffled and can see no way that either system should upset the other just by being on the same disk.

---

