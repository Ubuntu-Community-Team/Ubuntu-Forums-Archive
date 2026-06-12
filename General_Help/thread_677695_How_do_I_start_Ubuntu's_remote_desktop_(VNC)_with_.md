---
title: "How do I start Ubuntu's remote desktop (VNC) with manually login on that Ubuntu"
date: 2008-01-25
forum: General Help
---

### Post by xdefconx on 2008-01-25
Hye all!

How do I start Ubuntu's remote desktop (VNC) with manually login on that Ubuntu. Let say my scenario now like this :

I also running on Ubuntu on LAN environment/no firewall issue which i would like to remote desktop(VNC) to other Ubuntu machine. However, i cannot login/connect via remote desktop until i manually login on that machine then come back to my PC to remote desktop. Any solutions for me?

Thanxs

---

### Post by diaa on 2008-01-25
As far as I know, this is a known drawback for using VNC, you(or someone else) must be logged in so you can connect remotely to this PC.
You can [enable Auto Login]("http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html") to skip the login screen altogether or *may be* using another remote control software that's more aware can help, try freenx...

---

### Post by daflame on 2008-01-28
> **diaa said:**
> As far as I know, this is a known drawback for using VNC, you(or someone else) must be logged in so you can connect remotely to this PC.
You can [enable Auto Login]("http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html") to skip the login screen altogether or *may be* using another remote control software that's more aware can help, try freenx...

I would second FreeNX.  It is an easy and free option.  Check out the forum I setup:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by xdefconx on 2008-01-29
> **diaa said:**
> As far as I know, this is a known drawback for using VNC, you(or someone else) must be logged in so you can connect remotely to this PC.
You can [enable Auto Login]("http://www.watchingthenet.com/how-to-enable-automati-logon-in-ubuntu-or-kubuntu.html") to skip the login screen altogether or *may be* using another remote control software that's more aware can help, try freenx...


Hehehe i prefer this tips although maybe someone will advice it's not a good idea when thinking about security:p Thanxs **diaa**


> **daflame said:**
> ..I would second FreeNX. It is an easy and free option. Check out the forum I setup:
[http://ubuntuforums.org/showthread.p...ghlight=freenx](http://ubuntuforums.org/showthread.p...ghlight=freenx)...

Thanxs for ur info, FreeNX look cool for me but a little bit complicated. Base on your experience, it is FreeNX got any drawback issue? But so far base on my search study FreeNX look perfect. Thanxs dude!

---

### Post by daflame on 2008-01-30
> **xdefconx said:**
> Thanxs for ur info, FreeNX look cool for me but a little bit complicated. Base on your experience, it is FreeNX got any drawback issue? But so far base on my search study FreeNX look perfect. Thanxs dude!

Only drawbacks currently is no support for VNC proxy on Debian and less than perfect sound and remote printing support.  I am working on a patch currently for the VNC proxy issue as access to the local desktop is highly desired and this is a Debian ONLY problem.

FreeNX creates a NEW desktop when you log in and allows you to resume it later or log out if you want.  One more known drawback: You cannot resume a windows session from Linux, nor a Linux session from Windows.

---

### Post by bodhi.zazen on 2008-01-30
For VNC, see these links :

[uwiki]VNC[/uwiki]

[uwiki]VNCOverSSH[/uwiki]

---

### Post by GSBoomer on 2008-01-31
I'm already using FreeNX for remote sessions (accessing lappy at home from university).

One problem: If I force the laptop to reboot while I'm at work, the laptop does not connect to my home wireless network until I manually login at home. Therefore, I can't initialize a remote session unless I've previously logged on at home.

Any solutions?

---

