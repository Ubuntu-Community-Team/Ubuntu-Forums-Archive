---
title: "My cellphone on ubuntu?"
date: 2023-11-13
forum: General Help
---

### Post by josephchrzempiec on 2023-11-13
Hello, I have a bunch of older cellphones that are still pretty fast. One of them are a Samesun Galaxy S9. I would love to run ubuntu on it and give some new life into it. However everything I found online to do something only shows what to setup with. Not where to get the image from or what programs on the phone I would need. I saw once that the phone might needed to be rooted which I have done once on a phone but don't remember. 

i need help from the community to make this happen. Asking the community What are the steps and files i need to make this happen please?

Joseph

---

### Post by Paddy Landau on 2023-11-13
Look at [Ubuntu Touch]("https://ubuntu-touch.io/"), which refers to the [UBports installer]("https://devices.ubuntu-touch.io/installer/"). It has instructions for a variety of phones.

---

### Post by josephchrzempiec on 2023-11-13
> **Paddy Landau said:**
> Look at [Ubuntu Touch]("https://ubuntu-touch.io/"), which refers to the [UBports installer]("https://devices.ubuntu-touch.io/installer/"). It has instructions for a variety of phones.


thank you I will do that. I don't want to run it as a phone no more. Just as a system. I have it connected to a monitor right now and a bluetooth keyboard and mouse.

---

### Post by Paddy Landau on 2023-11-13
> **josephchrzempiec said:**
> I don't want to run it as a phone no more. Just as a system.
Ah, right, that wasn't clear in your request. Sorry, I don't know how to do that.

---

### Post by TheFu on 2023-11-13
> **josephchrzempiec said:**
> thank you I will do that. I don't want to run it as a phone no more. Just as a system. I have it connected to a monitor right now and a bluetooth keyboard and mouse.
I know of no way to directly boot a standard Linux onto a mobile device ... apart from my Nokia N800 Tablet which came with a customize Debian OS and Maemo for the desktop.  Today, that device has terrible performance, terrible battery life, and terrible resolution.  It belongs in a museum even though it was new in 2008 and I traveled with just it for a few years to many continents.

I have seen and actually run a Linux desktop under Android in a "chroot" environment on a 10inch tablet. The tablet at that time was one of the most powerful available. Did that back in 2011 running an Ubuntu.  It was convoluted and required using VNC to connect from the Android VNC client into the chroot'd VNC server running Ubuntu. Back then the hardware wasn't nearly as capable as today and some of the main reasons I wanted to use it was to access ssh and thunderbird though and ssh tunnel back to my home LAN and servers.  Sadly, some of the keyboard mapping in VNC didn't work, so I gave up.  Had I not tried and seen the 5+ second delay from any input to the GUI showing it, I would have wondered for years what was truly possible.

If it were me and I wanted a small computer to do some specialize desktop things, I'd forget the old phone idea and use a raspberry pi v3/v4/v5 instead.  The v3 is really cheap now and can handle many desktop needs.  A v4 Pi is at the point that it can replace many typical desktop uses, including some video editing, though it won't compare to an x86-64 CPU or GPU in performance.

Anyway, install Ubuntu ARM into a chroot on your phone, setup a VNC server there, then load a VNC client on your phone (or other workstation) and connect either locally or over wifi to the VNC server using an ssh tunnel for security if using wifi.  Never use VNC without either a VPN or ssh tunnel over any wired or wireless network. It isn't safe.  Locally, it would be fine, just be certain to always limit VNC connections to localhost  (127.0.0.x) addresses.

---

### Post by josephchrzempiec on 2023-11-13
> **Paddy Landau said:**
> Ah, right, that wasn't clear in your request. Sorry, I don't know how to do that.


I'm sorry about that. I honestly forgot to put that in there that I only wanted to run it as a system and not a phone. I can still run it as a phone and not use all the phone features. It should work okay like that. or am I wrong again?

---

### Post by josephchrzempiec on 2023-11-13
> **TheFu said:**
> I know of no way to directly boot a standard Linux onto a mobile device ... apart from my Nokia N800 Tablet which came with a customize Debian OS and Maemo for the desktop.  Today, that device has terrible performance, terrible battery life, and terrible resolution.  It belongs in a museum even though it was new in 2008 and I traveled with just it for a few years to many continents.



Can I just run the ubuntu phone with all the features it comes with as a desktop And use it as a normal desktop for mobile use?

---

### Post by MAFoElffen on 2023-11-13
For chroots, I've been doing that since around 2008 on HTC Wizard, when my HTC Tilt replaced it... I had been cooking Win Mobile ROM's for XDA. 

It depends on the phone... Here is a database of around 200 phone that you can flash Linux to, what they are supported by, and what stage of the support they are in so far...
[https://many.tuxphones.com/](https://many.tuxphones.com/)

---

