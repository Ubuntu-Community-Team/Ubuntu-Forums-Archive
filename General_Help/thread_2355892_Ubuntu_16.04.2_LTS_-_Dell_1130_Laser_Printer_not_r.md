---
title: "Ubuntu 16.04.2 LTS - Dell 1130 Laser Printer not recognized"
date: 2017-03-17
forum: General Help
---

### Post by gammayt on 2017-03-17
Ok, first, before you start reading, know that I'm not sure if you have to do something to actually detect the printer.  On my Windows system (I dual boot) since I plugged in my printer via USB, it instantly works like a charm.  However, on this Ubuntu system I can't seem to find any drivers for it.  Please help as much as you can.  

[SIZE=5]TL;DR:[/SIZE]
[SIZE=2]Dell 1130 Laser Printer, not recognized, cannot print, Ubuntu 16.04.2, i guess driver issue, thanks[/SIZE]

---

### Post by ronlewis7 on 2017-03-17
According to following link at the Ubuntu site, Ubuntu does not come with this driver installed.
The generic driver will work. Please refer to this link. This info pertains to version 11 but may work on your system.

[http://askubuntu.com/questions/138159/why-does-my-dell-1130n-printer-not-install](http://askubuntu.com/questions/138159/why-does-my-dell-1130n-printer-not-install)

I hope this helps.

---

### Post by howefield on 2017-03-18
If the above does not yield success, there is a Linux driver for this model on the Dell website.

It is a tar.gz file which will extract when double clicked, if placed in the ~/Downloads folder it can be installed with

```
cd ~/Downloads/cdroot
```
```
sudo sh autorun
```

Follow the installation wizard to the end and you should have a working printer.

---

### Post by gammayt on 2017-03-18
Howefield, could you link that to me please? I can't seem to find it.

Nevermind, I think I might have found it.  I'm trying it out right now.

Holy crap! It worked.  Thank you guys so much for all of the Ubuntu support and feedback, I'm never going back to Windows.  #LINUX

---

### Post by howefield on 2017-03-18
> **gammayt said:**
> Thank you guys so much for all of the Ubuntu support and feedback

You're welcome, glad you got it sussed and feel free to mark the thread as solved. :)

---

### Post by gammayt on 2017-03-18
Will do that, but I'm also making another thread on something related to this issue.  Sorry if i make many threads, but I'm really new to Linux but I've seen to get the hang of it.

---

### Post by howefield on 2017-03-18
> **gammayt said:**
> Will do that, 

Thank you.

> but I'm also making another thread on something related to this issue.  Sorry if i make many threads, but I'm really new to Linux but I've seen to get the hang of it.

It's a forum, a forum that thrives on questions and answers. You are free to make as many (sensible) threads as you want following the forums Code of Conduct and Posting Guidelines. :)

---

