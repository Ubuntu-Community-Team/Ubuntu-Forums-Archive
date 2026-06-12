---
title: "Problem With X11 Forwarding from Ubuntu"
date: 2007-10-31
forum: General Help
---

### Post by quanticle on 2007-10-31
Hello all,

I'm having issues getting X11 forwarding to work from my Ubuntu 7.10 box.  I've checked and made sure that X11 forwarding is allowed in /etc/ssh/sshd_config.  Yet, when I try to run an X11 app (like xclock) over SSH, I get the following error: Error: Can't open display: localhost:10.0.  

I have no idea what's going on, since there don't seem to be any other config files that affect this.

---

### Post by scrooge_74 on 2007-10-31
Try this:

Go to CTRL+ALT+F2 and log in, then type

xinit /usr/bin/xterm -- :1

then ssh -Y user@the_PC_you_want_to_connect

then when you log in depending on the GUI you have installed type

startxfce4
startkde
gnome-session

---

### Post by quanticle on 2007-10-31
I don't think I was clear.  I'm trying to connect from another PC to my Ubuntu box.  I'm wondering how to allow that.

I can run X apps remotely on another machine, but I can't start X apps on my box from outside.

---

### Post by scrooge_74 on 2007-10-31
Still you are not clear enough, you want to log into your box from another box right?

do you want to have a GUI? Yes ? then do as above

No? then normal ssh will do

Do you have port forward enable on the router? 

In my home lan I can use the GUI on any of my boxes using the above commands

---

### Post by quanticle on 2007-10-31
When I try the above method, I get the following error:

*******@*********$ gnome-session
Gtk-WARNING**: cannot open display

Yes I do have port forwarding enabled on the router, and the problem is the same whether I'm connecting from another machine on the same network or from a different network entirely.

---

### Post by scrooge_74 on 2007-10-31
Did you do any other changes to the ssh config files?

did you try startx instead of gnome-session

---

