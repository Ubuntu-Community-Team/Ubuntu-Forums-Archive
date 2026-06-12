---
title: "Connect to a certain session of X remotely"
date: 2014-11-06
forum: General Help
---

### Post by Csaba_Bodis on 2014-11-06
So I have a machine for which I have no keyboard and mouse.
It's running Ubuntu and I use it via ssh.
I'm using it partially as a torrent server so I though to connect it to my tv and watch movies from it directly.
If I boot it up I can see the logon screen on the tv. If I run 'startx' via ssh from my laptop I can see that the X starts on the TV. But I can't have control.
I tried with xrdp and tightvnc server, and though I could connect to my system I couldn't use that very session I see on tv. These are creating virtual X sessions.
So is there a way to connect remotely to that session?

---

### Post by ringstaart on 2014-11-06
I think the first method in this tutorial would be enough:
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)
It would let you control the X session from the command line. If you use a video player with proper keyboard control from the terminal, like mpv, it would probably be usable for what you need it for.

I haven't tested it myself.

---

### Post by Csaba_Bodis on 2014-11-06
Thanks but I could rather use a graphical solution.

---

