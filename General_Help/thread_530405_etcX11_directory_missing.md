---
title: "/etc/X11 directory missing"
date: 2007-08-20
forum: General Help
---

### Post by haloedrain on 2007-08-20
I haven't been able to start the X server because the /etc/X11 directory, which contains the configuration file and I'm not sure what else, seems to have gone missing.  Now when X server tries to start it gives me an error message complaining that it isn't configured properly (no kidding, eh?).  How do I fix this?

---

### Post by bmartin on 2007-08-20
Try running **sudo dpkg-reconfigure xserver-xorg**.

---

### Post by Simon L on 2007-08-28
this happened to me on a fresh install of ubuntu server.

the error message i received is 

"cannot stat etc/x11/x (no such file or directory)

i tried running sudo dpkg-reconfigure xserver-xorg
the message received is "xserver-xorg is not installed and no info is available"

any ideas?

cheers all

si

---

### Post by Steveway on 2007-08-28
The Ubuntu server doesn't have a GUI installed by default.
It's a server, you don't need a GUI for that.
You can install one by doing:
sudo apt-get install ubuntu-desktop

---

### Post by Simon L on 2007-08-28
thanks for the prompt reply!

I need the gui interface as it's not just me who will be using the machine, and while i have the time and the patience to get reacquainted with the cli, others do not! (and i'm not too worried about the consequent lack of security, as it's on an internal network)

I had installed (i thought) the gnome environment by way of aptitude. then, come the reboot, it all went to pot. the x set of programs are listed as installed in aptitude.

 I'll keep on tinkering :)

---

### Post by haloedrain on 2007-08-28
It's actually really easy to set up all the additional programs that are installed with Ubuntu server, so if you get too stuck you could always do a normal install and go that route ;)

---

