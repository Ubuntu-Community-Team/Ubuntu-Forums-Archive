---
title: "Installing Nvidia drivers..."
date: 2008-05-23
forum: General Help
---

### Post by initram on 2008-05-23
I installed Ubuntu 8.04 and installed the Nvidia drivers for my GeForce 8500 GT.  I had alot of trouble installing them...but once I figured it out the installation went fine.  The problem is, after the installation completes, I reboot the machine and all the resolution options are gone...I only get 640x480 and a lower one.  How do I get back my other resolution options?  Should I try using Envy?  Thanks.

---

### Post by drs305 on 2008-05-23
I just used envy yesterday and it updated my nvidia drivers. The package name in synaptic is envyng-gtk.

---

### Post by initram on 2008-05-23
Ok, I will try that once I reinstall Ubuntu.  I had tried Kubuntu and Mint just to see but didn't like them as much and they didn't help with my driver issues.

So I just need to install the envyng-gtk package and it'll do the rest?  No commands needed?  No exiting x-server...etc?  I'll let you know how it goes.

---

### Post by drs305 on 2008-05-23
> **initram said:**
> Ok, I will try that once I reinstall Ubuntu.  I had tried Kubuntu and Mint just to see but didn't like them as much and they didn't help with my driver issues.

So I just need to install the envyng-gtk package and it'll do the rest?  No commands needed?  No exiting x-server...etc?  I'll let you know how it goes.

Yes, but see my added remark below. I am running 64 bit hardy on this computer but I believe the package name is the same.
Install envy either through synaptic or
```
sudo aptitude install envyng-gtk
```
Then run it in terminal:
```
envyng-gtk
```
and select 'nvidia' drivers.


Added" After I walked away from my computer I felt I had to come back to mention that I initially just installed the nvidia drivers via System, Admininstration, Restricted Drivers Manager and checked the Nvidia box. On my computer that was all I had to do. I used envy yesterday just to see if it would update the drivers, which it did.

---

### Post by bigdee973 on 2008-05-23
what u should also try to do is install nvidia-settings...u could 
sudo apt-get install nvidia-settings or go to synaptic manager...and i hope u installed nvidia drivers through ubuntu add/remove rather than do it manually

---

