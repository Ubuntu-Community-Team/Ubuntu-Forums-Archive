---
title: "complete freeze"
date: 2006-07-30
forum: General Help
---

### Post by Chuck_W on 2006-07-30
For the first time my Ubuntu box totally froze. Firefox was running in the background and I had just started Celestia. When I tried to use the search function a dialog box opened and the mouse cursor disapeared. Nothing I tried on the keyboard worked. Finally had to turn off the power strip. Is there a log somewhere that might give me some idea as to why it locked up? Also, is there anything I should do when I start the computer again to repair any damage that might have been done?

Thanks

---

### Post by NewbieNik on 2006-07-31
Not sure on the log or help files, but if it locks up again try pressing the control+alt+backspce (Not del) keys, this should restart the X-server and closes any graphical environments, safer than powering off. (If your keyboard was working!)
I've had this before and it was because there was a text box open behind the window, but I couldn't move the window until I OK'd the text box....really annoying.

---

### Post by vierranet on 2006-08-03
I have been dealing with this issue for the past two weeks, and to the point of pulling out hair, but this is what I came up with for now. 

The issue isn't in FF but in X with the new kernel, this what I came up with.

Back up stuff, reinstall OS, when update notification pops up, click show updates and un-check everything that has to do with the X and the kernal update. 

It's only a quick-fix work around, but it works. No more freezing, hard boots, or hair loss.

Vince

---

