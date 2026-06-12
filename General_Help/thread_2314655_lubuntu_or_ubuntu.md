---
title: "lubuntu or ubuntu?"
date: 2016-02-22
forum: General Help
---

### Post by iuval on 2016-02-22
I have been using lubuntu for several years but recently my computer crashed when I tried upgrading to 14.04. I was able to recover most of my data from the old hard drive and had a friend mail me an even older hard drive from a used computer that apparently had ubuntu (not lubuntu) 14.04 LTS on it. I am debating whether to install lubuntu (and how--should I do it from the usb stick that I made from another computer, or download it directly here?). Here are my issues with ubuntu so far:
1. Does it use more RAM than lubuntu? I need all the RAM I can get to run intensive computations with Mathematica. I only have 2GB of RAM and no more RAM slots on metherboard.
2. How do I get a command line terminal? I have an old downloaded file called Mathematica_(somethingorotherlinuxversion).sh. I am not sure, but I think I need to make it into an executable and run it from command line.
3. How can I create a login or sudo password? I think currently it is blank. I was asked for one from the update manager and I just hit <enter> and it seemed to work. But this is not secure.

---

### Post by goofprog on 2016-02-22
From what I know, ubuntu using a version of gnome and lubuntu using the LXE desktop.  Yes, the gnome desktop will use more RAM.  A suggestion is to read up on some UNIX/Linux administration because adding users is a basic function in it.  I say it this way because adding users to an OS is a security risk and it is a type of Caviat emptor or "Let the buyer beware"

---

### Post by iuval on 2016-02-22
I tried installing lubuntu from the usb stick (for the nth time) It failed again, this time witha new hard drive. The last message it gave was: trying to overwrite /etc/console-setup/compose.iso-885i.11.ins which is also in package consoleetc.122. When I clicked OK it told me the installer crashed. What should I do?

---

### Post by iuval on 2016-02-22
It also said it couldn't submit a problem report because of 3rd party software

---

### Post by goofprog on 2016-02-22
I am not familiar with installer problems.  I would just use an old fashion DVD burn instead if you keep getting USB install problems from USB.  I also suggest to install it offline too.  Why?  Well there was a problem with a version of Linux that I was working on and everytime I tried a new computer name it was already online so I started to install it offline.

---

### Post by iuval on 2016-02-22
> **goofprog said:**
> I am not familiar with installer problems.  I would just use an old fashion DVD burn instead if you keep getting USB install problems from USB.  I also suggest to install it offline too.  Why?  Well there was a problem with a version of Linux that I was working on and everytime I tried a new computer name it was already online so I started to install it offline.

I'll try the offline idea. I don't have a DVD on this computer.

---

### Post by Travis_McEndree on 2016-02-23
The 32 Bit version of Ubuntu sounds OK for your use/specs. I personally prefer Ubuntu because I prefer Unity over any other desktop environment.

---

### Post by yoshii on 2016-02-23
From what I have read, Xubuntu doesn't use alot of resources for the desktop environment, and it's somewhat similar in RAM usuage to Lubuntu, although Lubuntu uses less.  
Personally, I chose Xubuntu on a low spec used computer and it's been running very smoothly.  I haven't had any problems with it.  I find that it's slightly more user friendly than Lubuntu, but of course you can still add Software Center and PulseAudio Volume Control and Gedit and gParted or whatever you like to Lubuntu also, to make it more user friendly.  

From what I read, Lubuntu and Xubuntu are the lightest on resource use of the 'Buntus.  I would not use vanilla Ubuntu.  Just be sure to make a SWAP partition.  I have mine sized at exactly 4GB and it's fine.

---

### Post by furtom on 2016-02-23
1. Are you formatting the disk when you install or trying to overwrite it? 

2. If you are installing anew, just be sure to choose a password when the time comes.

3. With your specs, I'd use Lubuntu or Xubuntu myself. No question either of those will run better than Ubuntu.

---

### Post by iuval on 2016-02-26
I was choosing the option to overwrite the disk. I tried with no network, but nothing works to boot off of hard drive. The hard drive is fine--I can look at files on it, I can write to it, just can't boot off it (but was able to both with ubuntu when it came with it, and my previous 12.04 lubuntu when it came with it). So I am giving up--upgrading to 14.04 was a terrible, time-wasting idea. Wasn't able to boot from the supergrub2,iso file either. I am going to get a new (refurbished) Lenovo computer with 4GB RAM and intel i5 processor. But what if I encounter the same problem when I erase windows 7 and try to install lubuntu (doesn't matter which version)?

---

### Post by iuval on 2016-02-29
[COLOR=#000000]t was not a hardware problem. It was something about the BIOS that was confusing all the installers. I'm not sure what it was but I changed a few things and was able to install lubuntu 15.02. What a waste of my time.[/COLOR]

---

