---
title: "remote access ubuntu  12.04"
date: 2013-01-03
forum: General Help
---

### Post by HernanLinux93 on 2013-01-03
Is anyone aware of a *LogMeIn*-like service or technology to use for *Linux*?
thanks :D

---

### Post by ryandcalvert on 2013-01-09
I was just looking myself and found this, I think it will work as good or better than logmein. It does however look like you will need to have at least two Linux machines.
[http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop](http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop)
It also would not surprise me if this forum has a bunch on remote desktop, I just haven't looked yet.
hope that helps.

---

### Post by MSPdwalt on 2013-01-09
What are you trying to remote control? A server/desktop that has/can be given a static IP, and doesn't go anywhere?  Or a laptop that could be anywhere at any time?

I would try X11 forwarding over SSH. If your target isn't moving around.  Otherwise teamviewer for Linux kind of works some of the time lol.  Remote management seems to be an industry that's largely ignored the Linux community.  I guess they think we can all support ourselves.

---

### Post by slickymaster on 2013-01-09
There are several ways to access a remote machine. You can choose from a command-line remote access, using [OpenSSH]("https://help.ubuntu.com/community/SSH") on the server and use ssh command on the client (take a look at this [post]("http://askubuntu.com/questions/25189/remote-login-with-graphical-display-manager-gdm-lightdm/25192#25192") for secure ssh transmission viewing the login screen), or you can have a graphical remote access using software like [Team Viewer]("http://www.teamviewer.com/en/index.aspx?cdsplit=C"), [Mikogo]("http://download.mikogo4.com/mikogo.tar.gz"), [x2go]("http://www.x2go.org/doku.php/download:start"), [VNC]("http://www.realvnc.com/products/vnc/"), etc.

---

