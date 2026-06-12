---
title: "trouble connecting to lightDM with Xdmcp"
date: 2019-11-21
forum: General Help
---

### Post by soroushkouhi on 2019-11-21
Hi All. 
I am trying to have a Xdmcp connection to my ubuntu server using Mobaxterm on my windows PC. I have setup LightDM on the ubuntu, and created the lightdm.conf in this form: 
[LightDM]
start-default-seat=false


[XDMCPServer]
enabled=true
port=177

Now, when I use the Xdmcp, the GUI opens the login page of Ubuntu, and I enter my password in the GUI. It enters the ubuntu, but freeze there. I am not sure what is wrong. Can it be the mobaxterm problem? 
Any help is appreicated. 
Bests,

---

### Post by deadflowr on 2019-11-22
What Desktop Environment or Window Manager session are you trying to log into?

---

### Post by soroushkouhi on 2019-11-22
I guess you mean the server desktop which LightDM.

---

### Post by deadflowr on 2019-11-22
What I mean is in order to utilize lightdm you need some session to actually log into.
From the description, lightdm is working as it should.
The login screen is lightdm.
Once you log in it switches and loads whatever session was selected.
If you do not have a session to select then it would simply stop there.

Ubuntu Server edition comes with no such things.
So you need to install one of the variants I suggested, either a full DE or a window manager.

I would suggest installing something simple like openbox or i3, both are basic window managers.

---

