---
title: "VNC help. How to make auto connect launcher?"
date: 2005-06-09
forum: General Help
---

### Post by MetalMusicAddict on 2005-06-09
I use RealVNC on windows so I was happy to see VNC in Ubuntu. I was wondering if theres a way to add the IP and password (if any) to the argument for a launcher?

---

### Post by MetalMusicAddict on 2005-06-10
No VNC users?

---

### Post by kiddyfurby on 2005-06-11
not sure about launchers, but...
xvncviewer [ip address]
would prompt password (if required), otherwise it just start the vnc session directly

---

### Post by MetalMusicAddict on 2005-06-11
Cool. That works. Can the password be added to the string? I tried but I could be getting it wrong.

---

### Post by kiddyfurby on 2005-06-11
kiddyfurby@ki-1300:~$ vncviewer -h
VNC viewer version 3.3.7 - built Oct 28 2004 23:56:22
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

usage: vncviewer [<options>] <host>:<display#>
       vncviewer [<options>] -listen [<display#>]

<options> are standard Xt options, or:
              -via <GATEWAY>
              -shared
              -viewonly
              -fullscreen
              -passwd <passwd-file>
              -noauto
              -encodings <encoding-list> (e.g. "raw copyrect")
              -bgr233
              -owncmap
              -truecolour
              -depth <depth>

perhaps passwd file means putting the password in a text file !?

---

### Post by avc on 2005-10-17
1) Write a script to launch vncviewer:

#!/bin/bash
vncviewer 192.168.1.2 -passwd ~/.vnc/passwd

(Replace the 192.168.1.2 with the IP of the computer you want to vnc to.)

2) Make a vnc password file by typing in the terminal:

vncpasswd ~/.vnc/passwd

and entering the password. This will make a file called passwd in the default location, which is inside your home folder/.vnc/

3) Finally, make a shortcut on the Gnome menubar by right clicking it, clicking Add to Panel, selecting Custom Applicaiton Launcher, and entering the full path to your script, e.g. /home/yourname/vnc.sh

Now if only vnc's fullscreen feature wasn't so hard to get out of... F8 doesn't work well when you run vncviewer with the -fullscreen option.

---

