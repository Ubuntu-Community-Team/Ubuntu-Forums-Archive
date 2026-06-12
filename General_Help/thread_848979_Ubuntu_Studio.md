---
title: "Ubuntu Studio"
date: 2008-07-04
forum: General Help
---

### Post by CodyT07 on 2008-07-04
Sorry if it is the wrong forum, but I didn't see one for ubuntu studio (in the 3rd party forums), so if you move this thread please send a pm my way.

One of the reason I moved to ubuntu was to try ubuntu studio. I been reading a few things here and there but here are my questions

*- Ease of use to normal ubuntu (I read the kernal was different and does require some tinkering with)
*- Support for my other apps (e.g Source base games)
*- How does it compare then  just to install the programs it comes with on ubuntu
*- Fiddling with it till you get it to work.(ubuntu has been near 0)
*- Support for my system (64 bit, 64 bit ubuntu didn't work for me even though my system ----should---- support it. Might of been a bad burn) 
*- 64 bit support (a whole nother forum)
---------------------------------------------------------------------
**- Is their a way to quick test you system for 64 bit support.
---------------------------------------------------------------------
*- Better sound (I understand sound is still a working thing on linux in general)

---

### Post by p_quarles on 2008-07-04
> **CodyT07 said:**
> ----------------------
**- Is their a way to quick test you system for 64 bit support.

What kind of cpu do you have?

In many cases, running 
```
sudo lshw
```
will tell you whether you have a 32-bit or 64-bit cpu.

---

### Post by Avinash.Rao on 2008-07-04
Hi,

I am using Ubuntu Studio with LTSP and its working really cool. I downloaded Studio from the ubuntu site about a month ago and did a custom install. My hardware is a AMD 64-bit, Dual core Athlon processor with 2GB RAM, its a normal workstation motherboard.  I am running LTSP, Squid and DHCP as of now. I was in search of an alternative for Adobe products and i came across this, i am still testing the Video/Audio/Image products under UStudio.

I didn't have to do much after install. I had to configure the network coz i am using 2 network cards, display driver thats it. The OS is running fine.

Infact, i have about 10 thin clients logging into the server anytime and its running fine!

1) I have n't checked the games part, may be if you do a full install on Ubuntu Studio you may get it. The purpose of Studio is more on Video and Audio utilities! But, you can download it anyways, use the add/remove option to see if you can find any.

2)  How does it compare then  just to install the programs it comes with on ubuntu - didn't understand this question.

3) Ubuntu desktop edition is really cool, if you have an internet connection, all the required updates/libraries are downloaded automatically. So, there's nothing to worry. The only thing you have to do is install on the recommended hardware so that all the utilities and libraries work without any problem.

4) The Ubuntu Studio 8 or just Ubuntu 8.0 CD supports both 64-bit and 32-bit hardware. Its a live CD, so you can just boot through the CD and check how Linux works! Its working for me. Coz, the first time, i installed Ubuntu 7.0 32-bit OS. when i got the latest version of Ubuntu 8.0 it was platform independent, in the sense i could install it on both 32-bit as well as 64-bit hardware.

5) *- Is their a way to quick test you system for 64 bit support. - Use the Live CD: The latest ubuntu OS CDs(I guess from version 7 onwards) is a live CD. so you can just boot through the CD and check how Linux works!

6) Sound: Sound works really on my machine. Are you having any trouble with the sound on Linux. Coz, booting your machine through the LIVE CD will show you what all will work, including sound, network, Display, etc..

Cheers,
Avinash




> **CodyT07 said:**
> 
One of the reason I moved to ubuntu was to try ubuntu studio. I been reading a few things here and there but here are my questions

