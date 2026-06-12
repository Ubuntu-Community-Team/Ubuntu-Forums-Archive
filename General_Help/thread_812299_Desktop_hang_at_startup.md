---
title: "Desktop hang at startup"
date: 2008-05-29
forum: General Help
---

### Post by myth1001 on 2008-05-29
It started with me trying to install wormux manually. I installed all the dependencies which are needed but it still wouldn't work. So, after i restarted my pc, booting process is as usual but when i log (automatic login) into the desktop, the desktop is totally empty (without icons and panel).. It shows only the background image of the Desktop Cube effect and the cube can still be rotated.

After the second reboot, the desktop is still empty, but this time with the desktop wallpaper. The desktop cube no longer working. So..what i have know is an empty desktop with a wallpaper only, movable mouse, no error messages,

I've no idea what exactly happen. :confused:Please help me to identify the source of the problem and help me to fix this..

thanks alot!!

---

### Post by myth1001 on 2008-05-29
please help.. :( anyone?

---

### Post by Nexano on 2008-05-29
i have the same problem on KDE :p

You could always try installing KDE, logging in there, and use synaptics to purge and reinstall gnome..

---

### Post by jordoncm on 2008-05-29
Were you installing wormux from source or did you find a deb package for it?

Are you able to interact with the desktop at all? Can you right click and bring up a menu? Or do any keyboard shortcuts work (ctl + alt + backspace)?

---

### Post by myth1001 on 2008-05-30
I was installing wormux from source. I can't interact with the desktop at all..not with mouse clicks. ctrl+alt+backspace will bring me out from the desktop and i will face flickering login page ( i used automatic login ).
I was thinking that compiz might be the source of the problem and i tried with the command

metacity --replace

but there's an error --> can't open X display

---

### Post by myth1001 on 2008-05-30
I've now uninstall wormux and compiz. I reset gnome configurations with this command.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

However, i'm still facing the same problem.
What should i do?

---

### Post by myth1001 on 2008-05-30
I've now uninstall wormux and compiz. I reset gnome configurations with this command.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

However, i'm still facing the same problem.
What should i do?

---

### Post by jordoncm on 2008-05-30
You could try reconfiguring X11 and/or Gnome. Boot into rescue mode and then run the following:

```
# dpkg-reconfigure xserver-xorg
```

xserver-xorg may not be the right name. It may ask you some questions but it should try to recreate a working xorg.conf file.

I am not sure what the dpkg-reconfigure package name would be for gnome (or if there is one). You could try:

```
# dpkg-reconfigure gnome
```

or

```
# dpkg-reconfigure gnome2
```

It may be able to bring the system back to a stable graphical state.

You could also always backup your home folder and reinstall.

---

