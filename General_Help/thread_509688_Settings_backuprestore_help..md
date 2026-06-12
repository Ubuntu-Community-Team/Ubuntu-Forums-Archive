---
title: "Settings backup/restore help."
date: 2007-07-25
forum: General Help
---

### Post by jasdparker on 2007-07-25
Hey all, here's what I'm looking for.  Linux user off and on for years now, but I'm trying to make the transition full time away from Windows and use Ubuntu as my permanent desktop environment.

So far, in about 2 weeks, I've completed reloaded about 3 times.  The problem is that I get the desktop running the way I would like and I'm happy.

But as I look around I decide to install package ABC from Synaptics package manager I install what  I was looking for and everything seems to be fine.  It's not till later when I try to run a different application that had previously been running, it's broken because of the more recent package I installed.  I know I can do a 'remove' from Synaptics, but that doesn't always fix it.

What I'm wondering, is there any way to create a blockpoint, so that if my system every gets messed up, I can easily restore back to where it was so all of the packages and settings files are exactly the way they were at the time of the blockpoint. 

Is there a way to do this?

I've seen some options using Tar and full backups and even incremental backups of only things in the /home directory, but don't know if that will do what I'm looking for.

Any help would be appreciated.

Thanks in advance.

Jason

---

### Post by ddrichardson on 2007-07-25
I get everything set up and then use [SystemRescueCD]("http://www.sysresccd.org/Main_Page") to create an image of the partition.

---

### Post by jasdparker on 2007-07-25
Yeah, that's definitely a thought.  I was hoping for something a little bit more automated.

You know, click a button, do a backup.  Click another button and restore (maybe with a reboot involved).  I was hoping not to have to back up and restore the whole partition, but that's definitely an option to consider.

Thanks!!

---

### Post by strabes on 2007-07-26
You can use sbackup for system backups, but for preferences all you need to back up is your home folder. I do semi-daily backups of my media and home folder because everything else is relatively easy to get back because all my hardware is supported out of the box.

---

