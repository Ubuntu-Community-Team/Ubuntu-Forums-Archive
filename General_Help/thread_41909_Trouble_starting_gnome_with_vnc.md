---
title: "Trouble starting gnome with vnc"
date: 2005-06-15
forum: General Help
---

### Post by gjaffe on 2005-06-15
I'm new to ubuntu and have had very little trouble configuring it.  :)

That is until I got to vnc.  I run a gnome session from gdm when I'm running locally.  I can start vncserver, and I can connect from a remote machine with a vnc client, but I just get a blank screen with an 'X' in the middle.

I tried creating $HOME/.vnc/xstartup as follows.

#!/bin/sh
gnome-session &

I made the file executable and re-started vncserser, but this did not help.

Does anyone know how to start a gnome session in a vncserver?

Thanks,

Gary

---

### Post by intangible on 2005-06-17
Check out this thread and see if it simplifies what you are trying to do: [http://www.ubuntuforums.org/showthread.php?t=41313](http://www.ubuntuforums.org/showthread.php?t=41313)

---

### Post by gjaffe on 2005-06-19
Yeah, that got it working.

Thanks. :grin:

---

