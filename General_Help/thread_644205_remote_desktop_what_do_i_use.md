---
title: "remote desktop what do i use?"
date: 2007-12-18
forum: General Help
---

### Post by teryowen on 2007-12-18
I have a machine connected to the network which im ssh'd to right now, what i want to do is download some package or set it up so that i can do remote desktop? What package do i need to set up on the remote machine and what packages do i need to install on the local machine?

By the way i dont have a monitor on the second computer so i would rather do all this through ssh.

Thanks in advance

---

### Post by bodhi.zazen on 2007-12-18
You can use ssh 

ssh -X will forward X apps

You can forward the entire desktop if you wish.

There is also VNC and FreeNX

[uwiki]VNC[/uwiki]
[uwiki]SSHHowto[/uwiki]

---

### Post by r-mo on 2007-12-18
Have to say I'd go with the VNC option. I've found X11 forwarding over SSH to be very slow when I've tried it (or is that just me?)

---

### Post by teryowen on 2007-12-18
alrite so i installed vnc server on the remote machine and xvncviewer on the local but no luck connecting?

---

### Post by HermanAB on 2007-12-18
Uhmm, SSH is all you need:
ssh -X -c blowfish user@server firefox

or if you are click-happy:
ssh -X -c blowfish user@server gnome-panel

La voila!

Herman

---

### Post by teryowen on 2007-12-18
wow HermanAB, great thanks alot.

By the way on a side note anybody familiar with setting up a sftp server?

---

### Post by teryowen on 2007-12-18
Hey herman the ssh -x name@server gnome-panel isnt workng but the firefox one works. is the command wrong maybe?

---

### Post by daflame on 2007-12-19
> **teryowen said:**
> Hey herman the ssh -x name@server gnome-panel isnt workng but the firefox one works. is the command wrong maybe?

You could check out FreeNX.  Here's a forum to help:

[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

