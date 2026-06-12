---
title: "Accessing Ubuntu 12.04 Desktop remotely from Windows 7"
date: 2014-01-22
forum: General Help
---

### Post by TheRealJimShady on 2014-01-22
Hi all,

Our system admin guys are in the process of setting me up with a virtual installation of Ubuntu 12.04 Desktop which I will then use Windows Remote Desktop to connect too and use from my Windows 7 PC. I'd appreciate some general advice and tips about this please. For example:

[LIST=1]
[*]Once Ubuntu 12.04 Desktop has been set-up and given an ip, do I need to install xrdp to connect to it?
[*]If so, is there anything I can do to make it more responsive? I ask as we did something similar when testing a few months ago, and things like dragging windows around was a bit unresponsive (although the actual processing power was really impressive, so maybe it's a graphics thing?).
[*]Would it be better/possible for me to use the in-built remote desktop functions within Ubuntu to connect to it, rather than xrdp?
[/LIST]

Thanks

James

---

### Post by TheFu on 2014-01-22
> **TheRealJimShady said:**
> Hi all,

Our system admin guys are in the process of setting me up with a virtual installation of Ubuntu 12.04 Desktop which I will then use Windows Remote Desktop to connect too and use from my Windows 7 PC. I'd appreciate some general advice and tips about this please. For example:

[LIST=1]
[*]Once Ubuntu 12.04 Desktop has been set-up and given an ip, do I need to install xrdp to connect to it?
[*]If so, is there anything I can do to make it more responsive? I ask as we did something similar when testing a few months ago, and things like dragging windows around was a bit unresponsive (although the actual processing power was really impressive, so maybe it's a graphics thing?).
[*]Would it be better/possible for me to use the in-built remote desktop functions within Ubuntu to connect to it, rather than xrdp?
[/LIST]

Thanks

James

RDP is slow.
VNC is slow.
NX is better, but can be slow.
Spice can be faster, but seems to have other, terrible issues for some. The keyboard mappings were wrong for me.

None of these will handle video very well. Audio redirection under spice works fairly well.
I use ssh mostly, but NX if a remote desktop is really needed. Least of all the evils. [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
With Linux desktops, the only built-in remote access is X/Windows. MS-Windows doesn't have a "built-in" want to handle that. Also, it uses lots of bandwidth and is NOT secure. That makes it suitable for use only inside company networks with large pipes or on the same LAN. Forget wifi.  You'd need to load an X/Server on your Windows machine and allow the X/Clients from the remote box to connect back. The link above explains.

Oh ... xrdp is a client (seems this is, thanks SD!). Won't do you any good when you want a "server" on the Ubuntu machine.  It would be useful to connect from a Linux machine back to some Windows server, however.  I usually use rdesktop for that.

---

### Post by TheRealJimShady on 2014-01-22
Thanks for the reply.

I'm not bothered about audio. I'm going to be using it for PostgreSQL database + QGIS mainly. And I will be accessing it from within our company internal network. Windows 7 PC in company network, connecting to virtual Ubuntu 12.04 in company network. Given this, you think this right?

[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

Would be the best solution?

---

### Post by steeldriver on 2014-01-22
I've never tried NX (my work doesn't provide it) but I actually find VNC (over SSH, with a lightweight desktop session - I'm using LXDE at the moment) not too bad. I'm about 3 miles away on a reasonably fast cable internet service. There are a bunch of VNC clients for Windows including TightVNC and UltraVNC.

Xrdp *is* the RDP server btw, I've played with it a bit (including the scarygliders version) but wouldn't recommend it

```

$ sudo service xrdp start
 * Starting Remote Desktop Protocol server                               [ OK ] 

```

---

### Post by TheFu on 2014-01-22
> **TheRealJimShady said:**
> Thanks for the reply.

I'm not bothered about audio. I'm going to be using it for PostgreSQL database + QGIS mainly. And I will be accessing it from within our company internal network. Windows 7 PC in company network, connecting to virtual Ubuntu 12.04 in company network. Given this, you think this right?

[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)

Would be the best solution?

No, I do not.  

BTW, that link provides 4+ options. Which one were your thinking if a GUI is required?

The best solution from where I sit is to forget the GUI completely and use ssh. Run QGIS on the local Win7 box and just use Linux as a DBMS server. GUIs require huge amounts of system resources that are better spent on other tasks, IMHO. ssh uses very little bandwidth. You might find a useability issue, but postgres will require the same CLI knowledge to get working anyway, so having a full desktop isn't likely to help.

For my "remote desktop", I use NX daily. Actually, I'm using it right now to type this.  My main desktop is a Linux VM running on a different machine. That same VM is accessed from 2ft or 10K miles away - doesn't matter to me. Plus if there is a connection issue or I just want to reconnect to the same desktop from a different machine in a different location, NX does that ... or not. My choice.  Lastly, NX uses ssh as the tunnel protocol, which is one of the most secure methods to connect different machines anywhere in the world ... perhaps only openVPN is more secure for a mainstream solution. There isn't much concern over the security between the connections like with other remote desktop tools.

There are newer versions of VNC that show impressive results for certain types of graphics - I think those modifications break compatibility, so only specific clients work with specific servers. Plus almost all the VNC options do not include encryption and cannot use key-based authentication, so VNC connections get hacked all the time if placed on the internet without using a VPN.  Inside a LAN, the risks are less, but there are more and more LAN-side attacks these days. 

Of course, this assumes many things and that your concerns for security match mine. 

Just saw that Steeldriver is responding too - read carefully. He's very smart.

---

