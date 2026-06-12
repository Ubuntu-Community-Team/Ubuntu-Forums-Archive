---
title: "Fixed 'boot record matching backup error' Now system stalls after disk chk on boot..."
date: 2007-05-07
forum: General Help
---

### Post by JungMin on 2007-05-07
I recently switched from Suse to Ubuntu 7.04.  Everything has been going fine for the most part.

My system had been running for the past 5 days or so....I got home from work last night and the Desktop was running VERY SLOWLY.  rebooted and it gave me the an error about 'boot record not matching backup'.  I searched around on here and changed the entry in the fstab from 1 to 0.  Now that error is gone....

Now, the system finishes the disk checks and stalls.....I think it stalls after checking the /home partition.  If i hit Ctrl-Alt-Del it loads up the 'Login Screen'.  When i try to login, it says that /home/jungmin doesn't appear to exist.  It says i can try to login as root, but if i try, it just kicks back to the login screen.

If I load up the Ubuntu CD, it sees all the partitions and i can browse them all.

I havent changed/edited anything in the system in weeks.  I have no idea what caused all of these errors last night!!??!?!?  It seems to have just happened.... (with other distros, i have screwed things up by editing files, installing stuff, etc....but here i have done NOTHING!!)

Any ideas??

---

### Post by JungMin on 2007-05-07
Well....this has been a weird few hours.  I rebooted a few more times.....ran 'fsck' on all the partitions manually...rebooted a few more times, then finally it booted up.  It checked a disk again on boot, then displayed 'fsck died with exit status 1'.  I think that means it corrected some errors.

So, I have no idea what caused the errors.....nor do i have any idea how it fixed itself.  But all is ok....for now.

---

