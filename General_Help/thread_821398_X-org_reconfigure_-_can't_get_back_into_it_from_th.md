---
title: "X-org reconfigure - can't get back into it from the terminal"
date: 2008-06-07
forum: General Help
---

### Post by Jeztastic on 2008-06-07
I am making some changes to Xorg via the xorg reconfigure program. However, when I am halfway through I get put back into the black screen, and can't proceed on the reconfigure screen. How to I get back into it?

Thanks!

---

### Post by fsmithred on 2008-06-07
Are you sure you're only half way through it? With the new xorg, all you get with dpkg-reconfigure is to set the input devices (mouse, keyboard, etc.) Depending on what you're trying to change, it might be easier to manually edit /etc/X11/xorg.conf.

If you're stuck in a plain console, you might get back to a graphical desktop with ctrl-alt-F7 or with 'sudo /etc/init.d/gdm restart'.

---

### Post by Jeztastic on 2008-06-07
It's 7.10, I've not tried it in 8.04, so it's still the old version. It's definitely only half finished. I have managed to start x using startx, but I get an error message when I try to start gdm.

---

### Post by unutbu on 2008-06-07
Press Ctrl-Alt-F2 to get to a virtual console. 
Login, then type

```
ls -l /etc/X11/
```

Look for a backup copy of xorg.conf -- maybe xorg.conf~ or #xorg.conf or xorg.conf.bak.

If you have one, look inside it to make sure it looks like it has a fighting chance of working, and then type

```
cd /etc/X11
cp xorg.conf xorg.conf.20080607
cp <backupxorg.conf> xorg.conf
```

Change <backupxorg.conf> to whatever the real backup is called.

Logout. Press Ctrl-Alt-F7 to get back to X. Press Ctrl-Alt-Backspace to restart the X server. (Warning: You'll lose everything that is not saved in your current X session.)

---

