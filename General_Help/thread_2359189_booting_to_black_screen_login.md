---
title: "booting to black screen login"
date: 2017-04-21
forum: General Help
---

### Post by jgw on 2017-04-21
I am booting to a black screen login.  My problem was that I was trying to get a hard disk to boot at startup.  That really screwed things up.  So, then, I went to /etc,  switched the file system from ro to rw, removed fstab and copied fstab.bak over to it.  Now the machine is only booting to a black screen.  

I logged into the black screen, did an "su",  then did "mount -o remount rw /"  the machine looked at me for a couple of minutes and then booted to a guest account.  I logged into that and then the entire system came up.  Then, I rebooted and was forced to go through the entire thing again.  I also remember I did a recovery boot instead of the regular.one.  While I think I was dealing with the current system it looks as if I am really dealing with the previous iteration.  So, I went to synaptic, fixed broken packages and then checked for updates and updated 12 packages.  I looks ok but I think I am still a guest and will try and fix that.  

Ok, I have re-booted.  I had to login on the black screen, then 'su", then did "mount -o remount rw /", at which point it started up.  I got rid of any guests so, this time, I just logged in.  Then, for the heck of it, I brought up the system monitor and found that I have the following running:
    upstart-udev-bridge 
    upstart-file-bridge
    upstart-dbus-bridge
    upstart-debs-bridge
    upstart
which I think is not right.

What I need are thoughts on this one because I think I have a problem. 
Anyway - appreciate any thought and/or suggestions on this one. 

Thank you...............

---

### Post by jgw on 2017-05-03
I give up on this one as there seems to be no replies.  Instead I have re-installed ubuntu to take care of the problem.

---

### Post by QIII on 2017-05-03
A better approach might have been to bump your post after 12 hours to get up to the top again.

A week is time enough for a post to sink to the bottom, settle into the ooze and be forever lost from human memory.

---

