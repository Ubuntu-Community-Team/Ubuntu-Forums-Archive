---
title: "Installing ubuntu from usb"
date: 2020-01-13
forum: General Help
---

### Post by Tom_Carr on 2020-01-13
Several questions -

Where are the most up to date instructions online?

What size USB flash drive do you need?  I have a 4GB here.  Will that do?

---

### Post by TheFu on 2020-01-13
Should. Depends on the specific size of the flavor of Ubuntu you will be "burning" to the flash drive.  Everything on it will be wiped.  Whenever you seek something related to Ubuntu how-to stuff, help.ubuntu.com  and tutorials.ubuntu.com are a good places to start.  


As for how to actually create a bootable, installable, flash drive, is the official answer:
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
There are links for how to do it for other OSes on that page too.

There are 50+ other answers, but those generally are more complex to someone new. Best to stick with the official answer that has been followed by thousands of relatively new-to-Linux people.

[https://help.ubuntu.com/](https://help.ubuntu.com/) has desktop and server User Guides for LTS and non-LTS releases, when you need that.

---

### Post by bernard010 on 2020-01-13
[URL="https://help.ubuntu.com/stable/ubuntu-help/index.html"]
https://help.ubuntu.com/stable/ubuntu-help/index.html[/URL]

Ubuntu 19.10 Desktop Guide

[URL="https://help.ubuntu.com/community/Installation/FromUSBStick"]https://help.ubuntu.com/community/Installation/FromUSBStick 

[/URL]Installation/From USB Stick

Yes to your question 4 GB is large enough for CD size .iso images and some
DVD file sizes. This is the latest up to date information for Ubuntu & Flavors.

[https://wiki.ubuntu.com/Releases ]("https://wiki.ubuntu.com/Releases")End of life for releases  18.04.3  LTS  2028 //  19.10  July 2020

Use Etcher to load .iso image (OS) Ubuntu on a USB the easiest way.

[https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

### Post by dragonfly41 on 2020-01-14
@Tom_Carr

It is not clear to me, from your recent posts, if you have progressed to running or even trying Ubuntu.

If we assume that you are still using Windows then one approach is to start by installing Rufus in Windows to burn into a USB or DVD a Ubuntu *.iso.

[One tutorial here]("https://www.computerhope.com/issues/ch001832.htm").

One of the fullest tutorials I have found in recent days is [here]("https://forums.linuxmint.com/viewtopic.php?t=287353").

I would bookmark it alongside many other posts.  It can be confusing but half the battle is understanding the terminology.

On the matter of flash drives for the LiveUSB  these can be purchased in[ most stores and supermarkets]("https://www.currys.co.uk/gbuk/computing-accessories/data-storage/usb-flash-drives/sandisk-ultra-usb-3-0-memory-stick-16-gb-black-21755388-pdt.html").

Check whether you have USB 3.0 or the older generation USB 2.0 ports.

---

### Post by C.S.Cameron on 2020-01-14
The most up to date discussion on Bootable USB drives is  **Howto make USB boot drives**: [https://ubuntuforums.org/showthread.php?t=1958073&](https://ubuntuforums.org/showthread.php?t=1958073&)

It is probably **overkill** for your needs.
If you are making a bootdrive in windows either UNetbootin or Rufus are easy to use and work for both UEFI or BIOS computers.

---

### Post by dragonfly41 on 2020-01-15
To complete the list of options there is an interim option which avoids the dual boot route.

It is to install VirtualBox in Windows 10 and then install a virtual Ubuntu image.

[Tutorial here]("https://itsfoss.com/install-linux-in-virtualbox/").

It could be a good interim step to learn Ubuntu. But remembet that it is a virtual Ubuntu machine running within Windows and factors such as memory size should be considered.

---

### Post by Tom_Carr on 2020-01-17
> [COLOR=#000000]It is not clear to me, from your recent posts, if you have progressed to running or even trying Ubuntu.[/COLOR]

I have been using it for years, but have always installed with a CD or DVD.  I will be making the boot drive on my computer running ubuntu 18.04.

I have been using ubuntu for a long time but am not a power user.  I just know enough to install it and use the  GUI and Chromium.

---

### Post by bunny9000 on 2020-01-17
unetbootin always works for me for Linux / Windows. If it doesnt, use rufus

---

### Post by mörgæs on 2020-01-18
> **bernard010 said:**
> [URL="https://help.ubuntu.com/stable/ubuntu-help/index.html"]
[/URL]
[https://wiki.ubuntu.com/Releases ]("https://wiki.ubuntu.com/Releases")End of life for releases  18.04.3  LTS  2028 //  19.10  July 2020


The column *end of life* refers to extended, paid support mostly relevant to corporate customers. The five year free *standard support* is what matters to the normal individual user.

---

### Post by sudodus on 2020-01-18
> **Tom_Carr said:**
> Several questions -

Where are the most up to date instructions online?

What size USB flash drive do you need?  I have a 4GB here.  Will that do?

**4 GB is enough to create a live drive of all official Ubuntu versions and flavours.** This is enough in order to install Ubuntu into an internal drive. (But if you want a persistent live drive (for example to use during travelling, it is a good idea to have a fast USB 3 drive with at least 16 GB.)

> **Tom_Carr said:**
> I have been using it [Ubuntu] for years, but have always installed with a CD or DVD.  I will be making the boot drive on my computer running ubuntu 18.04.

I have been using ubuntu for a long time but am not a power user.  I just know enough to install it and use the  GUI and Chromium.

In this case I would recommend that you use the [**Startup Disk Creator**](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Ubuntu), that is part of Ubuntu 18.04 LTS.

It is a robust cloning tool, very easy to use, I think the description in the previous link and the stepwise instructions in next link will be enough for you.

[**This link shows the official description by Canonical**](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0), the company that creates and maintains Ubuntu.

[hr][/hr]
If you want a tool with more options, you can install [mkusb via a PPA](https://help.ubuntu.com/community/mkusb),

If you run standard Ubuntu live, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)
```

sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi

```

---

### Post by Tom_Carr on 2020-01-18
One other related question - Why is installing from a usb drive superior to installing from a DVD?

---

### Post by CelticWarrior on 2020-01-19
> **Tom_Carr said:**
> One other related question - Why is installing from a usb drive superior to installing from a DVD?

First of all, optical media is *de facto* obsolete now.

Optical media is slow and comparatively expensive in the long run. Much slower burning & much slower reading.
Also prone to errors that once burned to WORM (write one read many) media that is a loss.
Any modern PC is designed to boot and install from USB; Optical drives are becoming a rarity.

Do you need more reasons?

---

### Post by mörgæs on 2020-01-19
> **Tom_Carr said:**
> One other related question - Why is installing from a usb drive superior to installing from a DVD?

It's not. The result will be the same. 

One can also install a minimal text-only Ubuntu from a CD and add all remaining packages from the repository later. Same result in the end.

---

### Post by dragonfly41 on 2020-01-19
**[A]** Evolution

Here is a shot of the *second* computer I worked with. [The Elliott 903]("http://www.computermuseum.org.uk/fixed_pages/Elliott_903.html").
Back then, programs were created on paper tape and patches were manually spliced into the paper tape.
See on that page at bottom the 18bit console panel.
Code was written by keyboard in octal.

Today we are moving to SSD.

---

### Post by Tom_Carr on 2020-01-19
> [COLOR=#000000]Here is a shot of the [/COLOR][I]second computer I worked with. [The Elliott 903]("http://www.computermuseum.org.uk/fixed_pages/Elliott_903.html").
Back then, programs were created on paper tape and patches were manually spliced into the paper tape.
See on that page at bottom the 18bit console panel.
Code was written by keyboard in octal.[/I]

You must be even older than I am.  The first computer I worked on was an NCR mainframe.  We wrote out  all the code on paper coding form, then gave them to the keypunch ladies (and they were always women, the programmers were all men).   They punched out the cards and then we fed them into the computer.  Night operators fed in the programmers  work at night, because the computer was only used  for production work during the day.

---

### Post by Tom_Carr on 2020-01-19
Ignore this post.  How do I delete a post?

---

### Post by sudodus on 2020-01-19
> **Tom_Carr said:**
> You must be even older than I am.  The first computer I worked on was an NCR mainframe.  We wrote out  all the code on paper coding form, then gave them to the keypunch ladies (and they were always women, the programmers were all men).   They punched out the cards and then we fed them into the computer.  Night operators fed in the programmers  work at night, because the computer was only used  for production work during the day.

Similar to me. During my studies, I made a small program in Algol, that was given to keypunch ladies amd then fed into a big main-frame computer shared between the defence department and the college. Need I say that debugging was very slow. After that experience I said that I will never work with computers. And here I am :-P

> **Tom_Carr said:**
> Ignore this post.  How do I delete a post?

You can report it (with the 'Report Post' button in the bottom left corner) and a moderator can delete it.

---

### Post by Tom_Carr on 2020-01-19
I would like to download the current version of ubuntu 20.04 and make a bootable usb drive with it.  I know 20.04 is in beta, but I would like to play with it.
I can't find anywhere to download it.  I went here:

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

But they only have 18.04 and 19.10.

---

### Post by dragonfly41 on 2020-01-19
I think that the exact model of the 10 year old Acer needs to be cited. Also USB port spec. 32bit or 64bit architectore? Then google usually unearths a tutorial. I have seen several.  [Search through the sticky threads on using old systems]("https://ubuntuforums.org/showthread.php?t=2130640").

Also to zero in on Acer, use the Advanced Search in this forum using Acer as one keyword. You can also search by author.

[Later edit] UEFI was not around 10 years ago.
[https://community.acer.com/en/discussion/552588/acer-aspire-5733-will-not-boot-from-usb](https://community.acer.com/en/discussion/552588/acer-aspire-5733-will-not-boot-from-usb)

This answer relates to an earlier post above which apparently has been deleted.

...

Incidentally here is another reason for dropping DVD. You can subsititute DVD for a second HDD or SSD in a caddy. This avoids sharing with Windows.

---

### Post by sudodus on 2020-01-19
> **Tom_Carr said:**
> I would like to download the current version of ubuntu 20.04 and make a bootable usb drive with it.  I know 20.04 is in beta, but I would like to play with it.
I can't find anywhere to download it.  I went here:

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

But they only have 18.04 and 19.10.

[Download the daily iso file from this link](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds/206401/downloads)

**zsync** is a nice tool, that you might install and use (instead of regular http downloading).

---

### Post by Tom_Carr on 2020-01-19
I got the ACER to work.  

Thanks everyone for all you help on this.  I am going to mark the thread as solved.

---

