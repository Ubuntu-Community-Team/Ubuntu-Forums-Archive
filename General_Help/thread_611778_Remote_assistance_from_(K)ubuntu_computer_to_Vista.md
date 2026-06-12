---
title: "Remote assistance from (K)ubuntu computer to Vista computer"
date: 2007-11-13
forum: General Help
---

### Post by megamania on 2007-11-13
I need to remotely help my friend with her new Vista laptop.

I only have ubuntu (gnome+kde) plus Virtualbox, if needed.

Does anybody know what to do to get this to work? It would be extremely convenient for me.

---

### Post by az on 2007-11-13
She can install VNC on windows:
[http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)
or
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

and you can use the VNC viewer built-in to Ubuntu (I am not at home and I forget what it is:  Basically, the terminal server client-  you pick VNC from the list and her ip address...)  Alternatively, in UBuntu you can install another vnc viewer:
[http://packages.ubuntu.com/gutsy/x11/xvncviewer](http://packages.ubuntu.com/gutsy/x11/xvncviewer)

---

### Post by megamania on 2007-11-13
> **az said:**
> She can install VNC on windows:
[http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)
or
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

and you can use the VNC viewer built-in to Ubuntu (I am not at home and I forget what it is:  Basically, the terminal server client-  you pick VNC from the list and her ip address...)  Alternatively, in UBuntu you can install another vnc viewer:
[http://packages.ubuntu.com/gutsy/x11/xvncviewer](http://packages.ubuntu.com/gutsy/x11/xvncviewer)
Thanks a lot! I had used vncviewer before, but only for linux-to-linux connections.

I'll try to install it on her machine and will let you know. Thanks again!

---

### Post by az on 2007-11-13
> **megamania said:**
> Thanks a lot! I had used vncviewer before, but only for linux-to-linux connections.

I'll try to install it on her machine and will let you know. Thanks again!

Applications -  internet - Terminal Server Client.  Pick vnc....

Also, I notice that the windows version of VNC has some trouble with Vista.  I hope the trial version of RealVNC works for you.

---

