---
title: "problems with wine... I think..."
date: 2007-04-12
forum: General Help
---

### Post by malder on 2007-04-12
A couple days ago (after working fine for months) opening picasa logs me out. I then tried another wine program (keepass) and it did worse - black screen with solid cursor in upper-left corner. Had to do a hard reset. I looked through the logs I know of, but nothing seemed to be pertinent to my somewhat unschooled eyes.

Today I clicked on the little yellow/orange star icon to upgrade packages and when I scrolled down the list of packages it did the same thing! Logged me out. Well, I logged back in and did an 'apt-get upgrade' from the command line and everything seems to be fine.

Ubuntu has been working flawlessly for me for about 6 months, so this seems to be totally out of the blue. I've tried updating everything (I use Automatix2 for wine/picasa), but no change.... :confused: 

Where should I start looking? 

Thanks!

Matt

---

### Post by Loafy on 2007-04-22
I'm having the exact same thing here. Ubuntu 6.10 working fine and so was Picasa. Now it logs me out each time I start it.

Maybe a recent update is causing some conflict?

Wish I knew....

---

### Post by Loafy on 2007-04-22
update:

I seached a number of forums and tried a few new things - if I use the older version of Picasa found at [http://picasa.google.com/support/bin/answer.py?answer=26902&query=windows](http://picasa.google.com/support/bin/answer.py?answer=26902&query=windows) in either WINE or Crossover then everything seems to work. It's not the Linux version but it seems to work under emulation with they typical caveats.

This version is for ME and Win98 but is a version 2.x of Picasa. Seems that something has changed with the app or a new update for Ubuntu is now causing a conflict.

HTH

---

### Post by malder on 2007-04-23
SOLVED:

It actually ended up being the video driver I was running. Even though Ubuntu in general had no video issues the driver was still crashing just wine. Updated the video driver via Envy script and all is working as it should.

---

