---
title: "[SOLVED] Restoring my filesystem"
date: 2008-04-14
forum: General Help
---

### Post by jdm2 on 2008-04-14
I really messed up my system.  I have two hard drives in my system.  One is a 160 drive that stores my vides,music,picture,etc.  The other is an 80 gb drive.  It had 2 os on it.  It had 6.06 (40gb) and 7.04 (20gb).  Last night i wasn't thinkg so I delete one of those file sytem to free up space.  Then my system crashed.  I try to access my files form a ubuntu live cd and I couldn't do it.  So then I installed it over the 6.06 since I haven't used it in 6 months.  I still couldn't access it.  I finally put in a knoppix cd.  I was able to access it.  I had it backing up to an external hard drive.  I wasn't able to get all the files since some where owned by root.  This morning I figured out how to get them.  I got some of the backed up,but I still have to finish that.  I found the area where I deleted the files ( all got deleted except for root and some others).  I just have to finish backing those up, but I was wondering if I copied those files out of .Trash and put them back where they belong, if it would work and if grub would reconize it.  Thanks for the help.

---

### Post by jdm2 on 2008-04-15
I have solved my problem.  If any of you were wondering.  I was able to access my stuff using a knoppix live cd.  Then I was able to back up my data.  I wasn't able to get to my home folder which I thought was in the /root/.Trash folder.  I then went to the terminal and did sudo nautilus and I was able to see if it was there or not.  Everything that I acidently deleted was in the .Trash folder.  I still wasn't able to access the folder.  I tried to change the permission to be able to access it and that still didn't work.  I finally figured out that all the drives are loaded as read only by default.  I unmounted the drive then I changed it to read and write then I mouted it.  I then did sudo nautilus and changed the permission on the folder.  I was then able to access the files and then I backed it up.  Then i opened a terminal and did sudo fsck.  I then shutdown and popped in an ubuntu 7.04 live cd.  I started up the cd.  I was able to see my 160drive.  I then installed ubuntu 7.04 on the entire 80gb hard drive.  I then booted up and I was able to access my 160gb hard drive :) .  I then copied over my email/firefox/etc from my old home folder into the new home folder and they worked.  I then installed the software that I was missing and did updates.  Everything is working so far.  My next step is to get everything back to how it was and to get my media support back :) .  Everything is working now I believe.  

P.S. I was having a weird issue with my 160 gb drive.  To access it,  root had to mount it.  When I clicked on it, it came up with an administrator prompt then I enter in my password and it was mounted.  I think I fix that problem by change the permissions on it.  So right now I beleive everything is working, but I was only able to get it up and running last night so I don't kow so much yet.  

P.S. I screwed up a couple of times until I got to this point.  I reccommened that everybody get a knoppix cd and if something happens to your system try that first.  I'm still a noob compared to most people, but I learned a lot from this experience.  :)

---

