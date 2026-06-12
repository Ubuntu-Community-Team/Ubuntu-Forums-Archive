---
title: "how to install application on ubuntu live usb"
date: 2017-04-04
forum: General Help
---

### Post by giobaxx on 2017-04-04
Good Evening guys


A colleague told me about the possibility of being able to install software into a live version of ubuntu? Can you tell me if is it possible? My goal would be to prepare a live version of Ubuntu with a spefic  antivirus  installed (McAfee Command Line Scanning )

---

### Post by Bucky Ball on 2017-04-04
McAfee in Ubuntu? News to me, but that doesn't mean much.

Installing anything in a live session (Try Ubuntu using install media) is a waste of time as it will be lost on reboot. A live session retains nothing on reboot.

To do what you're wanting you would need an install to USB which can be easily achieved. You could also use a 'persistence' install, which I think is much the same thing. I've never used a persistence install so you will need to do some research there.

Good luck.

PS: The Command Line Scanner, if that's what you're talking about, is well dead by the looks of it. 

> Command Line Scanner is inddded End of life now and the End of Support by McAfee for this product is Jan 2011.

[From here]("https://community.mcafee.com/thread/23319?start=0&tstart=0").

---

### Post by sudodus on 2017-04-04
There are two alternatives, to make what you install and tweak survive after shutdown and reboot.

1 - You can create a ***persistent live*** drive and install some programs.

2 - You can create an ***installed system*** (like installed into an internal drive but to a USB drive or memory card).

See this link and links from it for more details, [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by giobaxx on 2017-04-04
Im not at work but the correct version should be McAfee VirusScan Command Line for Linux and is not my choice but what i have to use.....i look for a persistent solution, so a way to customize a custom image of ubuntu.
Becasue for the moment i have to install the AV each time  i run a live version...

---

### Post by sudodus on 2017-04-04
- What media do you intend to use? A USB pendrive? In that case what brand name and model?

- Would you mind getting a new and better one, to get better performance?

- Do you intend to use this system in one computer or should it be portable between many computers? What computer(s)? Brand name and model)?

---

### Post by lisati on 2017-04-04
*Thread moved to **General Help**.*

---

### Post by giobaxx on 2017-04-04
Basically i have to perform an Offline Scan  for about 30 Workstation installed with various OS(Ubuntu Windows Red HAT).  I have to use McAfee VirusScan Command Line for Linux in a live version of Ubuntu.
I did the same some months ago and everytime i had to install the antivirus and update the definition.....is very boring. It would be useful to prepare a persistant installation on a usb stick to use in this scanning
[COLOR=#000000]
[/COLOR]

---

### Post by gordintoronto on 2017-04-04
See this tutorial about creating a Live USB with persistence:
[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by sudodus on 2017-04-05
If you have an Ubuntu system, you can install mkusb, which can create a persistent live system in a USB drive or memory card. See these links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by giobaxx on 2017-04-08
Tanks a lot i will try to learn!!!

---

### Post by C.S.Cameron on 2017-04-08
It is my experience that a Full install to flash drive boots considerably faster than a Persistent install.
It would save a lot of time using a Full install flash drive if 30 computers need to be scanned each session.
A Full install flash drive should work on all of the computers as long as no proprietary drivers are installed.

---

