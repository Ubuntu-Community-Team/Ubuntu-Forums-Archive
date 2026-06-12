---
title: "Remote desktop ubuntu to windows"
date: 2008-01-01
forum: General Help
---

### Post by IPOD on 2008-01-01
Hi I was wondering if there is a way to view my ubuntu desktop with XSERVER on windows if so how?

---

### Post by dlegend on 2008-01-01
What I did (though this is from within the same network) is set up remote desktop via System > Preferences > Remote Desktop. I used TightVNC as my Windows client to connect. If you have a router you'll need to forward the proper port to your Ubuntu machine. 

Depending on the display, a different port will be used. I googled a precise answer for port number:
> 
**What port does VNC use? What is a display?**

VNC typically has one server per user running. It also typically assigns desktop (or ``display'') numbers in sequence, starting with '1' for the first instance created, as in the example in Subsection 1.4. To each desktop corresponds a port number. The port number is computed as port= display + 5900. So in the above case, the VNC server is listening for connections on port 5901.


Anyway, to download TightVNC get it here: [http://www.tightvnc.com](http://www.tightvnc.com)

If you are accessing the machine through a local network all you need to do is type in the machine name for the address. If this is through the internet then you will need to use the IP address and port.

---

### Post by IPOD on 2008-01-01
> **dlegend said:**
> What I did (though this is from within the same network) is set up remote desktop via System > Preferences > Remote Desktop. I used TightVNC as my Windows client to connect. If you have a router you'll need to forward the proper port to your Ubuntu machine. 

Depending on the display, a different port will be used. I googled a precise answer for port number:


Anyway, to download TightVNC get it here: [http://www.tightvnc.com](http://www.tightvnc.com)

If you are accessing the machine through a local network all you need to do is type in the machine name for the address. If this is through the internet then you will need to use the IP address and port.
Thanks but how I find the port and also does it have to be in my system workgroup
Its not on my workgroup but is in my network

---

### Post by dlegend on 2008-01-01
> **IPOD said:**
> Thanks but how I find the port and also does it have to be in my system workgroup
Its not on my workgroup but is in my network

If you can ping your Linux system by typing in the computer name through command prompt in windows you should just be able to type "yourcomputername" in TightVNC to connect. It will try the default port automatically which is what Remote Desktop does. Default port should be 5900 since the remote desktop is using "display 0". If you create additional servers it will be 5900 + display_number (which you probably don't need to worry about).

---

### Post by IPOD on 2008-01-01
WHat do I type in the comand promt I typed in the name of the computer but it said  (my ubuntu PC name) is not a valid comand

---

### Post by dlegend on 2008-01-01
> **IPOD said:**
> WHat do I type in the comand promt I typed in the name of the computer but it said  (my ubuntu PC name) is not a valid comand

```

ping computername

```

---

### Post by IPOD on 2008-01-01
it siad request timed out

---

### Post by dlegend on 2008-01-01
Then you will need to use the network address of your machine. The port shouldn't need to be defined but if it is then use 5900.

Or you may be able to use a syntax similar to \\workgroup\computername (not sure if that would work).

---

### Post by IPOD on 2008-01-01
I am installing it on this cpu anyways so I will just do it from there

---

### Post by MrFSL on 2008-01-01
> If you have a router you'll need to forward the proper port to your Ubuntu machine.  This is sort of misleading. If you have a router and both computers are on the internal side of this router then odds are you DONT have to set any port forwarding. If you have a router at your home and you are trying to connect from OUTSIDE your network (via the Internet for instance) then you will probably have to setup either DMZ or port forwarding.

> Thanks but how I find the port and also does it have to be in my system workgroup
Its not on my workgroup but is in my network
Workgroups don't matter for VNC.

> If you can ping your Linux system by typing in the computer name through command prompt in windows you should just be able to type "yourcomputername" in TightVNC to connect.

Again - somewhat misleading. If you can ping the computer (either by hostname or IP address) then you can reach them across the network (Step one complete). - but there are several other things you must check before you can make your connection. Correct me if I am wrong but doesn't a user have to be logged into Ubuntu for this particular VNC server to work? In Windows - Remote Desktop does not require a user be logged in. Furthermore - in Windows mutliple remote users cannot be logged in at the same time. Lastly - this is a security risk if the user is not accessing within his/her own network.

Here is some useful reading on using VNC.
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
Here is some useful reading on securing VNC using SSH
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
Here is some useful reading on an alternative VNC server that can be loaded so that a user does not have to be logged in to remotely connect. This server can also use SSL to encrypt the connection:
[https://help.ubuntu.com/community/x11vnc](https://help.ubuntu.com/community/x11vnc)

Hope this helps clarify.
Cheers
:)

---

### Post by dlegend on 2008-01-01
Thanks for providing the extra information MrFSL. I'm not too good with technicalities I just know what's worked for me and try to help where I can :)

Hope you get things working IPOD! Also, happy new years =)

---

### Post by MrFSL on 2008-01-01
> **dlegend said:**
> Thanks for providing the extra information MrFSL. I'm not too good with technicalities I just know what's worked for me and try to help where I can :)

Hope you get things working IPOD! Also, happy new years =)

No Problem! - Just the fact that you take the time to post and try to help someone else is OUTSTANDING! Don't worry if you miss some details - we're a big team here right? ;) And happy new years to you too - and to all!

Cheers

---

