---
title: "tsclient fullscreen"
date: 2005-04-29
forum: General Help
---

### Post by cdburgess75 on 2005-04-29
When I enable fullscreen on my tsclient and connect everything works fine.  But how can I escape it without killing X windows and killing the tsclient and rdesktop processes.  Does anyone know of a keyboard shortcut to switch workspace switcher sreens?  Or perhaphs to kill tsclient while in full screen mode?

---

### Post by Xerampelinae on 2005-04-29
[QUOTE=cdburgess75]When I enable fullscreen on my tsclient and connect everything works fine.  But how can I escape it without killing X windows and killing the tsclient and rdesktop processes.  Does anyone know of a keyboard shortcut to switch workspace switcher sreens?  Or perhaphs to kill tsclient while in full screen mode?[/QUOTE]
 Assuming you are using gnome, and that you haven't changed shortcut keys, you would hold control and alt, then press left, right, up, or down arrows to change workspaces.

---

### Post by cdburgess75 on 2005-04-29
Yes gnome 2.10.  That does switch it but not in fullscreen tsclient mode.  However,  I found a solution after reading your post.  ESC + left or right arrow closes tsclient
thanks.

---

### Post by jaavee on 2006-10-18
The answer to the most frequently asked question about terminal services client without killing tsclient:
  To toggle between fullscreen and not full screen, use the key combination: Ctrl-Alt-Enter.

[URL="http://www.gnomepro.com/tsclient/"]
http://www.gnomepro.com/tsclient/[/URL]

---

### Post by skirkpatrick on 2006-10-28
So how can I get tsclient to connect to another Ubuntu machine in fullscreen mode?  Whenever I try to select fullscreen mode, tsclient will return with an error and not connect.  I can connect using **vncviewer -fullscreen host:0** in a terminal but then Ctrl-Alt-Enter doesn't work.

---

### Post by XeroCurve on 2006-11-03
Hit F8 and "Quit Viewer" :)

---

### Post by skirkpatrick on 2006-11-03
Thanks, that did help.  What I'd like to be able to do is keep a full-screen VNC session running on in one workspace and be able to switch back and forth to another workspace without killing the VNC session.  Any thoughts?

---

