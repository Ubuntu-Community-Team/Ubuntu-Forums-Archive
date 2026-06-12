---
title: "Faster or better than VNC?"
date: 2007-09-26
forum: General Help
---

### Post by LotsOfPhil on 2007-09-26
Is there any VNC like app that will let me transfer files between systems by dragging and dropping?

Failing that, is there one that is faster? Both the local and remote machines are fast, on a fast network, and the VNC window is slooooow.

---

### Post by Junzuki on 2007-09-26
> **LotsOfPhil said:**
> Is there any VNC like app that will let me transfer files between systems by dragging and dropping?

Failing that, is there one that is faster? Both the local and remote machines are fast, on a fast network, and the VNC window is slooooow.

Take a look at gftp: [http://gftp.seul.org/](http://gftp.seul.org/) you can get it via synaptic or apt-get. I use it via shh2 for backups etc to other box's and its secure and pretty quick.

---

### Post by SeanTater on 2007-09-26
Some file managers (I don't know if Nautilis is among them, but I think it is) also have the sftp:// protocol, provided you install an ssh server on the computer you are trying to download from.

Note however! That if you use it the way it installs by default, someone will only need your username and password to do anything they want on your computer, so DON'T do this if you are directly connected to the internet or you have port 22 forwarded (which it usually isn't)..

This considered, ssh is probably one of the easiest servers you can set up. Also, your files are encrypted as they travel across the network. SSH is quite fast and you should theoretically get about 80 to 120 MB/s (about 2/3 to full Gigabit Ethernet speeds)

---

### Post by fjgaude on 2007-09-26
I do as Sean suggests using SSH but also use DSA public/private keys to keep the computers secure. Has worked for a long time without problems, no Internet hacking, etc. Speed over the Gigabit net is about 110MB/sec for large files. I use Unison to keep everything in sync, and also Grsync. Both can be installed with Synaptic or apt-get.

Make sure all the Linux boxes have SSH server installed.

---

