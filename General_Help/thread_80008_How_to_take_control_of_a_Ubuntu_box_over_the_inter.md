---
title: "How to take control of a Ubuntu box over the internet"
date: 2005-10-21
forum: General Help
---

### Post by Kako on 2005-10-21
Hi All,

First, I'm a beginner, well not 100% beginner as I used to run Slackware long time ago...but I have had some sort of reset since that.

Two members of my family (computer noobs) asked me to get them cheap computers. From all spare parts I have, I could build two decent computers and decided to have run free software. And therefore I decided to go Ubuntu :p 

Now, sooner or later (probably sooner), they'll call and say "I'm stuck and don't know how to do that...can you help ?". Which leads to my question: what's my best option to take over their computer through the internet ?

I know that VNC can be used but I'm not sure it is really usable over the Internet (far way too slow, no ?). Is there any other options ? (I need to be able to take control of their computer so that they can see how to do what they want).

Thank you all for your help
Kako

---

### Post by objorkum on 2005-10-21
I think VNC would be the best option (if you want to see things, if not, you can use SSH).

GNOME has built in VNC. Go to System > Preferences > Remote Desktop

I'm not sure which port it uses, but you must open a port in the router/firewall, if you have one.

I'll check Google/netstat

---

### Post by objorkum on 2005-10-21
Okay, found it out.

You just need to activate GNOME's VNC-server, and open/forward port 5900 in your router/firewall.

Which OS are you going to use to view the desktop?

Ubuntu has a built in VNC-viewer found in Applications > Internet > Terminal Server Client (choose VNC).

In Windows, download VNC-viewer from [www.realvnc.com](www.realvnc.com)

---

### Post by Game_Ender on 2005-10-21
I would check out freeNx it is the free implementation of the [NoMachine](www.nomachine.com) NX server.  You should be able to setup freeNx over ssh if you are familar with the command line.  There should be packages for the FreeNX client and server in the repository (search the forum for more help as well).  If the freeNX client gives you problem you can use the NoMachine client free of charge.  From all reporst freeNX is much, faster that VNC.

---

### Post by bionnaki on 2005-10-21
wow - I didnt realize you could do this. My mother wants to stay away from windows due to previous experience with a virus & I have recommended linux to her. She wants me to set her up, but I know she will eventually mess something up & will need help....

I'll have to look into this

---

### Post by az on 2005-10-21
Regardless of your OS, VNC and the like are a huge security risk.  Perhaps they can turn it on when they will need it?

---

### Post by RSX311 on 2005-10-21
bust out OpenSSH, and make a login for yourself.  Don't have to mess with the  GUI or anything.

---

### Post by Kako on 2005-10-24
For sure, I'd rather use SSH only, but unfortunately as they are real beginners (one has even never used a computer), I'll need to show them how to do certain things, therefore I need to be able to control their desktop.

freeNx sounds great. I'm not sure however I can control their X session. Has someone tried that already ? 

Thanks for your help
Kako

---

### Post by SickTwist on 2005-10-24
I also recommend GNOME's built-in remote desktop app. It is already installed in Ubuntu and would be very simple for your family members to turn on/off (better security for them to turn it off when it is not in use).

---

### Post by Kako on 2005-11-10
Hey,

So finally I tried the built-in VNC and really performances are quite good. It's completely usable ! 
You can just notice a slow down if there is a bitmap in the background of the remote desktop.

Cheers,
Jean-François

---

### Post by az on 2005-11-10
Yeah.   On a LAN it is as though you are sitting in front of the other screen.  Over the net (broadband, not dialup) there is only a small lag.  It is very useable.

---

