---
title: "Lock screen while remote desktop VNC"
date: 2008-05-17
forum: General Help
---

### Post by mohamedx5 on 2008-05-17
Dear All
I am using VNC to remote desktop from windowsXP in home machine to Ubuntu machine in my office, but my friends in office can see the ubuntu desktop while Iam using it from home, how can I lock the screen while I remote desktop on it?

---

### Post by aml on 2008-12-11
I don't think so. When I need to start a new session remotely I either launch the apps directly by tunnelling X over SSH, or starting a new X session and VNC'ing into that.

It is a major missing feature that you can not remotely connect to an existing X session at the local console and have the screen lock automatically. This is trivially easy to do in Windows.

The best I can come up with (as of Hardy) would be to only ever use VNC sessions. For example, when you want to work at the local machine, start a VNC server, then start a very basic X desktop, and connect a VNC client to the local machine. Then you can connect disconnect the local client and VNC in remotely to your existing session without any of it being displayed on the screen. Clunky, inelegant, and something that will hurt linux adoption in the workplace.

Does anyone know if this is going to be fixed, or even recognized as a problem?

---

### Post by feoras on 2008-12-17
That's a real pity.  I would really like this facility too.  I guess I'll just have to open a second X instance.

---

### Post by st1710 on 2009-10-28
Rather than sharing your desktop, you probably want to start another VNC server session on a different display. 

Then, assuming you are using a normal gnome session on VNC, then you should have an instance of gnome-screensaver running. If not you can add it to your start-up apps, or start it manually once you have started your vncserver, from the command line.

To lock the screen you need to do a "xdg-screensaver lock" command. You can simply add a new button to your panel with that line as the command. I usually pick a little padlock icon.

Of course, if you have a user switcher applet running already - as you probably do - then you can just click on the lttle green man and select lock screen. So, you don't need the new button, but I find it more convenient. 

In either case - you just need gnome-screensaver to be started. It may spew errors when it first starts, but it doesn't seem to effect operations.

---

### Post by magneze on 2009-12-15
Aha, this sort of answers a query I had. I have the same security concern.

How do I start a new Xsession and connect VNC to that?

</newbie>

---

### Post by cj13579 on 2009-12-15
This is possible and is really easy:

[http://ubuntuforums.org/showthread.php?p=8503523](http://ubuntuforums.org/showthread.php?p=8503523)

---

