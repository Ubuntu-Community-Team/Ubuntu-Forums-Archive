---
title: "Couldn't find package build-essential"
date: 2005-06-25
forum: General Help
---

### Post by apoulemanos on 2005-06-25
I'm following [this guide](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/) for installing my rt2500 wireless card.  I have a problem though, when I get to the point where I download build-essential, it gives me the message: "couldn't find package build-essential."  I checked and it is definitely not there.  How could I get this package?

Please, give detailed instructions as I'm new to linux, and particularly apt.

---

### Post by frodon on 2005-06-25
When you use apt the command will search into repositories defined in sources.list file. So I think the command return this result because you don't have the repository where build-essential is.
Open your sources.list file : 
```
gedit /etc/apt/sources.list
```
If you don't have these lines add it and try again :
```
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hoary-security universe main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary-updates main restricted universe multiverse
```

For information you can do the same thing using synaptic.

---

### Post by hadeel on 2007-05-10
i was faceing the same problem and i try this soulution but i couldn't save the change i made in sources.list

---

### Post by taurus on 2007-05-10
Try

```
**gksudo** gedit /etc/apt/sources.list
```
Otherwise, build-essential package is on the CD so insert it in the drive and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Waldemar Sikorski on 2008-05-11
I guess it's time to reactivate this thread.
New to ubuntu 8.04. I don't have a cd. I've downloaded an iso and installed ubuntu as an app.
I need commands that apply to my installation. I do have problems with internet connection - wireless.
For the last 6 hours I've been running in circles from one thread to another.
Laptop HP zv6233nr with Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless Lan Controller (rev 02).
Any help appreciated. I'm at an internet caffe that on top of everything has developed dialup speeds with verizon DSL. Sucks.

---

### Post by frodon on 2008-05-12
You want to reactivate a 3 years old thread ?

This thread was talking about ubuntu hoary 5.04 which is way differentthan ubuntu hardy heron 8.04.

Please open a new thread for your issue, this one is definitely outdated.

Thanks, thread closed.

---

### Post by frodon on 2008-05-12
You want to reactivate a 3 years old thread ?

This thread was talking about ubuntu hoary 5.04 which is way differentthan ubuntu hardy heron 8.04.

Please open a new thread for your issue, this one is definitely outdated.

Thanks, thread closed.

---

