---
title: "Installing and enabling VNC server"
date: 2024-05-24
forum: General Help
---

### Post by andrewk1972 on 2024-05-24
I want to install and configure VNC server on Ubuntu 22.04. In addition, I use GNOME desktop, and I don't want to use RealVNC...I'd prefer to use another alternative such as Tiger VNC.

However, the guides I have don't work and when starting the server the desktop system crashes...

Any idea what could be wrong?

I have a Raspberry PI running Raspbian with PIXEL and it was really simple to setup--enable VNC in the preferences and then connect to the Raspberry PI using TigerVNC client. Moreover, when connecting to the Raspberry PI from the client (MacBook) the native display session does not close, and the VNC client simply mirrors the native display.
Is it possible to do the same thing in Ubuntu 22.04?  

Any help is much appreciated.

---

### Post by TheFu on 2024-05-25
**Gnome doesn't work with most remote desktops. **

The solution is to use almost any other one that is lite.  XFCE or Mate would be my initial recommendations.  This all started with Gnome3 when the DE really wanted direct access to a GPU.

There are two other options.
[LIST]
[*][https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/](https://ubuntuhandbook.org/index.php/2022/04/ubuntu-22-04-remote-desktop-control/) - if you want the Gnome approved method using RDP - yuck!
[*][https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go) - requires X11 (doesn't work with Wayland); Doesn't work with Gnome/KDE-plasma, but almost any other DE or pure-WM setup works.
[/LIST]

Both VNC and RDP tools need a full VPN to be secure.  x2go uses the NX protocol that leverages ssh, so existing ssh-keys will be honored if you have them setup - and if you don't, why not?!!!!   Setting up ssh-keys is 2 commands, 1 time.  Makes all ssh stuff more secure AND more convenient.  I never understand why people don't just setup ssh with keys for authentication. Makes no sense.

---

### Post by HermanAB on 2024-05-26
VNC is a sure fire way to get any computer hacked.  Rather learn to use SSH - you won’t be sorry.

---

### Post by currentshaft on 2024-05-26
100

---

