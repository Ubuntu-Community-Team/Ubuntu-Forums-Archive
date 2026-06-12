---
title: "VNC - Gray Screen with Terminal"
date: 2006-12-26
forum: General Help
---

### Post by shanepardue on 2006-12-26
I am trying to connect to my desktop from a laptop using xtightvncserver. This is the output I get... 
```
shane@shane-desktop:~$ vncserver :1
xauth: (argv):1:  bad display name "shane-desktop:1" in "add" command
Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.

New 'X' desktop is shane-desktop:1

```
When connecting from the client, It asks for a password and brings up a gray screen with a terminal. 
The terminal shows the contents of the desktop, but it doesn't match what's on the screen on my desktop. 
What am I doing wrong?


and for the record, vino (the default remote desktop on ubuntu) doesn''t even connect. It says 
"connection reset by peer"

---

### Post by shanepardue on 2006-12-27
If no one knows how to fix this, what's the best way to vnc then?

---

### Post by flguy2 on 2008-01-17
In case anyone else has this problem, I fixed it on my Ubuntu Gutsy 7.10 server by installing the desktop (duh).  The Amazon EC2 public image didn't have the desktop installed.  Obviouslly, I am new to this.  Btw, this is on a 64-bit instance.  I am using tightvnc viewer from my WindowsXP desktop.

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

apt-get install vncserver (if you haven't already)

---

