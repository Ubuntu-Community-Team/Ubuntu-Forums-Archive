---
title: "Ubuntu as a virtual machine is running painfully slow."
date: 2013-02-02
forum: General Help
---

### Post by Nyakitty on 2013-02-02
I installed ubuntu as a virtual machine(using this guide [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)) and it is running painfully slow. Everything from the mouse down to clicking and typing lag noticeably enough that the OS is almost unusable. I'm guessing it might not lag if I wasn't running it in a virtual machine, but I'd like a chance to test out Ubuntu before I decide to commit to it that much; since I don't have a lot of money to spend, a VM seemed like the best option.

Running multiple instances of firefox doesn't seem to make it any slower. And I've been making sure all programs apart from virtualbox are closed in Windows 7.

The ubuntu iso I used was the ubuntu-12.10-desktop-i386.iso. In other words, the 12.10 32-bit version. I tried using the 64-bit version, but it didn't want to work.

My computer specs: 

Manufacturer: Hewlett-Packard
Model: HP Pavilion dv6 Notebook PC
Processor: AMD Turion(tm) II P540 Dual-Core Processor 2.40 GHz
Installed memory(RAM) 4.00 GB (3.74 GB usable)
System type: 64-bit Operating System

---

### Post by UAdnan on 2013-02-02
I'm not really sure how I can help you regarding the virtual machine issue, but I'd advice you not to base yourself on the virtual machine's behaviour to figure out how well does Ubuntu work in your computer.

You probably have a pen drive, re-writable DVD hanging around, why not try Ubuntu using a LiveUSB or LiveCD ?

---

### Post by haqking on 2013-02-02
12.10 is known to be buggy in a VM due to lack of 2D-Unity

Personally it works fine for me but alot of people are having issues with it.

see here [http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly](http://askubuntu.com/questions/207813/why-does-an-ubuntu-12-10-guest-in-virtualbox-run-very-very-slowly)

[https://www.virtualbox.org/ticket/11107](https://www.virtualbox.org/ticket/11107)

[http://ubuntuforums.org/showthread.php?t=2110051](http://ubuntuforums.org/showthread.php?t=2110051)

---

### Post by mcduck on 2013-02-02
As with any virtual machine setup, make sure you install the drivers & tools for the VM in the guest operating system.

In this case it's the VirtualBox Quest Additions you need to install:

```
sudo apt-get install virtualbox-guest-additions
```

---

### Post by Nyakitty on 2013-02-02
Thanks for the info. I'll try installing guest additions and if that doesn't work, using 12.04 to see if that version runs better.

Might try liveusb eventually if I can't get VM to work, but it'll likely be a good week or two until I have a decently sized flash drive.

---

### Post by Yellow Pasque on 2013-02-02
As noted, the Unity desktop requires 3D acceleration, and if none is available, it will use the CPU to do all of the graphics acceleration.
So basically, use Xubuntu or Lubuntu if you want to run in a VM.

---

### Post by alexii on 2013-02-03
How much memory did you give the VM? That tutorial has a picture of someone giving 512 mb... If you followed suit, that is certainly your problem. Give at least 1 gig, or up to 1.5 gigs per your host's specs.

---

