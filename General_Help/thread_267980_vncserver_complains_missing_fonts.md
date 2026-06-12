---
title: "vncserver complains missing fonts"
date: 2006-09-29
forum: General Help
---

### Post by javaperl on 2006-09-29
here is what i got:

[FONT="Courier New"][COLOR="Black"]xwang@home7:~$ vncserver
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.

29/09/06 10:15:56 Xvnc version 3.3.tight1.2.9
29/09/06 10:15:56 Copyright (C) 1999 AT&T Laboratories Cambridge.
29/09/06 10:15:56 Copyright (C) 2000-2002 Constantin Kaplinsky.
29/09/06 10:15:56 All Rights Reserved.
29/09/06 10:15:56 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
29/09/06 10:15:56 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
29/09/06 10:15:56 Desktop name 'X' (home7:1)
29/09/06 10:15:56 Protocol version supported 3.3
29/09/06 10:15:56 Listening for VNC connections on TCP port 5901
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
29/09/06 10:15:57 Xvnc version 3.3.tight1.2.9
29/09/06 10:15:57 Copyright (C) 1999 AT&T Laboratories Cambridge.
29/09/06 10:15:57 Copyright (C) 2000-2002 Constantin Kaplinsky.
29/09/06 10:15:57 All Rights Reserved.
29/09/06 10:15:57 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
29/09/06 10:15:57 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
29/09/06 10:15:57 Desktop name 'X' (home7:1)
29/09/06 10:15:57 Protocol version supported 3.3
29/09/06 10:15:57 Listening for VNC connections on TCP port 5901
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring

Fatal server error:
could not open default font 'fixed'
[/COLOR][/FONT]

---

### Post by dannyboy79 on 2006-09-29
i am a newbie and was curious about the thread so I peeked in. well, from reading your error why don't you first go to your terminal and type in 
sudo find / -name Speedo 
NOTE: captial and not captial letters matter in linux.
once you find the font, set correct fontPath in the vncserver script. if you don't know what the vncserver script is than just look around in nautilus for something that might be like "xvncserver.conf" or something like that, once you find that do a 
sudo gedit /blah/blah/filename and add the path to the Speedo font. 
I am trying to help and if I haven't by any means than I am sorry for wasting your time. It's just I am work and kind of bored, i sometimes just look thru the ubuntu forums and find threads that I could maybe help on and since I have tried xvncviewer before I thought I would read what problem you were having with xvncserver but I can't help you more than what I have guessed. Sorry, good luck.

---

### Post by florisla on 2006-11-06
I had this issue as well... Unfortunately, I have not solved it either.

What did work for me, was to install tightvncserver instead of the usual vncserver.  And then, by editing /usr/bin/tightvncserver , I could set all the font paths to their actual locations.  After that, the errors in the vnc logs were gone and I could start a vnc session to localhost.

---

### Post by florisla on 2006-11-06
By the way, shouldn't we report the error with the missing 'fixed' font somewhere?  Vncserver does not appear to be listed in Launchpad -- is that because it is part of Universe?

---

