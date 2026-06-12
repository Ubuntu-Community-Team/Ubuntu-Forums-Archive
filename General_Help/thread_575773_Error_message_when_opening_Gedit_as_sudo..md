---
title: "Error message when opening Gedit as sudo."
date: 2007-10-14
forum: General Help
---

### Post by omarian on 2007-10-14
Hi,

I am running Feisty Fawn with all the latest updates on 2 machines, a laptop and a desktop. Every time I try to open any files in Gedit such as:

# [COLOR="#8b0000"]sudo gedit /boot/grub/menu.lst[/COLOR]

and enter the password, I get the following lines:

[COLOR="DarkRed"]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (gedit:5169): WARNING **: Throbber animation not found

** (gedit:5169): WARNING **: Throbber fallback animation not found either
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found[/COLOR]

and then Gedit opens fine. I can even save the changes I make to files. What does this message mean? What is esd and what device is it not able to open?

Anybody have any suggestions for how to solve this?

Thank you!

---

### Post by Shazaam on 2007-10-14
Try this (gksudo) for graphical apps.... 
```
gksudo gedit /boot/grub/menu.lst
```
(small L)
You MAY get an "authentication" message, I haven't had any problems ignoring it.

---

### Post by newlinux on 2007-10-14
esd is the enlightened sound daemon 
```

man esd

```
you can probably ignore the message, but you should definitely use gksudo with graphical apps you want to run with root previleges.

---

### Post by ryanVickers on 2007-10-14
quite often when running things from the command line, as root, a toin of stuff will be appearing to be complaining about stuff, but it's actually fine ;)

for an example, type "sudo firefox" ;)  It's more English in the explanation than what you've got there, and what you've got there is the more common types of messages, but... :)

---

### Post by omarian on 2007-10-14
Thank you for replying. I ran gksudo and got more error messsages:

[COLOR="DarkRed"]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]

and after entering the password, nothing happened. Why is that?

---

### Post by newlinux on 2007-10-14
Nothing to worry about. If you take out references tto "wacom" and restart you X server you won't see those messages.

Lots of threads on it. here's one:

[http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009)

---

