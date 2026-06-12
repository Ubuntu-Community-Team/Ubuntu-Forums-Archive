---
title: "why cant ubuntu use a vncserver that works?"
date: 2007-05-11
forum: General Help
---

### Post by ncdirtbag on 2007-05-11
hey folks, ive tried debian and ubuntu a few times and every install its the same thing..
apt-get install vncserver seems to install fine. but when I try to actually fire up vncserver?!

jason@ubuntu:~$ vncserver

New 'X' desktop is ubuntu:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/jason/.vnc/ubuntu:1.log


gripe 1:  why cant you guys fix the config file so that it uses 
~/vnc/.xstartup  like everyone else 

gripe 2:  its not really listening on port 5901  (im sure this is because of gripe 3)
jason@ubuntu:~$ netstat -an | grep 5901
jason@ubuntu:~$ 

gripe 3: WTF is with the missing fonts?!
jason@ubuntu:~$ cat  /home/jason/.vnc/ubuntu:1.log
11/05/07 16:37:19 Xvnc version 3.3.7 - built Mar  8 2007 21:58:32
11/05/07 16:37:19 Copyright (C) 2002-2003 RealVNC Ltd.
11/05/07 16:37:19 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
11/05/07 16:37:19 All Rights Reserved.
11/05/07 16:37:19 See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC
11/05/07 16:37:19 Desktop name 'X' (ubuntu:1)
11/05/07 16:37:19 Protocol version supported 3.3
11/05/07 16:37:19 Listening for VNC connections on TCP port 5901
failed to set default font path ''
Fatal server error:
could not open default font 'fixed'
jason@ubuntu:~$ 

ive been over the forums and see lots of other folks with these same issues, but never can find a real answer. 

-dirtbag

---

### Post by EvenStevens on 2007-05-11
Strange...I installed the Windows server and viewer through Wine and it works perfectly.

---

### Post by ncdirtbag on 2007-05-11
case in point, this poor guy has been waiting over 6 months for the same answer..

[http://ubuntuforums.org/showthread.php?t=273148](http://ubuntuforums.org/showthread.php?t=273148)

btw, my issue is from a fresh install of Ubuntu 7.04

-dirtbag

---

### Post by seamuso on 2007-05-11
it uses an xstartup for me ...
```

seamuso@bluebuntu:~$ vncserver

New 'X' desktop is bluebuntu:1

Creating default startup script /home/seamuso/.vnc/xstartup
Starting applications specified in /home/seamuso/.vnc/xstartup
Log file is /home/seamuso/.vnc/bluebuntu:1.log
seamuso@bluebuntu:~$ netstat -an | grep 5901
tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN
seamuso@bluebuntu:~$ date
Fri May 11 15:22:38 MDT 2007

```

---

### Post by supersigmoid on 2007-05-16
This is the reason it's not reading your ~/.vnc/xstartup:

> **ncdirtbag said:**
> 
Starting applications specified in /etc/X11/Xsession
Log file is /home/jason/.vnc/ubuntu:1.log


it should be loading ~/.vnc/xstartup, not /etc/X11/Xsession.  That is the problem.  How to solve it, I do not know ;-P.

---

### Post by supersigmoid on 2007-05-16
I've found the solution (from [this page]("http://www.experts-exchange.com/OS/Linux/Q_21303449.html")).  You have to edit /etc/vnc.conf with:

$vncStartup = "~/.vnc/xstartup"

rather than

$vncStartup = "/etc/X11/Xsession"

Then it will work just fine.  Only thing is this changes the setting for all users.  *My* question, then, is: can we set it up so that it will read ~/.vnc/xtartup if this file exists for the users but otherwise uses /etc/X11/Xsession (or some other file) as the default?

---

### Post by crimson on 2007-05-30
> **supersigmoid said:**
> *My* question, then, is: can we set it up so that it will read ~/.vnc/xtartup if this file exists for the users but otherwise uses /etc/X11/Xsession (or some other file) as the default?

Instead of making the change in /etc/vnc.conf, put your changes in ~/.vncrc and this will override the defaults in /etc/vnc.conf (which you can leave as it was, or change to whatever default you want).

---

### Post by orengolan on 2007-12-07
got the same problem.

> I've found the solution (from this page). You have to edit /etc/vnc.conf with:

$vncStartup = "~/.vnc/xstartup"

rather than

$vncStartup = "/etc/X11/Xsession"

didn't work

> Instead of making the change in /etc/vnc.conf, put your changes in ~/.vncrc and this will override the defaults in /etc/vnc.conf (which you can leave as it was, or change to whatever default you want).


can't find the .vncvrc file

---

### Post by bingoUV on 2007-12-07
1. ~/.vncrc rather than .vncvrc
2. Create it if it does not exist

---

### Post by orengolan on 2007-12-07
sudo gedit ~/.vncrc

$vncStartup = "/etc/X11/Xsession";

 sudo vncserver :1

and now I get this in the terminal:
```

New 'X' desktop is oren-desktop:1

Starting applications specified in ~/.vnc/xstartup
Log file is /home/oren/.vnc/oren-desktop:1.log

```

and this in the log:
```

Fatal server error:
could not open default font 'fixed'
/bin/sh: Can't open /home/oren/.vnc/xstartup

```

If I remove the ~/.vncrc I get this in terminal:
Starting applications specified in /etc/X11/Xsession

and the log file shows only the fonts problem.

---

### Post by gnychis on 2007-12-15
solution for me, add this to vnc.conf:
$fontPath .= "/usr/share/fonts/X11/misc/,";

---

### Post by HermanAB on 2007-12-15
The main problem with VNC is that once you finally figured out how to get it to work properly, you realize that you don't need it and that SSH is so much easier, convenient and secure...

Ferinstance:
$ ssh -X -c blowfish user@server gnome-panel

La Voila!

The trouble is that VNC solves a nonexistent problem.  You don't need to forward the whole friggen desktop - you already have one.  Just run the  program that you want to run directly over SSH, or if you are really lazy, run the Gnome, KDE or Rox panel as shown above.

Cheers,

Herman

---

