---
title: "Boot issue"
date: 2007-07-13
forum: General Help
---

### Post by nelsondumais on 2007-07-13
I installed Wubi on a Core Duo with Vista. All went well. But when I choose "Ubuntu" on Windows boot manager, I don't go very far. After a few seconds, I get this message : "*Can't access ttx: job control turmed off*". Then it says :" *(initramfs)*. Any clue why? Thank you.

---

### Post by nelsondumais on 2007-07-13
I solved it!!!

The message "*Can't access tty: job control turned off*" only meant I had to remove from my PC the USB2 cable connecting an external SATA drive. No kidding!

Why can't operating systems talk plain understandable English?

---

### Post by ago on 2007-07-13
Hmmm a USB2 sata drive should not trigger a failure anyway...

---

### Post by ago on 2007-07-13
Can you please run the installer with the cable attached and provide me with the zenigata.log and lupin.log in /tmp?

---

### Post by CrazyGuy123 on 2007-07-13
Great job for finding the problem.  Just for the record, "Can't access tty: job control turned off" is more of a generic error caused while starting a shell, (and a shell is only used to fix and diagnose problems if something goes wrong)

You could have seen the real error by turning off the "quiet splash" options while starting up.

---

### Post by nelsondumais on 2007-07-16
Dear **Ago**,

You asked me to run the installer with the cable attached and paste to your attention the *zenigata.log* and* lupin.log*.  It was kind of you, so I got to work. 

-	I booted my PC on Vista and fired the Wubi 7.04 icon on my desktop.
-	I uninstalled Wubi
-	I reinstalled Wubi + Feisty Fawn
-	The installer rebooted the PC and finished its installation without any GUI
-	It then rebooted and told me it had failed to start the X Server!

It is then I decided to quit and write an article about being unsuccessful with Wubi. 

I must admit having been writing about technology in major Quebec medias for over two decades. I’m a career reporter who, amongst other techno-things, gives time and pays attention to the Open Source Movement and to the Linux phenomenon in particular. With time, I’ve become clever on a Mac and a PC, a status I’ve not yet attainted, though, on a Linux or on a Solaris system. As for the PC I use for reviews, it’s a Core 2 Intel 6600 (2.4 GHz) with 2 Gb of RAM, SATA HD, and Radeon X1900 PCI Express graphic adaptor, *happily *running Vista Ultimate (*a couple of weeks ago, it refused to run Solaris 10 on a brand new SATA drive*).

This time, my project was to install Wubi and write a nice cool story on how it had been easy and straight forward, using as many screen dumps as necessary. Since Wubi has been designed to please people like me (many of us *suffering *with ATI boards), people that would appreciate rebooting painlessly on a cool Linux configuration and the go back to Windows, I thought it was a great idea I should support. 

But it screwed up. Here’s why:

-	If I install Wubi with my 20-inch LCD monitor connected to the ATI board, I never go further than the X Server failure;
-	If I install it with my monitor connected to the on-board video resources, I get way beyond the *Can't access tty *message which, as I already told you, I outfox unplugging a stupid USB2 cable;
-	Doing so, I can access the Ubuntu desktop, do all required updates and even give a shot at Beryl; 
-	But I can’t install the missing ATI drivers. I can’t even modify (using GEDIT) the X Server file to let it know I’m using all generic devices so it can stop bugging me if I want to use my ATI board. For that I need to boot connected to ATI, not on the PC's mother board. Once Ubuntu is installed with the monitor connected to the ATI board, it refuses to start with the monitor connected to the on-board video resources. And vice versa.
-	I’m not familiar enough with Linux to solve that problem in console mode.

As a result, I can’t boot either on Vista or on Ubuntu without, each time, changing my monitor connection.

When you asked me to generate some log files, I reinstalled Wubi (*for a sixth time*) with the monitor … stupidly attached to the ATI connector. I thus destroyed the gorgeous Berylized installation I had achieved with the monitor on the on-board connector and smashed my nose, once again, on the X Server failure. So, I got a little aggravated and decided to put a stop to my agony and move on to some other review project. After all, I’ve got Ubuntu up and running on another PC and that’s enough for my Linux crave. BTW, there’s no ATI board on that PC…

The problem seems to be the fact Ubuntu and ATI aren’t nice to each other. In the same time, there’s an awful lot of Linux illiterate ATI users out there, people Wubi has been designed for. So far, I’ve tested a few recipes on the Ubuntu forums to solve some of my issues and it hasn’t worked at all. In other words, the effort necessary to tweak Wubi/Ubuntu, to make it work in a PC environment like mine (which isn’t hard to find at all), is too hard and people will tend to quit, which is not what Wubi is all about.

That’s what I’m going to write in my story. 

But again, I might be all wrong and it could be, once again in my reviewer life, something specific to me, like my attitude, my lack of knowledge or, who knows, my PC that turned corrupted overnight just prior to the Wubi revew. 

It’s life!

Thanks for trying to help.

---

### Post by ago on 2007-07-16
> **nelsondumais said:**
> The problem seems to be the fact Ubuntu and ATI aren’t nice to each other.

Yep that's a known problem. Usually it should be enough to install the linux restricted modules (linux-restricted-modules-generic restricted-manager) and the proprietary ati driver (xorg-driver-fglrx) , or even with the restricted-manager. See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

We will try to fix that in coming releases. I appreciate it is very annoying when people cannot boot at all into a graphical environment and I am aware of the issue. 

As for USB I start having a theory but I'd need some detailed logs. It's difficult for me to debug issues I cannot reproduce.

> In the same time, there’s an awful lot of Linux illiterate ATI users out there, people Wubi has been designed for.
I do not have the resources to compensate for the lack of cooperation from hardware manufacturers, I wish that could be fixed properly, all we can do is find workarounds, and it's not always obvious.

---

