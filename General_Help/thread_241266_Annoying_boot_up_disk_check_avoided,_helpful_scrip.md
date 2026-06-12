---
title: "Annoying boot up disk check avoided, helpful script created!"
date: 2006-08-22
forum: General Help
---

### Post by musther on 2006-08-22
I know a lot of people are a little annoyed by the boot up disk check every 30 boots or so.

I've created a helpful little package with an easy installer and easy use, it scans your partitions (fsck) and then shuts down the machine, might be a good idea to run this every so often before when you leave your computer for the night.

[https://wiki.ubuntu.com/fsckdown](https://wiki.ubuntu.com/fsckdown)

---

### Post by compwiz18 on 2006-08-22
Looks cool, but can you make a way to cancel the shutdown and check in case it was clicked accidentally (yes, I did just accidentally click it :P )?

I've been look for something like this for a while, thank you :D

---

### Post by musther on 2006-08-22
The machine has to restart in order to run the fsck, but do you mean you would like it to boot up and return to the log in screen rather than power off?  If so I'll try to add that functionality soon.

---

### Post by compwiz18 on 2006-08-22
No, I like the way it shuts off when it's done, cause then I can run it before I go to bed.  What I want is at the "When you continue, Ubuntu will be shutdown..." box, put an OK and Cancel, so that when I accidentally click on it (which I did :P) I can stop it from restarting and doing the disk check (I realize now, having run it, that I can cancel at the type in your password box, but since it uses sudo, if I've used sudo in the last 5 minutes, it won't give me that option)

Thank you for all your work :D

---

### Post by musther on 2006-08-22
I've added some functionality, it is now possible to cancel in case you click on it by accident!  Also you get the chance to change the command which is executed when the check is complete, the default is 'init 0' if you send a blank line your machine will remain powered on, and you can of course issue any command you want.

Have Fun!

-------EDIT-------

Actually I can't see any reason why anybody would want to do anything special when it finishes, so now it's just a 'Do you want your computer to power down after.......'  Yes or No.

---

### Post by compwiz18 on 2006-08-23
Sounds awesome, will try it after I reinstall Ubuntu (XGL didn't fly on my computer...)  Thank you for your hard work :D

---

### Post by musther on 2006-08-23
No worries!  It's helping me hone (or at least develope) my scripting skills....

Glad you find it useful.

---

