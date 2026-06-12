---
title: "Xserver (X11 forwarding through SSH, Windows XP)"
date: 2005-09-08
forum: General Help
---

### Post by SWAT on 2005-09-08
I think this is the most-likely sub-forum in which I can post this. I'm using Ubuntu on my main PC (PC3), and using VNC/SSH to access my PC from my school securely worked fine. Now I heard about Xserver and X11 forwarding and I wanted to try it out.

So I installed [Xwinlogon](http://www.calcmaster.net/visual-c++/xwinlogon/) on my school's WindowsXP machine. Since I have a very tight configuration at home, I'll try to explain it and I hope that someone will reply and help me out a bit. 
Remember: I have VERY selective port forwarding (from PC1 to PC2), so I really need to know which port I NEED to forward (if any). 
I have 3 PC's. 
PC1: Windows XP machine (school) IP: random 
PC2: Linux PC (I connect to this one with SSH, when I use VNC) IP: 192.168.x.x 
PC3: Linux PC (my home pc, my workstation where I work on with VNC) IP:192.168.x.x 

_PC1 <---(internet)---> PC2 (tunnel) <---(LAN)---> PC3 (workstation)_
 
This way I can use VNC without problems. :D 
But how can I use this with Xwinlogon? Because I tried it with a lot of different methods, but somehow I can't get it to work.  
 
On another note, I don't even get it working on my home LAN. So which ports need to be set 'open' on the client PC (I need to configure the firewall then, in this case firestarter) etc. ?

*Screenshot of the GUI of Xwinlogon*
[IMG]http://home.hccnet.nl/s.schauenburg/Pictures/xwinlogon.jpg[/IMG]

---

