---
title: "Remote XDMCP/Xnest problem"
date: 2007-05-11
forum: General Help
---

### Post by paulc2020 on 2007-05-11
Seem to have got everything on my Ubuntu 6.10 installation running like a dream but have run into a brick wall with remote XDMCP logins. I suspect I need to amend something in  my GDM conf but the magic tweak has so far eluded me.  

When I attempt to connect to a remote system via XDMCP from the GDM login window I just get a blank screen. The same thing happens when I use a tsclinet/Xnest combination or Xnest on its own. It also does the same thing with Xephyr.  

For example:

This works fine ...

Xnest :1 -ac -geometry 1024x768 -query localhost

Someone targeting my machine using this also works ...

Xnest :1 -ac -geometry 1024x768 -query mymachine

For me this gives a blank screen ...

Xnest :1 -ac -geometry 1024x768 -query remote-system

Colleagues of mine run the above and get presented with a dtlogin screen whereas mine is just blank.


Checked iptables ...

churcp01@pc-s031015:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I have not been able to work about how to switch on a debug option and the only output I'm seeing  seems to relates to font paths:

error opening security policy file /usr/lib/xserver/SecurityPolicy
Couldn't get keyboard.
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


Any help or pointers on this would be much appreciated

Paul

---

