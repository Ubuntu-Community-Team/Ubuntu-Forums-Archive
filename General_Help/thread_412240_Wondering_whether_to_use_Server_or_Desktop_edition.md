---
title: "Wondering whether to use Server or Desktop edition...."
date: 2007-04-17
forum: General Help
---

### Post by foldor on 2007-04-17
I have just brought home the computer we were messing around with in school for the semester. It is an old machine that we got to test our technical knowledge on without worrying about having it break. The computer is an old Pentium 3 1000 MHz with 256MB of RAM ( Might get it to 512MB soon) and some random integrated video card.

The thing I want to know is if I should install Ubuntu Server or Desktop edition. The criteria I want to meet are as follows:

- Must be able to host an FTP using a site like dynDNS.org or no-ip.org for general personal use.
- Must be able to remotely login.
- Must have SAMBA support for sharing folders between all computers in the house.
- Preferably able to join a workgroup domain on a windows network, for use with Xbox Media Center.
- Must run decently on the computer.
- Preferably able to turn off or hibernate or sleep and still be able to wake it up or turn it on remotely.

The computer already has Ubuntu Server 6.10 installed on it and I put the ubuntu-desktop package onto it to help set it up. I just feel that its getting to be to similar to the desktop edition and I wasn't sure if it would be better for what I am trying to do.

I just thought I would come here and ask what everyone thought would be a good idea.

Also any other thoughts on what I could do with this machine that isn't ridiculous or generally difficult to set up would be great to hear.

Oh and last but not least any help pointing me towards a guide or two that can help with this would be greatly appreciated.

Thanks in advance and I hope to hear from some people,
foldor

---

### Post by foldor on 2007-04-18
Sorry, but I would like some help still. So I am bumping this.

---

### Post by az on 2007-04-18
> **foldor said:**
> 
- Must be able to host an FTP using a site like dynDNS.org or no-ip.org for general personal use.
- Must be able to remotely login.
- Must have SAMBA support for sharing folders between all computers in the house.
- Preferably able to join a workgroup domain on a windows network, for use with Xbox Media Center.
- Must run decently on the computer.
- Preferably able to turn off or hibernate or sleep and still be able to wake it up or turn it on remotely.

The computer already has Ubuntu Server 6.10 installed on it and I put the ubuntu-desktop package onto it to help set it up. I just feel that its getting to be to similar to the desktop edition and I wasn't sure if it would be better for what I am trying to do.


The computer hardware can handle all that.  The software you have on it now is equivalent to installing the desktop version and then installing the various servers (FTP, Samba, NFS... ) on top of that.  Does it run a web server as well?  If not, you can remove the LAMP stack (apache2, mysql and php)

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

As for hibernating or sleep, you need a motherboard and a NIC that supports WOL (Wake on Lan) and then you just have to send the wake up packet to it from wherever...

---

### Post by Smuve on 2007-04-18
I haven't tried this, but when I install Feisty in a few days, I"m going to try the server edition, then add on gnome-core.  Obviously I'm going to research it a little more, but I think that by using gnome-core instead of ubuntu-desktop, it installs the necessary things for a gui without all of the extra software bloat like OOffice and Evolution etc.

Maybe somebody can confirm or deny this. . .

---

### Post by Smuve on 2007-04-18
Or maybe this will work.  I copied off of a similar post a while ago.  Install these on top of server edition to get gnome up and running. . .
```
sudo aptitude install xorg gnome-core gdm synaptic gnome-app-install update-manager
```

gnome-core is what I was thinking of in my previous post, not ubuntu-core.  I'll go back and edit that real quick.

---

### Post by strabes on 2007-04-18
You could also install the package ubuntu-desktop if you want everything that comes with ubuntu....probably not though.

---

### Post by vlad_x2 on 2007-04-18
If you are confortable enough to work in cli (like, not touching x) then the server version is for you, else choose the desktop. Everything that is in the server can be installed on the desktop too with aptitude (or apt-get).

---

### Post by moon2js on 2007-04-21
> **vlad_x2 said:**
> If you are confortable enough to work in cli (like, not touching x) then the server version is for you, else choose the desktop. Everything that is in the server can be installed on the desktop too with aptitude (or apt-get).

The kernel is different though, no? Optimized for serving or something?

---

