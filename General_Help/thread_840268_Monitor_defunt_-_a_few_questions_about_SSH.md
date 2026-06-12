---
title: "Monitor defunt - a few questions about SSH"
date: 2008-06-25
forum: General Help
---

### Post by eludlow on 2008-06-25
My monitor has just died, and I can't get a replacement until the end of the week.  However, I can SSH into the machine from my laptop, so I can still access the data etc.

I also have VNC installed, but is there a way to log into X via ssh, so I can then connect using VNC.

Also, is there a way to run update manager through shell?  I know this can be done on SUSE using yast, but I've never done it on Ubuntu.

Any help appreciated.

Thanks,
Ed Ludlow

---

### Post by HalPomeranz on 2008-06-25
> **eludlow said:**
> 
I also have VNC installed, but is there a way to log into X via ssh, so I can then connect using VNC.


I'm not sure I understand what you're asking here.  If you have VNC on the headless machine and a VNC client on your laptop, why can't you just make the connection without SSH?  You can use port-forwarding with SSH to tunnel the VNC connection more securely ([https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)) but you may want to try getting the basic VNC connection working first.

Also, you could just use straight X forwarding instead of VNC.  SSH into your headless system using the -X option to enable X forwarding and then run any X app (like Synaptic, for example) and it will automatically pop up on your laptop's display.

> **eludlow said:**
> 
Also, is there a way to run update manager through shell?  I know this can be done on SUSE using yast, but I've never done it on Ubuntu.


Aside from running Synaptic remotely via X forwarding, you can do updates directly from the command line:

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by bodhi.zazen on 2008-06-25
You can also ssh -X which forwards x applications.

so you can :

```
ssh -X user@ip
```

Then:

```
gksu snyaptic
```

and on ....

You can mount remote directories with sshfs

[http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

---

