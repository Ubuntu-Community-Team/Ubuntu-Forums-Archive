---
title: "Can't get VNC to work"
date: 2008-06-11
forum: General Help
---

### Post by brownbrown on 2008-06-11
Hi everyone,
I recently installed a copy of 7.10 Xubuntu, and immediately made the upgrade to 8.04.
My problem is this:
I followed [this]("http://backports.ubuntuforums.com/showthread.php?t=795036") tutorial on how to set up a vncserver on a 8.04 system, but after following all the steps, minus the open-ssh part (I only plan to use this VNC on the LAN) I cannot VNC into the server from this windows machine, which is on the same LAN. 
This is my Xvnc file ```
service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = nobody
        server = /usr/bin/Xvnc
        server_args = -inetd -query localhost -geometry 1024x768  -depth 16 -cc 3 -once -SecurityTypes=none -extension XFIXES
        port = 5901
}
```
I set my host server to a static ip, so for example, when I attempt to connect using tightvnc on from the windows machine, I put 192.168.1.11
A few seconds later a message pops up saying failed to connect to server.
I am lost as to what is wrong, so any help would be appreciated.

---

