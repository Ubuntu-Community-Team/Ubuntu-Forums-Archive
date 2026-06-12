---
title: "Ubuntu Won't Boot - Get Dumped Into BusyBox"
date: 2008-06-25
forum: General Help
---

### Post by joey-elijah on 2008-06-25
Hey all - i got prompted to do a 'partial upgrade' when i was on my EeePC's Ubuntu Gutsy, so i clciked okay etc, and then it kinda became unresponsive - Firefox would 'start' but never open, same with the terminal and Update manager.

So i restarted.

Now, however, the splash screen loads a tiny bit of the load bar but then jumps to the lovely BusyBox screen!

How can i get back to Ubuntu?

The most annoying thing is, this happened once or twice before and i used to do something to get it working - some command that checked the files and got rid of loads of errors or something ....

Help?! Please?!

-- my ubuntu is on an 8GB SDHC card - eeepc 701, 4GB SSD, 2gb ram

---

### Post by rubicon on 2008-06-25
Well then, do something you've done before! Very likely it is 'fsck -y /dev/sda1'. But you should see some message on the screen when such a thing happens, just check every vtty console to be sure (Alt+1-8 ).

---

### Post by joey-elijah on 2008-06-25
i'll give it a try! do i type this into busybox?

---

### Post by rubicon on 2008-06-25
> **joey-elijah said:**
> i'll give it a try! do i type this into busybox?
Yep.

Again, before that, check logs if you can and consoles for useful messages.

---

### Post by joey-elijah on 2008-06-25
bin/sh: fsck: not found

wtf?! i'm sure this is what i did before!

---

### Post by rubicon on 2008-06-25
Odd. What about /sbin/fsck -y /dev/sda?

---

### Post by joey-elijah on 2008-06-25
/sbin/fsck: not found.

i assume that during the 'partial upgrade' when it froze and i rebooted, it hadn't got aroundt to replacing files or something... ?

---

