---
title: "how i can deal with xorg and desible vga card"
date: 2008-04-18
forum: General Help
---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-18
please my keyboard and right click of mouse is off , someone tell me that i need deal with xorg and disable the vga card but he do not know how , anyone can help ?

---

### Post by jingo811 on 2008-04-18
How did your problem occur?  Was it an Ubuntu install from scratch or something else?
Which Ubuntu version did you use Hardy, Gutsy, Feisty, Edgy, Dapper?
Did you md5sum check your iso and burnt cd?

Are the cables to your mouse and keyboard loose perhaps :-)

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-18
i have ubuntu 7.04 , laptop dell 4600 , the problem occur after i press ctrl+shift+left click of mouse +space when i try to get desktop environment , after that when i move some window i see it waves like a flag , and the keyboard and right click of mouse don't work , i check this on microsoft windows and i got no problem thats mean my hardware is ok , just still i got this trouble on ubuntu

---

### Post by jingo811 on 2008-04-18
Are you playing with the Desktop 3D effects program Compiz-Fusion?  Maybe your graphics isn't setup correctly yet for 3D effects?  That can cause hardware problems elsewhere I would think.  Stopped using Compiz-Fusion circa 4 months ago it's risky business if you don't have any problems with installing operating systems every month or so that is.

If your ATI or NVIDIA isn't setup properly try ENVY it worked for both my ATI and NVIDIA machines.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by a-aaaaaaaaaaaaaaaaaaaaaaa on 2008-04-18
i can do nothing , i can' write , copy - paste , or anything

---

### Post by jingo811 on 2008-04-19
> the problem occur after i press ctrl+shift+left click of mouse +space when i try to get desktop environment 
I'm trying to see why you do the above?  When you have installed Ubuntu for the first time you get a graphical login manager correct?  Or have you customized your Linux in such a way that you can only get the GDM (graphical login manager) when you press "Ctrl+Shift-Left click mouse+Space"?
I've never encountered a situation like yours where you have to press the keyboard in such a combination to get DE (desktop environment ) working.  It has always been there even when the screen is badly configured :confused:

Try this on a terminal either on your running Ubuntu or when using your Live CD:
[LIST]
[*]**Ctrl+F2**     ; before logging in on your running Ubuntu's GDM.  When you're in textmode then login.
[*]**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_01**
[*]**sudo nano /etc/X11/xorg.conf**
[*]Press **Ctrl+w**  ; then type [COLOR="Sienna"]section "device"[/COLOR] for a quick search.
[*]You see something like this change the highlighted red part into [COLOR="Red"]"vesa"[/COLOR].
> Section "Device"
        Identifier      "Generic Video Card"
        Driver          [COLOR="Red"]"fglrx"[/COLOR]
        Busid           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection
[*]Press **Ctrl+x** to exit and choose YES to save your change.
[*]Reboot PC does your problem still exists?
[/LIST]

---

