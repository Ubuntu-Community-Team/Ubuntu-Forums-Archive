---
title: "possible to rotate windows?"
date: 2006-11-13
forum: General Help
---

### Post by harty83 on 2006-11-13
This may seem stupid, but does anyone know of a program that will allow you to rotate windows?  I have a few programs that are notorious for having option dialogs that extend beyond my screen so that I can not set certain options nor can I change the size of the dialog.  My resolution is longer than it is tall so if I could rotate the window, maybe I could see the other options.

---

### Post by musicinmybrain on 2006-11-13
Can you not click and drag the title bar to get the dialogs onto the screen? If the dialog has no title bar for some reason, try holding "Alt" and clicking and dragging anywhere in the window.

---

### Post by harty83 on 2006-11-13
> **musicinmybrain said:**
> Can you not click and drag the title bar to get the dialogs onto the screen? If the dialog has no title bar for some reason, try holding "Alt" and clicking and dragging anywhere in the window.

The dialog is already at the very top of my screen and has more options "off" my screen at the bottom.  I cannot move it up anymore to see the other options at the bottom.

---

### Post by podunk on 2006-11-13
There is a little light weight app to switch desktops called 3ddesktop in the package manager - but I'd bet that the window you can't read all of is strictly on one desktop.

---

### Post by harty83 on 2006-11-13
> **podunk said:**
> but I'd bet that the window you can't read all of is strictly on one desktop.

Exactly :)

---

### Post by podunk on 2006-11-13
Usually if you re-size a window then close it, the desk manager will open it up at that size from then on. Use the nifty little trick posted by musicinmybrain. Click in the window, press and hold the ALT key, drag it around til you can see the edge.

Hover your mouse around the edge til it turns into a 2 headed arrow, and click and drag the border to make the window so it fits your screen. Click the X in the upper right to close the window and it should reopen at the last size from then on.

---

### Post by penguinchrissy on 2006-11-13
[http://ubuntuforums.org/showthread.php?t=268036&highlight=howto+beryl](http://ubuntuforums.org/showthread.php?t=268036&highlight=howto+beryl)
If you go there it will help you install a program called beryl. This program sets the desktops into a cube format that allows you to rotate between them. I've only gotten to work in drapper I tried edgy but didn't feel like messing around it is possiable though.

---

### Post by Spano on 2006-11-13
Kind of a long shot here, but it works nicely on my sytem.
Do you have a flat panel monitor that supports portrait mode?
Add this option to /etc/X11/xorg.conf
```
Section "Device"
    Identifier     "nVidia Corporation NV41.1 [GeForce 6800]"
    Driver         "nvidia"
    Option         "RandRRotation"             "true"
EndSection
```
Reboot and go to System > Prefrences > Screen Resolution.  If your vid card supports RandRRotation 
the Rotation drop down menu is enabled and you can choose left, right, inverted or normal rotation on the fly.
Not sure what cards/drivers are supported.  Might not let X start
on un-supported hardware.

---

### Post by Peepsalot on 2006-11-13
> **podunk said:**
> Usually if you re-size a window then close it, the desk manager will open it up at that size from then on. Use the nifty little trick posted by musicinmybrain. Click in the window, press and hold the ALT key, drag it around til you can see the edge.

Hover your mouse around the edge til it turns into a 2 headed arrow, and click and drag the border to make the window so it fits your screen. Click the X in the upper right to close the window and it should reopen at the last size from then on.
I would also recommend you try this.  Except the instructions here are backwards for the first step.  press and hold the ALT key, **THEN** click in the window and drag it.

---

### Post by harty83 on 2006-11-14
> **Peepsalot said:**
> I would also recommend you try this.  Except the instructions here are backwards for the first step.  press and hold the ALT key, **THEN** click in the window and drag it.

Sorry I am an idiot.  I didn't quite understand the alt thing but I've got it now and that is what I needed!  Thanks guys.

---

