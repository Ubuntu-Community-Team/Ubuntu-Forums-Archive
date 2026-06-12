---
title: "I sync /home in two pcs but in pc2 firefox don't open"
date: 2008-05-30
forum: General Help
---

### Post by oscar_19 on 2008-05-30
When I sync the /home of pc1 with /home pc2 firefox don't open in pc2 and in pc1 yes . I have opened in ubuntu both users with dave.
And the terminal don't open in pc2 but in pc1 terminal and firefox work. If I use alt+f4,f3..  the terminal works in pc2 but with the icon no.
Do you know how to solve this problem?

---

### Post by paulphillips on 2008-05-31
So let me get this straight (it's quite hard to understand what your problem is)...

You've got 2 pcs.  Both have ubuntu installed.  PC1 is where you are getting your "dave" user account info from, and PC2 is where you'd like to transfer your account to.
You login as "dave" on PC1 - stuff works
You login as "dave" on PC2 - stuff doesn't work (not clear what's not working... are you able to login? Are there any errors on the screen when you do?)

My first question would be whether your UIDs are the same on both machines.  I.e. cat /etc/passwd on both PC1 and PC2 and look at the "dave" line.  Are they different?

---

### Post by Zorael on 2008-05-31
Also, make sure to clear cache. Had some issues opening up firefox a while ago with a settings directory copied from a Windows partition, and this fixed it.

---

### Post by oscar_19 on 2008-05-31
yes I want transfer /home pc1 to /home pc2
I cannot open terminal and programs with their icon and firefox.
i have the same user and  password in both.
There aren't error when I click in the terminal  or in firefox or other program they try to open with the circle in the desktop and appears minimize but then dissapear.
Sorry about my english I am latin.

---

### Post by paulphillips on 2008-06-03
What happens if you try to create a completely new user on pc2?  Can that user open a terminal or firefox?

---

### Post by gug@fnal.gov on 2008-06-03
Hi,
   Are the OS installations exactly the same? If not, then just mirroring the home area from one system to another may not work. I have had problems in the past with upgrades of RedHat Linux sometimes messing up my desktop environment due to changes in window manager software. In those cases I had terminal access and was able to rename various hidden files (those starting with "." until I found the problem ones which usually were gnome related). 
    I like the earlier suggestion of testing things under a different account. Then you can also check to make sure the uid and gid match for pc1 and pc2. If that works, you could start selectively synchronizing the two pcs. 
  Step 1, rename the old /home/dave and create a new one: 
    sudo mv /home/dave /home/dave.bad
    sudo mkdir /home/dave
    sudo chgrp -R dave /home/dave
    sudo chown -R dave /home/dave

  Step 2: login and try launching a terminal or firefox. If that works then go to the selective synchronizing.
  Step 3: copy the none hidden files from pc1 to pc2 and repeat step2. (any file that starts with a-z,A-Z or 0-9). This should work.
  Step 4: Look at all of the hidden files/directories and copy a few over at a time until things stop working. Then you will have a good idea what to exclude from you synchronization in the future.


When I last had problems, these were the ones that gave me the most trouble sharing between systems or after an upgrade. 
.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

---

