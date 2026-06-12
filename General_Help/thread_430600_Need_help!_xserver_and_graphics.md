---
title: "Need help! xserver and graphics"
date: 2007-05-02
forum: General Help
---

### Post by crimmie on 2007-05-02
Hi!
I Installed Ubuntu for the first time today and everything works find except for the graphical settings. With default settings from the install the screen goes totaly blank upon login screen.

My graphics card is an ATI Radeon 1900xt. When I try to reconfigure with "sudo dpkg-reconfigure xserver-xorg" and choosing ATI it won't boot complaining that the "device section instance can not be found. BUSId: PCI:5:0:1)" When I use VESA it goes blank (no output from video card). The only setting I can get into Ubuntu without going blind is with VGA. If I use VGA it forces the resolution to 320x200 which makes it impossible to to anything inside ubuntu. 

What can I do?

---

### Post by taurus on 2007-05-02
Do you by any chance have two graphic cards on your machine, one onboard and one add-on?  

What's the output of this command from a terminal/prompt?

```
lspci
```

---

### Post by crimmie on 2007-05-02
Nope. lspci printout shows both primary and secondary VGA adapters as ATI Radeon 1900 @ BusId: PCI:5:00.0 and PCI:5:00.1

Errorlog after choosing ATI in xserver: "No matching Device section for instance..."

---

### Post by taurus on 2007-05-02
> **crimmie said:**
> Nope. lspci printout shows both primary and secondary VGA adapters as ATI Radeon 1900 @ **[COLOR="Red"]BusId: PCI:5:00.0 and PCI:5:00.1[/COLOR]**

Errorlog after choosing ATI in xserver: "No matching Device section for instance..."

Well, that could be the problem there.  In your /etc/X11/xorg.conf, it is looking at PCI:5.00.1!  Why don't you change the BusID to PCI:5.00.0?

---

