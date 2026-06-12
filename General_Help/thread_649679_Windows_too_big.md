---
title: "Windows too big"
date: 2007-12-25
forum: General Help
---

### Post by Linuxratty on 2007-12-25
They are off the edge even and i can't grab them.
 I have a choice of two resolutions,too big and huge.
Any thoughts?

---

### Post by Rhubarb on 2007-12-25
If you can see a part of a window on your screen, you can press Alt + left drag the window so it's back on your screen.

I'm not sure quite what you're asking, please be more specific.

---

### Post by taurus on 2007-12-25
Sounds like you have low resolutions for your monitor.  Press <Ctrl><Alt>F2 and log in with your username and password.  At the prompt, reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Now, press <Alt>F7 to get back to the original screen.  Then, restart X server with <Ctrl><Alt>Backspace.

---

### Post by Linuxratty on 2007-12-25
> **Rhubarb said:**
> If you can see a part of a window on your screen, you can press Alt + left drag the window so it's back on your screen.

I'm not sure quite what you're asking, please be more specific.

Ok..The edges of the windows are off the screen so I can't see them. This means I can't see the scroll bar and the X that closes the window. I can see the arrows to the left and use the window controls on the left.
 This also happened while i was using Klikit Linux after I installed Gstreamer,but they were even bigger than this.
 Ive searched gnome high and low looking for something besides the two screen resolutions..600/
400 or 640/480...And I'm coming up empty handed.
 This is a very old monitor...A mag that was refurbished when i got it about 8 years ago...it's not a flat screen.

---

### Post by Rhubarb on 2007-12-26
Perhaps you just need to adjust some settings on your monitor?
Adjust the height and the width of your display on your physical monitor.

---

### Post by JarvidLol on 2007-12-26
Right click the little box with the name and icon at the bottom of the screen and select move.

---

