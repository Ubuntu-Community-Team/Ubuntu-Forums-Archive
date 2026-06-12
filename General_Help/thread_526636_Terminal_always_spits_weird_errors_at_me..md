---
title: "Terminal always spits weird errors at me."
date: 2007-08-15
forum: General Help
---

### Post by MicroChris on 2007-08-15
Hey all,

Whenever I do anything via terminal (or Konsole, in my case :KS), I get presented with the following error:

```
chris@linux:~$ kate
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

What's causing this and what can I do? The programs start fine, it's just a little annoyance.

---

### Post by aks44 on 2007-08-15
The terminal just allows you to see messages that are otherwise hidden when you launch programs directly through the GUI.

Don't bother with that, the programs work fine in spite of those messages.

EDIT: just checked, I used to have those errors but I don't see them anywore. As a wild guess I'd say that it has to do with X.org's configuration regarding input devices (by default xorg.conf includes useless stuff). I know I removed them recently.
Anyway if you don't want to tinker with your xorg.conf that's not a problem, those messages are harmless.
Otherwise, you should remove every InputDevice you don't use in xorg.conf (remember to make a backup before modifying it).

---

### Post by MicroChris on 2007-08-15
Well I understand that, but it does it with most every command I throw at it. :(

---

### Post by ThrobbingBrain66 on 2007-08-15
Those are refering to a Wacom tablet.  Ubuntu has it enabled by default.
First, make a backup of the file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```
Get rid of those errors by editing your xorg.conf file.
```
gksudo gedit /etc/X11/xorg.conf
```
There are three InputDevice sections related to the tablet (one of them is Stylus, I don't remember the other two). Fully comment out each section (use #) and also remember to comment out the references to the sections in the ServerLayout section closer to the end of the file.  Then after a reboot, you won't get those errors anymore.

---

