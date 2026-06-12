---
title: "[SOLVED] Screen Resolution reset to 800x600."
date: 2008-06-03
forum: General Help
---

### Post by Midnightsun on 2008-06-03
Hey guys,

Last night I switched on my computer and for the first time since installing Ubuntu it froze mid-boot.  I forced-power off and rebooted and everything seemed to work fine, however the resolution on my monitor had changed to 800x600 and I'm unable to select any resolution higher than that.  I had previously had 1200x800.  

I'm using:

Advent Laptop
15.4" Widescreen
SiS Mirage 3 Graphics (on board)

I've put a copy of my xorg.conf up here: [http://pastebin.com/f36e7d5e4](http://pastebin.com/f36e7d5e4)

---

### Post by Midnightsun on 2008-06-03
Just thought to mention - I did not have to install and proprietary drivers to get the 1200x800 resolution.  I think I had been using the basic vesa drivers?  My knowledge of these things is unfortunately a little shabby...

---

### Post by Midnightsun on 2008-06-04
Sorry to bump this guys but still getting nowhere with this problem and it's driving me insane!  I would really appreciate any advice people can give...

---

### Post by Midnightsun on 2008-06-05
OK - I solved this problem thanks to some help from a chap named Peitschie on the Ubuntu IRC channel.  Remarkably simple to fix - will post solution here in case anyone else has the problem:

1. Hit ALT + F2
2. Type:  "gksu displayconfig-gtk"
3. Click on the monitor and change to something more appropriate.
4. Log off all users
5. Log back in.
6. Do a little dance.  

Will mark this solved.

---

