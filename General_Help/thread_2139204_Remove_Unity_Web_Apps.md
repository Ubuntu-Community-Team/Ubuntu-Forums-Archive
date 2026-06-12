---
title: "Remove Unity Web Apps"
date: 2013-04-26
forum: General Help
---

### Post by darkeale on 2013-04-26
Hi,

I installed the Facebook, Gmail and Hotmail Unity web apps and now I want to remove them.  I removed them from software center and tried from the terminal, and it says they have been removed, but they are still there under applications and still run when I click the icon.  Anyone know how I can remove them?

Thanks!

---

### Post by ARooster on 2013-04-28
The Unity integration web apps seem to be stored in ~/.local/share/applications/

So, to remove them:
Open a terminal window (CTRL+ALT+T)

To remove all the web apps:
Code:
> cd ~/.local/share/applications/
rm *.desktop

note that the files ending in .desktop are the Unity desktop integration web applet files so if you intend to keep some of them (removing Gmail and the rest but keeping Facebook or vice versa, for instance) instead of rm *.desktop just do a ls and delete them by rm the ones you wish to be rid of.

Or alternatively open Nautilus or another file manager to go to the above mentioned path (note that in order to find .local in your home folder you will need to enable Show Hidden Files) and delete the files, ending in .desktop as you see fit.

---

### Post by LizardW13 on 2013-05-20
Thanks very much for taking the time to explain how this is done ARooster, you explained it well and I've got rid of them now :D

---

