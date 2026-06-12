---
title: "Remote Support for Beginners"
date: 2008-05-17
forum: General Help
---

### Post by walding on 2008-05-17
Hi,

My parents have Gutsy on their PC (dual-boot with WinXP).  
When in Windows, I can arrange easy remote help through Windows "remote assistance" feature, that works via MSN LIve MEssenger.  Works fine, without any configuration on their part.

When in Ubuntu, I can't succeed in connecting to them.  We tried the "remote desktop" option, but I can't connect via VNC.
Is there an easy way to do it?  It can't involve them doing any CLI stuff.  They are complete novices, and are stuck with a few things in Ubuntu.

Any suggestions welcome!

Cheers,

AW

---

### Post by Aearenda on 2008-05-17
The problem for Ubuntu->Windows is that the Windows Remote Assistance feature needs client-side smarts that Ubuntu doesn't have - it isn't plain RDP during the connection phase. However, the Terminal Server client in Ubuntu can use RDPv5 to connect to Windows XP Professional if the Remote Desktop feature is turned on on XP. It uses port 3389, and you'd have to tell the router/firewall to forward this to the PC. Home edition doesn't allow this at all, and it's not really something I'd want to leave open on the firewall all the time.

To connect to Ubuntu using VNC from Windows or from Ubuntu, they need to have Remote Desktop turned on in System->Preferences, and they need to have their firewall/router/whatever forwarding port 5900 (I think) to their computer. However, this is not secure unless you turn encyption on in the advanced settings, and I would think twice about allowing it over the internet in clear. An SSH tunnel would be better, but needs some setting up. Once done, there would be no need for command line work at their end. 

In practice, I just run SSH to my remote sites, and use ssh -C -X if I need to start a graphical app - this can include the vnc client looping back to the desktop of the target machine. I avoid the script kiddies by using a high port number, and I use a key with a passphrase rather than a straight password for authentication. Again, the firewall needs to forward the chosen port to the target computer, but the port number is your choice this time. I think Cygwin may allow a similar approach for contacting Windows, but have never tried this.

Lots to think about - none of it easy, I'm afraid. Maybe you'd be better off using one of the web sites that mediate this kind of thing.

---

### Post by walding on 2008-05-17
Thx. 
If I can connect, however insecurely, for the few minutes it takes to set them up with SSH, then I can disconnect and reconnect securely.  The problem I have is that I'm 90 miles away with a dodgy leg that's preventing me driving (or walking, presently!).

Something a little easier on Ubuntu would really give Ubuntu a boost, allowing novices the confidence to take the plunge with the comfort that remote assistance is just a click away.    At the moment, my parents have been reverting back to Windows.

---

### Post by Aearenda on 2008-05-17
The bit that makes it hard is configuring the router/firewall - I think RA on Windows uses UPNP to open a port automatically if it can.

I think I would proceed as follows:

1. Get your parents to boot Windows, and you use Windows to commence a Remote Assistance session so you get to control their PC.
2. Use IE on their machine to configure their router firewall to forward port 5900 to their PC.
3. Install a vnc service that allows encryption on their PC - I haven't looked recently, it would be worth doing some local testing at home to see what works with Ubuntu's vnc client. Check the Windows firewall allows 5900 through as well.
4. Install the relevant vnc viewer on your pc, and make sure you can connect to their PC using vnc instead of RA (all still on Windows).
5. Reboot your PC to Ubuntu and check that you can use the vnc viewer there to connect to their PC, still using Windows.
6. Reboot their PC into Ubuntu and get them to log on.
7. Check that you can still connect to their PC using vnc.

At this point, you have what you want, and so long as all the vnc software supports encryption, it should be safe enough for this purpose. You can use vnc for all remote control sessions, and it doesn't matter which OS is running at either end. I would want to create a desktop icon on both Windows and Ubuntu that enables the vnc service on your parents PC so it does not run all the time, allowing your parents to turn it on when needed.

If performance is good, you may not need SSH after all.

EDIT: Looks like UltraVNC for Windows may offer encryption in a free product.

EDIT2: x11vnc has millions of options on Ubuntu, including ssl encryption.

More info: See [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC) for a full explanation of VNC on Ubuntu, and links for getting it to work over ssh. This would need Cygwin on Windows, I believe; but reverting to RA on Windows is always an option :-)

---

### Post by andersja on 2010-11-04
Consider using Gitso for cross-platform as well as Ubuntu-to-Ubuntu support. I use it regularly and it works very well: 
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

