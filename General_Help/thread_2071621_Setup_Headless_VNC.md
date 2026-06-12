---
title: "Setup Headless VNC"
date: 2012-10-15
forum: General Help
---

### Post by jwshgeek on 2012-10-15
I'm trying to setup an Xubuntu desktop system that will be headless for testing.  I need vnc to simply show me what is on the screen of the workstation, not create a new session and I need it to be able connect to it even if it's not logged in (trying to emulate a multi-user setup for a remote client).

Any help will be much appreciated.

---

### Post by jwshgeek on 2012-10-16
Any ideas on this, I've tried several different guides online, but can't seem to get any to work

---

### Post by Lars Noodén on 2012-10-17
You could try x11vnc.  That one seems to work for me.  To attach it to an existing session, use that display number.  (e.g.  :****0)

```
 
x11vnc -safer -localhost -rfbauth ~/.vnc/passwd -display :0 

```

That will allow you to connect over an SSH tunnel.  Just for form, add a VNC password, too, before starting.

```

x11vnc -storepasswd

```

tightvncserver used to work for me but not any more.  I seem to be missing a step or something.

As time permits, try to begin mastering use of the shell for your servers.  It really is much more powerful and flexible than any GUI.

---

### Post by jwshgeek on 2012-10-18
so after installing x11vnc I ran the following,

sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
sudo chmod 744 /etc/x11vnc.pass

then I added the following to /etc/lightdm/lightdm.conf

greeter-setup-script=/usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log

I've tested it with logouts and reboots and it works fine with one minor flaw of disconnecting the active connection when you log out and having to reconnect once its at the login screen

---

