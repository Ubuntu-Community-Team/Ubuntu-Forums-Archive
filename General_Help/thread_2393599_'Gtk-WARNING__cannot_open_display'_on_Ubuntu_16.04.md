---
title: "'Gtk-WARNING **: cannot open display' on Ubuntu 16.04 server with lxde"
date: 2018-06-05
forum: General Help
---

### Post by linden-e on 2018-06-05
Hello,

  The *Gtk-WARNING **: cannot open display* message is shown when I try to run LXDE with the *startlxde* command on my VPS-hosted Ubuntu 16.04 server, even with *startx*. Exporting the DISPLAY variable has no effect either. Did anyone encounter the same problem?

   Any advice or hint on how to solve this issue would be very much appreciated.

   Thank you very much.

---

### Post by spjackson on 2018-06-06
How are you connecting to the server and from what? You need to enable X11 forwarding over ssh, i.e.
```

ssh -[xXY] hostname

```

---

### Post by linden-e on 2018-06-06
Thank you for your reply. I am indeed connecting to my server with *sudo ssh [IP address] -Y* from my private IP. I have no problem connecting to the server (I am currently connected to it), but I am still unable to start lxde with the *startlxde* command. It did work after my first installation of lxde but failed after rebooting, or it takes an exceedingly  long time to respond. Here is the response I received from my last attempt to run lxde, after fourteen minutes of waiting:

[  
root@myserver:~# startlxde
Agent pid 19592

** Message: main.vala:99: Session is LXDE
** Message: main.vala:100: DE is LXDE


(lxsession:19590): Gtk-WARNING **: cannot open display: localhost:10.0
root@myserver:~# 
]

---

### Post by linden-e on 2018-06-07
The problem is now solved. It took me some time to find out that it was an iptables issue that I had missed, not an lxde one.

Thank you so much again for your help.

---

