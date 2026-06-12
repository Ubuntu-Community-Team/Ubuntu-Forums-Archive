---
title: "Some observation"
date: 2007-10-19
forum: General Help
---

### Post by jmgtan on 2007-10-19
With gnome in general, or kde for that matter, even with the same resolution 1280x800 and the same dpi: 96dpi, everything appears larger than windows... maybe am missing something, it just takes up too mch screen real estate

---

### Post by yabbadabbadont on 2007-10-19
What is the output if you run, in a terminal window, the following command?
```
xdpyinfo | grep -i resolution
```

---

### Post by jmgtan on 2007-10-19
thnx for the reply, The result is: 100x100 dots per inch, how do you change this? Why is it not following the one in the Appearance window

---

### Post by yabbadabbadont on 2007-10-20
Because whichever devs are in charge of the Xorg packages decided, in their infinite wisdom, to include "-dpi 100" as a parameter when starting the X server in /etc/X11/xinit/xserverrc.  :x  This forces the X server to **always** use 100 DPI no matter what you set elsewhere...  You'll need to edit that file and remove the option, then restart X in order for the correct DPI to be used.

Edit: Assuming that you have the default Gnome setup installed, hit Alt-F2, then run "gksudo gedit /etc/X11/xinit/xserverrc" to edit the file.  You have to use gksudo (for a graphical editor) or sudo (for a terminal based one) in order to have permission to save your changes to the file.  Here is what mine looks like **after** I removed the DPI option:
```
/home/daffy $ cat /etc/X11/xinit/xserverrc 
#!/bin/sh
exec /usr/bin/X11/X -nolisten tcp

```

---

### Post by jmgtan on 2007-10-20
Ok this is really weird, I tried what you said, i've removed the -dpi argument in the file, but after restarting the X server, i'm still stuck at 100x100 dpi, also tried putting -dpi 96, still the same output.

---

