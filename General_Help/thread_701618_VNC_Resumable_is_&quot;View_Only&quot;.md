---
title: "VNC Resumable is &quot;View Only&quot;"
date: 2008-02-19
forum: General Help
---

### Post by adam.hampton on 2008-02-19
I have VNC set up with resumable sessions so it automatically starts up when teh computer powers up.  But the problem I'm having is that the session is view-only.  I can't click any menu options.  I can hover over the menus or icons on the desktop, and make it bring up the bubble descriptions for each function, but no ability to click or right-mouse.

I can then run VNC4SERVER and initiate a new connection on display 2, for example, which will then have full abilities.  I just don't know how to change this control.

And again, it's resumable.  I've already looked for the settings in /usr/bin/vnc4server, which I couldn't find.

---

### Post by HermanAB on 2008-02-19
Hmm, well, actually VNC should not be used since it is insecure and really rather clunky.  VNC sends your user name and password in plain text over the wire, which is not a particularly hot idea and it copies the whole friggen desktop, which is stupid since you already got one.

For Windows, rdesktop with RDP is better and for Linux SSH is better.  With Windows, you can do seamless RDP using a utility from Cendio ([http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)) and with Linux, SSH is 'seamless' by design.

Some examples:
ssh -C -c blowfish -X user@server gnome-panel
ssh -C -c blowfish -X user@server kicker
ssh -C -c blowfish -X user@server "gedit /etc/fstab"

Cheers,

Herman

---

### Post by adam.hampton on 2008-02-19
Can I use seamless RDP or rdesktop from a linux host to a windows guest.

I understand how to launch an app from another linux box, but if I don't know what I need to launch, I'll have to browse through menus and directories, meaning I'll need a visual desktop of some sort.  

Those are the two reasons why I've been using VNC.

I can still use VNC if I just put it in a VPN (like using Hamachi).  
So if I could still get help with fixing the view-only problem, that would be greatly appreciated.

---

