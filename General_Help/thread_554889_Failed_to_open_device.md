---
title: "Failed to open device"
date: 2007-09-19
forum: General Help
---

### Post by Damad on 2007-09-19
How can I fix this? 

dustin@theaxebox:~$ konsole
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by apetresc on 2007-09-19
This is a perfectly normal "error". It is caused by this: in the default xorg.conf file, there are entries for Wacom input devices (stylus, tablet, eraser). However, most computers *do not* have these devices, so that error results. It does not actually cause any problems, it is more of a warning than anything else.

If the problem really bugs you, it is fixable. Open up your /etc/X11/xorg.conf file, find the lines:
```
InputDevice     "stylus"        "SendCoreEvents"
InputDevice     "cursor"        "SendCoreEvents"
InputDevice     "eraser"        "SendCoreEvents"
```
And comment these out with "#". Then restart X and these "errors" will be no more :)

---

### Post by Damad on 2007-09-19
So, i have been told that this is something i should just be able to ignore, but it prevents programs from opening. The only time i get this message is when a program won't open, and when they do open, i never get this messsage. Sometimes I get this message when I open a program from the terminal, but the konsole will never open and other programs will sometimes never open either.

EDIT: many thanks for your help, AdrianP, i'm giong to try this now.

---

### Post by apetresc on 2007-09-19
> **Damad said:**
> So, i have been told that this is something i should just be able to ignore, but it prevents programs from opening. The only time i get this message is when a program won't open, and when they do open, i never get this messsage. Sometimes I get this message when I open a program from the terminal, but the konsole will never open and other programs will sometimes never open either.

That's really weird, and shouldn't happen. There is probably a second, unrelated problem at work. Do my fix with commenting out the entries from xorg.conf and let me know if the applications open now. (Please let me know even if they *do* start working! :))

---

### Post by Damad on 2007-09-19
Commenting out the entries did indeed fix the "errors" but the konsole still will not open. It is the only program i recall having problems like this with, and I recall also having similar troubles running Amarok, all though it would open not as often, usually after a restart of X. Is Konsole a KDE program, and would me running it in Ubuntu have anything to do with it? Usually it runs just fine, though.

EDIT: I'm having the same problem with Amarok as of right now. The process will open but the program itself will not.

---

### Post by apetresc on 2007-09-19
> **Damad said:**
> Commenting out the entries did indeed fix the "errors" but the konsole still will not open. It is the only program i recall having problems like this with, and I recall also having similar troubles running Amarok, all though it would open not as often, usually after a restart of X. Is Konsole a KDE program, and would me running it in Ubuntu have anything to do with it? Usually it runs just fine, though.

EDIT: I'm having the same problem with Amarok as of right now. The process will open but the program itself will not.
That is bizarre :confused: Even though they are KDE apps, they should run just fine in the Gnome version of Ubuntu.

You should probably create a new thread, since this is a new problem - your applications are not starting :(

---

### Post by Damad on 2007-09-19
Thank you for all your help!

---

