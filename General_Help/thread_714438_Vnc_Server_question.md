---
title: "Vnc Server question"
date: 2008-03-03
forum: General Help
---

### Post by fedex1993 on 2008-03-03
Okay i am running debian right now on my server close enough to ubuntu and i was wondering if i can have a gnome running and then ahve a vnc server so that it can be headless and can only be accessed by the vnc is that even possible?

---

### Post by SpaceTeddy on 2008-03-04
in general - yes, that is possible... but why use vnc if you have already an x-server (whoch you need for the vnc anyway) - tunnel the x though a ssh login and open the windows directly on your screen... 

but in general, of course that can be done - the output of the screen is there no matter if you have a monitor attached or not...

---

### Post by eldragon on 2008-03-04
yes, that can be done.

ive written on some post about how to do that with x11vnc (vino server seemed flawed at the time).

but as suggested, if you are under a lan, you could also set up a ssh daemon and route X to local windows. much better solution.

ive set both here at home, and use ssh X forwarding behind LAN and vnc (tunneled through ssh) behind WAN.

---

### Post by fedex1993 on 2008-03-04
how can i tunnel it threw X ssh i need like an example like all i sort of want is it for it to just show the desktop and what not sort of like a virtual box machine ecept threw a vnc server

---

### Post by bodhi.zazen on 2008-03-04
See this link :

[uwiki]VNCOverSSH[/uwiki]

---

### Post by fedex1993 on 2008-03-04
ty bodhi.zazen

---