*- Ease of use to normal ubuntu (I read the kernal was different and does require some tinkering with)
*- Support for my other apps (e.g Source base games)
*- How does it compare then  just to install the programs it comes with on ubuntu
*- Fiddling with it till you get it to work.(ubuntu has been near 0)
*- Support for my system (64 bit, 64 bit ubuntu didn't work for me even though my system ----should---- support it. Might of been a bad burn) 
*- 64 bit support (a whole nother forum)
---------------------------------------------------------------------
**- Is their a way to quick test you system for 64 bit support.
---------------------------------------------------------------------
*- Better sound (I understand sound is still a working thing on linux in general)

---

### Post by logos34 on 2008-07-04
Search 'ubuntusudio' on this page:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Read through the docs. Should answer most of your questions.

Here's another link:
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-8.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-8.04)

I run x64 studio and it's almost identical to regular ubuntu.  Smooth.  With the exception of suspend/hibernate issues (since solved), no more problems than I had in 32-bit.  For average desktop use you don't need to tweak anything (well, maybe one or two parameters but that's about it).  The kernel is the major difference--runs the real-time/low-latency -rt version.  Bit more zip, but otherwise hard to tell any diff.

If you can run the 64-bit live cd, then you have a x64 support; other than that google the specs of your processor model number

cat /proc/cpuinfo

EDIT: or do as p_quarles suggested and run lshw

I wonder why lshw shows "x86-64" capability, but cat /proc/cpuinfo doesn't...hmmm

---

### Post by CodyT07 on 2008-07-04
> **p_quarles said:**
> What kind of cpu do you have?

In many cases, running 
```
sudo lshw
```
will tell you whether you have a 32-bit or 64-bit cpu.
It has support for x86-64 technology according that command.

> 2) How does it compare then just to install the programs it comes with on ubuntu - didn't understand this question.
What I meant was, Install of installing ubuntu studio, just install the programs it comes with by default on normal ubuntu

Okay, a few more opinions here and there would be great. 

*- Can I install 64 bit ubuntu studio on top of 32 bit ubuntu? Lets say my burners aren't exactly the best around. And I have slow internet, and my programs are rather huge and need to be downloaded from the internet...

---

### Post by Avinash.Rao on 2008-07-04
In the official Ubuntu and ubuntu Studio Download page, you have two different downloads one for 32-bit and 64-bit hardware either on Intel or AMD. 

It should work, I am assuming that the OS install should detect the hardware type and install the correct kernel for the hardware. Thats what happened to me. 




> **CodyT07 said:**
> It has support for x86-64 technology according that command.


What I meant was, Install of installing ubuntu studio, just install the programs it comes with by default on normal ubuntu

Okay, a few more opinions here and there would be great. 

*- Can I install 64 bit ubuntu studio on top of 32 bit ubuntu? Lets say my burners aren't exactly the best around. And I have slow internet, and my programs are rather huge and need to be downloaded from the internet...

---

### Post by CodyT07 on 2008-07-04
> **Avinash.Rao said:**
> In the official Ubuntu and ubuntu Studio Download page, you have two different downloads one for 32-bit and 64-bit hardware either on Intel or AMD. 

It should work, I am assuming that the OS install should detect the hardware type and install the correct kernel for the hardware. Thats what happened to me.

You talking about a clean install? 
I want to upgrade my current ubuntu 36 bit to ubuntu studio 64 bit. Without the need to reinstall all my programs.

---

### Post by Avinash.Rao on 2008-07-04
Are you saying you just want to upgrade the kernel to 64-bit.? or if you want to upgrade from ubuntu 32-bit to Ubuntu studio 64-bit, the programs will change! Coz, the whole kernel will change in ubuntu Studio. As far as i know, you have to reinstall the programs if you upgrade the OS Kernel.

Hope this helps

> **CodyT07 said:**
> You talking about a clean install? 
I want to upgrade my current ubuntu 36 bit to ubuntu studio 64 bit. Without the need to reinstall all my programs.

---

### Post by p_quarles on 2008-07-04
> **CodyT07 said:**
> You talking about a clean install? 
I want to upgrade my current ubuntu 36 bit to ubuntu studio 64 bit. Without the need to reinstall all my programs.
Can't be done.

---

### Post by logos34 on 2008-07-04
right, you can't do a cross-architecture upgrade.  You'll have to reinstall and dl all the pkgs again because x64 ubuntu can only use the x64 debs

---

