---
title: "Cant open terminal"
date: 2014-02-16
forum: General Help
---

### Post by whatthefunk on 2014-02-16
I broke it....again:P

I added a new startup process last night which my system apparently doesnt like.  When the desktop loads, it tries to load the new process, fails, and then nothing will open.  I need to either be able to open System Settings so I can delete the startup process, or open a terminal so I can take it out of autostart.  What can I do?

(Kubuntu 13.10)

---

### Post by tripp98 on 2014-02-16
ctrl alt f1 should take you to a login screen 

if the gui will open ctrl alt t will open a terminal

---

### Post by whatthefunk on 2014-02-16
Thanks for the response.

Ctrl Alt F1 brings up a flashing cursor, nothing else happens.  Ctrl Alt T does nothing.

---

### Post by varunendra on 2014-02-16
I think the troubleshooting steps depend upon how you added the processes to Startup. Also, I'm not experienced with Kubuntu, but in Ubuntu, the normal "Startup Application" program stores the startup files (xyz.desktop) in /etc/xdg/autostart directory.

**EDIT:** User specific Startup programs are stored in .config/autostart directory in user's Home.

So maybe boot from a live cd and modify/remove the offending ones if you have added them via "Startup Applications" (or whatever equivalent Kubuntu offers).

Otherwise it depends how you added them.

---

### Post by whatthefunk on 2014-02-16
> **varunendra said:**
> I think the troubleshooting steps depend upon how you added the processes to Startup. Also, I'm not experienced with Kubuntu, but in Ubuntu, the normal "Startup Application" program stores the startup files (xyz.desktop) in /etc/xdg/autostart directory.

**EDIT:** User specific Startup programs are stored in .config/autostart directory in user's Home.

So maybe boot from a live cd and modify/remove the offending ones if you have added them via "Startup Applications" (or whatever equivalent Kubuntu offers).

Otherwise it depends how you added them.

I tried booting from the Live CD, but couldnt access the home partition.  

I added them through System Settings, but I know that in KDE if I delete the autostart file, it will revert any changes I made.

---

### Post by whatthefunk on 2014-02-16
Got it.  Booted in recovery, mounted my home drive (I think I made a syntax error when I tried this the first time) and was able to remove the offending process.  Starts up fine now.
Thanks for the ideas guys.

---

