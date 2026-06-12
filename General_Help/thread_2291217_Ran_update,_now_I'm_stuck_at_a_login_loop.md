---
title: "Ran update, now I'm stuck at a login loop"
date: 2015-08-18
forum: General Help
---

### Post by Speedwagon on 2015-08-18
I ran an update on Ubuntu 15.04 this morning, and it asked me to do a reboot to finish. So I did, and now I'm stuck with a login loop. Ctrl+alt+F1 gets me to a black screen with no command prompt. Advanced mode, previous kernel(?) will allow me to login, but I get no menu. I have a dual monitor setup, and when I boot normally now, the display is mirrored instead of panning across both. So it would appear this might be a driver issue.  How do I solve it though?

---

### Post by Theeboon on 2015-08-18
I had the same. I guessed it was my graphics driver (.xsession-errors had some GPU-related messages). You have ATI graphics, right? I tried reinstalling fglrx, even installing fglrx-updates instead, but both just wouldn't work. In the end I just removed all fglrx-related drivers and now it logs in again.

Seems to be something wrong with fglrx. I didn't see if it was updated today though, as I wasn't around when the updates were initiated.

---

### Post by Speedwagon on 2015-08-18
I do have ATI, yes. I found a command through a search to use purge to remove that, but it gave me an error that purge didn't exist.

---

### Post by Theeboon on 2015-08-18
Try this: 

sudo apt-get remove --purge fglrx fglrx-core fglrx-amdcccle

---

### Post by Speedwagon on 2015-08-18
Got it to remove the packages, and got rid of my login loop. So I can login, but I don't have a menu now, and a ctrl+alt+t did not get me a terminal. Though I did figure out I can right click to open a terminal window.

---

### Post by Theeboon on 2015-08-19
Try a sudo apt-get install ubuntu-desktop.

---

### Post by Speedwagon on 2015-08-21
Got it all back to normal. Thank you for the help.

---

### Post by v3.xx on 2015-08-21
This question is popping up often.  What was the solution?

---

### Post by Speedwagon on 2015-08-21
I just followed the steps in this thread and got it to work.

---

