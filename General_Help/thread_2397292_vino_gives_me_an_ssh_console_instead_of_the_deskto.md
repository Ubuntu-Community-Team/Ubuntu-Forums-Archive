---
title: "vino gives me an ssh console instead of the desktop"
date: 2018-07-27
forum: General Help
---

### Post by maurice-volaski on 2018-07-27
I have two Ubuntu machines, 18.04 and I want to control the desktop of one with the other. I started up vino on one and logged into the other with the vinagre client. But instead of getting a window showing me the whole desktop of the other, I just get an ssh console session.

Also, it's not clear how to set the preferences for vino as there is no vino-preferences command.

---

### Post by TheFu on 2018-07-27
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

I've never used vino and don't use VNC, but generally, there is a client and a server for protocols like this.  If you didn't setup the server before trying the client, don't expect it to work.  Also, most remote desktops using fancy graphics systems that want a full GPU generally work poorly, if at all.  The default desktop on 18.04 is Gnome3, which is considered heavy.  For VNC or any remote desktop, you want a lighter desktop like LXDE, XFCE, or Mate.

But ... there's an easier solution if the machines are on the same LAN and it isn't slow wifi.   Use X-forwarding to run programs over the network.  It isn't a "desktop", but GUI programs work fine this way.  The only requirements are
1) ssh connectivity between the systems
2) X11Forwarding enabled in the sshd_config on the remote system
     /etc/ssh/sshd_config:```
X11Forwarding yes
```
3) A working  X/Windows Server on the system you physically type on.

So, I'm on a laptop and want to run libreoffice on a system upstairs, but have that window displayed on my laptop.
```
$ ssh -X {IP to remote system} libreoffice
```
That's it, with a few assumptions about networking and userids that are probably true.  In a second or 2, libreoffice will pop up on my laptop.  Most X/Windows programs will work, but don't expect audio or video to work.  If you setup ssh-keys between the systems, then you won't get prompted every time for a password.  If you have internal DNS or /etc/hosts files setup on both systems with static IPs, then you can use the hostname instead of an IP.
Often, it is convenient to setup a few scripts to make running to programs elsewhere easier. Web browsers often will notice this attempt and run a local version instead of the remote browser.  I haven't looked recently, but there were command line options for chromium and firefox to override this default, bad, behavior.  If I go out of my way to run a browser remotely, it is because I want that.

IMHO.

---

