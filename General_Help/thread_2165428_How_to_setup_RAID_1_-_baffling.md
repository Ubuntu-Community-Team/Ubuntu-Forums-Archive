---
title: "How to setup RAID 1 - baffling"
date: 2013-08-04
forum: General Help
---

### Post by catnip-gn on 2013-08-04
I want to setup a RAID 1 with my two, 2TB disks.  How in the heck do I do this?  I currently have 12.10 and have searched all over i-net (this forum too before it went down) and there are so many tedious ways to do this without doing a fresh install, where some sources seem to conflict with eachother.  I think the best result was to start all over with 13.04 desktop and set it up during the install - so I went thru the trials of this only to find out I couldn't!  Or - seems that I couldn't - so I went back to my 12.10.

SO - what should I do?  Get the 13.04 server edition (that was an option I believe) and then install the desktop on top of that?  Any guidance is appreciated!!!

---

### Post by newbie-user on 2013-08-05
I would've said to use the alternate install, but it seems that the last alternate installer was for 12.04. I suppose then that installing the server first, then installing ubuntu-desktop afterwards would be the way to go. I'm surprised there isn't an option for software raid in the live cd. I haven't used a live cd for installation in a long time, so I don't remember the install process from a live cd.

---

### Post by SlugSlug on 2013-08-05
Do you want the OS installed on the RAID or just data?

Install mdadm

and skip to the bottom bit of this page
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by catnip-gn on 2013-08-05
Just data.  OS is installed on separate drive.   Installed mdadm a few weeks ago and didn't  do anything for me.  Maybe inexperience?

---

### Post by SlugSlug on 2013-08-06
section 7 on above link

---

### Post by catnip-gn on 2013-08-07
No convenient way of doing it then, huh?  a lot of terminal commands and cross your fingers.  i'll give it a try I suppose.

---

