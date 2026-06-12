---
title: "what am i missing? - GNOME panel problem"
date: 2007-06-01
forum: General Help
---

### Post by the100thmonkey on 2007-06-01
ok, i was running Xubuntu FEISTY on my laptop, and decided to install GNOME on the system for the easy to set up GL effects. all went well, and for a while i was able to boot into XFCE or GNOME without a problem.

now, though, i have a problem - if my computer isn't connected to the ethernet cable (it doesn't currently have a wireless NIC), i get to the login screen, and i can log in OK, but i can never quite reach a fully-functioning GNOME desktop:

the panel refuses to start properly - in particular, the network monitor, desktop switcher, and other application status applets won't load.

i can't launch any programs from the panel shortcuts, or the panel menus, as far as i can tell.

the desktop background doesn't display

the splash box that displays the services that are starting seems to hang at "restricted-drivers". it appears late (along with the percussion), and hangs around far longer than it does when the ethernet cable is plugged in.

i have a home network currently comprising 3 PCs connected via a Linksys WRT54-G  router (running the Open Source firmware)

if you need more info, please ask me :)

just to be clear: 

there are no problems if my PC is connected to a live ethernet cable

---

### Post by steevols on 2007-06-01
Try booting in w/the network attached and removing the network-manager applet from your panel.

---

### Post by the100thmonkey on 2007-06-01
like this:

[[img]http://pix.nofrag.com/7b/a3/2773e538eda030bf1b87bbe666e3t.jpg[/img]](http://pix.nofrag.com/7b/a3/2773e538eda030bf1b87bbe666e3.html)

the network icon on the left at the top is the network places shortcut, not the network-manager applet. the net-manager applet usually lives on the right, next to the GL desktop icon.

same result.

---

### Post by steevols on 2007-06-01
Well, try disabling the Network Manger SERVICE from the GNOME startup services.

---

### Post by the100thmonkey on 2007-06-02
[[img]http://pix.nofrag.com/53/44/d4e7fd60a3a3d3254903ff90a328.jpeg[/img]](http://pix.nofrag.com/53/44/d4e7fd60a3a3d3254903ff90a328.html)

system > preferences > sessions?

same result.

---

### Post by steevols on 2007-06-02
Well, I'm out of ideas, but I have a question... why not just leave the NIC plugged in?

---

### Post by the100thmonkey on 2007-06-02
i would, but i'm running it on a laptop that i use for teaching.

i don't have a connection at the school, but i use it for lesson planning, and occasionally delivering Audio Visual materials.

 it was pretty embarrassing on thursday when i had to fight with my PC to get it to start, wasting loads of time... :/

does the panel component create a crash report? are there any logs i can look at to get more information? one of the problems is that since the panel doesn't start properly, the system can\t display an error message...

---

### Post by steevols on 2007-06-02
I don't know about the error logs. Did you by any chance change your usernamd, uid, or password recently?

---

### Post by the100thmonkey on 2007-06-03
i fixed it, although how or why what i did resolved the problem is beyond me.

the main obstacle was that i hadn't moved the computer for a few weeks, and consequently couldn't be sure what caused the problem.

i even went so far as to uninstall and reinstall SAMBA and ubuntu-desktop, with no effect.

in the end, it seems that Compiz or something in the GL desktop caused the problem. i figured that the last change i had made to the system before before setting up my LAN with SAMBA(hence the reinstall above), i had activated AIGLX and Compiz for the pretty. turning GL effects off had no effect, but installing Beryl and running it in place of Compiz did... :confused:

anyway, it's working fine now (as far as i can tell - it's running like it should, i suppose),

thanks for your help. :)

---

### Post by steevols on 2007-06-03
Boy, compiz... never thought of that, despite the fact that it did the same thing to me not that long ago...

Glad you got your problems fixed!

---

