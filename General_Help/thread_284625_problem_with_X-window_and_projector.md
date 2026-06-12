---
title: "problem with X-window and projector"
date: 2006-10-25
forum: General Help
---

### Post by linux&gt;mac on 2006-10-25
I have a Toshiba satellite Pro 6100 with nvidia graphics card, but when I connect a projector to the VGA output and hit Fn+F5, there is no output to the projector and the X-window is screwed up. The only way I can use the projector is that I connect the project and restart the computer. Although there has output to the projector, but there is nothing in the compuer screen!  Does anybody meet the same problem?

---

### Post by line72 on 2006-10-26
I've had similar problems on my dell laptop were the fn+f5 doesn't work correctly.  What I did was setup TwinView in clone mode.  This isn't perfect, but works pretty well for me.  Add the following to your Screen section in your /etc/X11/xorg.conf (and make sure you are using the nvidia, not nv driver)

Option "TwinView" "True"
Option "TwinViewOrientaiton" "Clone"
Option "MetaModes" "1600x1200, 1600x1200; 1280x1024, 1280x1024; 1024x768, 1024x768; 800x600, 800x600"

You might want to add a few more resolutions in the MetaModes depending on your laptop and also the projector.  This will always show a picture on your laptop screen and will also show one on the projector if it is plugged in.  If you plug in the projector after X has started, you will need to restart X (ctrl+alt+backspace).  Also, this won't automatically detect the resolution of your projector, so you may need to login and lower the resolution before it will show up.

---

### Post by T_W on 2006-12-13
This worked for me with one change:

> Option "TwinViewOrientaiton" "Clone"

Should be 

> Option **"TwinViewOrientation"** "Clone"

Slight misspelling of "orientation" in original message.

After setting this up, I needed to:

1) Restart X with the external monitor/projector connected (Ctrl+Shift+Backspace).
2) I also had to hit the "CRT/LCD" key on my laptop.

---

