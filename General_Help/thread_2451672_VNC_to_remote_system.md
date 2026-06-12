---
title: "VNC to remote system"
date: 2020-10-09
forum: General Help
---

### Post by bomberb17 on 2020-10-09
My system runs 20.04.1 LTS just upgraded from 18.04.
I want to VNC to my desktop. However my remote system is still on the login screen.
I saw that x11vnc can vnc to login screen
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)
However when I run the suggested command
```
x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /home/USERNAME/.vnc/passwd -rfbport 5900 -shared
```

[FONT=arial]I get the following loops:

```
--- x11vnc loop: 1 ---

 --- x11vnc loop: waiting for: 29974

09/10/2020 00:12:30 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:30 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:30 passing arg to libvncserver: -rfbport
09/10/2020 00:12:30 passing arg to libvncserver: 5900
09/10/2020 00:12:30 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 29974
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:31 -auth guess: failed for display='unset'
09/10/2020 00:12:31 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:31 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---


 --- x11vnc loop: 2 ---

 --- x11vnc loop: waiting for: 30143

09/10/2020 00:12:33 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:33 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:33 passing arg to libvncserver: -rfbport
09/10/2020 00:12:33 passing arg to libvncserver: 5900
09/10/2020 00:12:33 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 30143
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:33 -auth guess: failed for display='unset'
09/10/2020 00:12:33 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:33 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---


 --- x11vnc loop: 3 ---

 --- x11vnc loop: waiting for: 30312

09/10/2020 00:12:36 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:36 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:36 passing arg to libvncserver: -rfbport
09/10/2020 00:12:36 passing arg to libvncserver: 5900
09/10/2020 00:12:36 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 30312
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:36 -auth guess: failed for display='unset'
09/10/2020 00:12:36 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:36 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---


 --- x11vnc loop: 4 ---

 --- x11vnc loop: waiting for: 30481

09/10/2020 00:12:38 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:38 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:38 passing arg to libvncserver: -rfbport
09/10/2020 00:12:38 passing arg to libvncserver: 5900
09/10/2020 00:12:38 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 30481
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:38 -auth guess: failed for display='unset'
09/10/2020 00:12:38 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:39 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---


 --- x11vnc loop: 5 ---

 --- x11vnc loop: waiting for: 30650

09/10/2020 00:12:41 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:41 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:41 passing arg to libvncserver: -rfbport
09/10/2020 00:12:41 passing arg to libvncserver: 5900
09/10/2020 00:12:41 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 30650
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:41 -auth guess: failed for display='unset'
09/10/2020 00:12:41 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:41 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---

c
 --- x11vnc loop: 6 ---

 --- x11vnc loop: waiting for: 30819

09/10/2020 00:12:44 passing arg to libvncserver: -rfbauth
09/10/2020 00:12:44 passing arg to libvncserver: /home/rahul/.vnc/passwd
09/10/2020 00:12:44 passing arg to libvncserver: -rfbport
09/10/2020 00:12:44 passing arg to libvncserver: 5900
09/10/2020 00:12:44 x11vnc version: 0.9.16 lastmod: 2019-01-05  pid: 30819
xauth:  file /root/.Xauthority does not exist
09/10/2020 00:12:44 -auth guess: failed for display='unset'
09/10/2020 00:12:44 -auth guess: since we are root, retrying with FD_XDM=1
09/10/2020 00:12:44 -auth guess: failed for display='unset'

 --- x11vnc loop: sleeping 2000 ms ---
```[/FONT]


[FONT=arial]Can someone help?[/FONT]

---

### Post by HermanAB on 2020-10-09
Note that VNC is mostly an old Windows thing.  For connections between Linux machines, there are better solutions, for example SSH.  (Windows 10 also has SSH built in, but it still needs a 3rd party X client.  It is getting there.)

---

### Post by bomberb17 on 2020-10-09
> **HermanAB said:**
> Note that VNC is mostly an old Windows thing.  For connections between Linux machines, there are better solutions, for example SSH.  (Windows 10 also has SSH built in, but it still needs a 3rd party X client.  It is getting there.)

Of course I am using ssh, all these inputs/outputs I quoted are through a remote terminal.
This however does not answer my question.

---

### Post by HermanAB on 2020-10-09
Well, you can do everything with SSH.  On UNIX systems, VNC is kinda redundant.

$ ssh -Y user@server "firefox http://ubuntuforums.org"

Anyhoo, you seem to be doing something as root with VNC, which can only lead to big pangs of regret:
"xauth:  file /root/.Xauthority does not exist"

---

### Post by bomberb17 on 2020-10-09
> **HermanAB said:**
> Well, you can do everything with SSH.  On UNIX systems, VNC is kinda redundant.

$ ssh -Y user@server "firefox http://ubuntuforums.org"

Anyhoo, you seem to be doing something as root with VNC, which can only lead to big pangs of regret:
"xauth:  file /root/.Xauthority does not exist"

I know that I can do a lot of stuff with ssh. Again this is not my question. I need specifically to remotely access the desktop for other reasons.

---

### Post by HermanAB on 2020-10-10
SSH is already working and you can run the whole desktop over SSH if you want.  To speed it up, enable compression and use simple encryption such as Blowfish, then you can launch Gnome, KDE or XFCE remotely.  It works OK, same as VNC, plus it is actually secure also.

However, for VNC, you got to fix the top error first.  It shows that you are doing something as root which should be done as a user instead.

---

### Post by bomberb17 on 2020-10-11
> **HermanAB said:**
> SSH is already working and you can run the whole desktop over SSH if you want.  To speed it up, enable compression and use simple encryption such as Blowfish, then you can launch Gnome, KDE or XFCE remotely.  It works OK, same as VNC, plus it is actually secure also.

However, for VNC, you got to fix the top error first.  It shows that you are doing something as root which should be done as a user instead.

Ok so at this moment the remote host is at the login screen. How can I  use SSH to see whatever is displayed on that host and login to the  desktop? (i.e. much like as Teamviewer/anydesk)

---

### Post by TheFu on 2020-10-11
Not an answer either, but when **ssh -X** and **xspice** don't work, I use **x2go**.  it feels about 2-3x faster than vnc or rdp.

But that isn't the answer you seek. Sorry.

---

### Post by ActionParsnip on 2020-10-11
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Works well. What are you doing on the remote system once connected via VNC? There may be a sleeker solution to what you are doing

---

### Post by bomberb17 on 2020-10-11
> **ActionParsnip said:**
> [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

Works well. What are you doing on the remote system once connected via VNC? There may be a sleeker solution to what you are doing

Sorry forgot to mention that I have already TightVNC but it doesn't work for my purposes, because it shows some other desktop than the actual desktop being shown on the monitor.

---

### Post by kevdog on 2020-10-12
I really like x2go.  Give that a try.

---

