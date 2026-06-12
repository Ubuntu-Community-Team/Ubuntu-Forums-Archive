---
title: "Dedicated Server + Desktop"
date: 2012-12-07
forum: General Help
---

### Post by MrDyne on 2012-12-07
Me and my friend just bought and built a powerful desktop computer to  become our groups dedicated server for our Website, Minecraft server,  and for rendering Blender projects so we don't have to hog up our own  PCs.

I have a few questions about setting up a Ubuntu based server.

The first question is, what the heck do I put as a hostname?
I  demo installed Ubuntu Server on a crap computer to try it out and I  didn't know what to put as a hostname? Does it need to be related to the  main domain name we are pointing at the server "server.domain.com" or  can we just put in whatever name we want? "leviathan". None of the  online guides i've read really explained the hostname. We don't need to be able to  type in [http://serverhostname](http://serverhostname) in our other computers as we can remimber  the LAN IP address of it.

2nd question. We want a server +  desktop. I very much dislike the Ubuntu GUI, way to OSX/Apple for my  taste (Window controls on the left side, really?!) So is it better to  put Ubuntu Server on the computer and install XFCE or start with Xubuntu  and install LAMP, SSH, FTP, Mail, DNS, etc....

3rd question. We  don't want the GUI running all the time so can it be set to not  automatically start with the computer? (Computer boots to a boring  terminal/headless screen. Type xstart for GUI.) And then can the  "shutdown" button be removed from the GUI or at least set to just close  the GUI and go back to terminal. Don't want users turning the entire  server off. Just the GUI to save power.

Oh and do I really need a swap partition when the computer has 16GBs of RAM? Would it extend hard drive life any to not have a swap?

~MrDyne

---

### Post by HermanAB on 2012-12-07
Howdy,

Since you are new to it all and the machine will have a keyboard and screen, install regular Xubuntu and then add your servers.

The Linux scheduler and memory manager are very good, so you should just leave the GUI up - there is not much point in killing it.

If your machine is sitting in a dank corner of a dark warehouse with no keyboard or screen, then you don't need the GUI at all, since you will manage it remotely using SSH.

Make the hostname whatever you want, eg pluto.example.com, but always use lower case and no underscores. There are DNS reasons for that.

You should always define swap space, else the machine can grind to a halt when you do something intensive.  If you want to use Suspend, then you need swap to be double the RAM size, otherwise a couple gigabytes will do.

Hope that helps!

---

### Post by Kirk Schnable on 2012-12-07
As a sidenote, if you'd like the server to always sit at a text console, but you'd like graphical management over the network/Internet, you might find a solution like NX to your liking. It can remotely access a GUI like XFCE which you can have only running while a session is active. 

Here is some reading on the various NX options readily available to you on Ubuntu:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
[https://help.ubuntu.com/community/NomachineNX](https://help.ubuntu.com/community/NomachineNX)
[http://www.humans-enabled.com/2012/04/how-to-install-freenx-server-on-ubuntu.html](http://www.humans-enabled.com/2012/04/how-to-install-freenx-server-on-ubuntu.html)

---

