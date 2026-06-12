---
title: "Ubuntu Graphics are Wonky/Weird - Problematic Display"
date: 2020-12-05
forum: General Help
---

### Post by anthony-anselmo on 2020-12-05
Okay I installed the latest Ubuntu on a new machine, but the graphics are very wonky/weird. Lots of triangles and display problems.

This is an old PC machine my neighbor gave me.

I was able to install an older version of Ubuntu from a long time ago with no problems but this version I have display issues. 

Any suggestions?

---

### Post by howefield on 2020-12-05
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by anthony-anselmo on 2020-12-05
This really a PC Users forum issue.

---

### Post by ajgreeny on 2020-12-05
All your previous posts have been related to Apple machines; is this not the case with this one?

Tell us in detail what the hardware is.  "an old PC machine my neighbour gave me" is not enough to give us any real chance to help you.

---

### Post by anthony-anselmo on 2020-12-05
It is an old PC with Windows XP on it, probably 2002? AMD processor, MSI is all I know.

---

### Post by ajgreeny on 2020-12-05
Moved back to General help as not Apple hardware.

Assuming you can boot to Ubuntu, please use Ctrl+Alt+F4 to get to a tty command line, login with username and password (typing password will not show anything on screen, not even asterisks) and then run command ```
inxi -Fzx
``` and post the output back here.

As the computer is from 2002 I suspect it will not have sufficient resources to run Ubuntu, but it may just about be possible to run Xubuntu or Lubuntu if it is definitely 64bit.
If it's only 32bit you will have to use something else as none of the Ubuntu family of OSs are available now as 32bit images.

---

### Post by anthony-anselmo on 2020-12-05
I got command inxi not found

---

### Post by ajgreeny on 2020-12-05
OK, so run these two commands from the tty you used before ```
sudo apt install inxi
``` to install inxi then ```
inxi -Fzx
``` to find the hardware.

---

