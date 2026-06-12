---
title: "Problems with .sh files in autostart"
date: 2006-09-04
forum: General Help
---

### Post by POKETNRJSH on 2006-09-04
My friend was helping me with a couple things I need to fix, and they both ended up as .sh files in /home/josh/.kde/Autostart/. One is

```
#!/bin/bash
#
ln -s /tmp/.esd-1000 /tmp/.esd
```
which is supposed to make audio in Flash work (I'm currently getting no audio.)

```

#!/bin/bash
#
xmodmap -e 'keycode 115=Menu
```
Is supposed to make my WinKey open the KMenu. This script works if I execute it in the Konsole; the flash script does not. Neither work when I start Kubuntu. What do I have wrong, and why doesn't the Flash script work?

---

### Post by x64Jimbo on 2006-09-04
What is the absolute path of the sh files? Are they set to be executable?

---

### Post by POKETNRJSH on 2006-09-04
Isn't the absolute path /home/josh/.kde/Autostart/ ? I'm not too sure on that one.

They both have -rwxr-xr-x for permissions.

---

### Post by elettronicha on 2006-09-05
As for the second problem, I created in my home directory a file called ".xmodmaprc" (without inverted commas "") containing lines like this one:
```
keycode 160 = XF86AudioMute
```
and then put in /home/myhome/.kde/Autostart/ the bash script, i.e. that one ending for .sh with a line like:
```
xmodmap /home/myhome/.xmodmaprc
```
Finally I gave execution permission to the .sh file.

---

