---
title: "How Do I Install Ubuntu 7.10 on a Compaq Armada 100S"
date: 2008-01-18
forum: General Help
---

### Post by Boichot1956 on 2008-01-18
I don't know to much on installing any type of Linux program and I need to learn how.  I have been reading about Ubuntu 7.10 and would like to have this program on my laptop.  I tried running the Live CD of Ubuntu 7.10 but I couldn't get into my BIOS to do this.  I tried but couldn't.  I tried F2, F8, F9, F10, F11, Del Key, Alt F2, Alt F8, Alt F9, Alt F10, and Alt F11.  I couldn't run the Live CD.  What should I do now?  I even burned the Ubuntu 7.10 Alternate Desktop CD.  I am afraid of taking the first step in doing this.  I need step by step instructions how to do this.  I know I need to back up every important file, but after that what do I do?  I can follow instructions when written out and in front of me.  It has to be very detailed and in easy terms that I can understand.  Please help me out.  I know once I learn how to install Ubutu Linux on my laptop I will always remember how to do it.  Please help me.  I want to be able to use Ubuntu 7.10 because I feel more safer with that program than Windows 2000.  I do want to keep Windows 2000 and have a duel boot, but if I can't I need to know how to install Ubuntu 7.10 permentally on my laptop step by step in easy terms if you can.  I do not know all the technical terms as of yet.  Please help me,

Thank you,

Vickie

P.S.  Have a nice weekend:)

---

### Post by jeffus_il on 2008-01-18
Firstly, read this:
[http://users.utu.fi/sjsepp/ubuntu/frameset.html](http://users.utu.fi/sjsepp/ubuntu/frameset.html)

An extract:

> **BIOS settings**

  This laptop's BIOS is rather limited. You can only customize very basic things. To start with, disable all powersaving features from BIOS. You can always turn them on later if you like. Most of the BIOS powersaving features do not affect Linux anyway, so they are pretty useless.
  **NOTE: You must disable the CPU frequency scaling from the SCU!** If you do not disable it, your laptop will hard-lock if you use 2.6 kernel and CPU frequency scaling kernel support. Even with 2.4 kernels it's a good idea to turn it off: it does not scale the frequency without additional (windows) software, and probably even makes the system less stable.
   **Installing Ubuntu**

 With Ubuntu 5.10 I did an expert install, so I can't help with the basic install. The install went quite well, even though "base-config" did not come up after reboot as it should have. Instead "apt" was consuming 97% of CPU for some reason, so I had to kill it forcefully using "ps aux" and "kill -9". It _is_ possible that the laptop would have recovered from this all by itself, but I guess we'll never know ;). Anyway, after the offending process was killed, I was able to run "base-config" and install software with "aptitude". For some reason neither "xserver-xorg" nor the Gnome desktop were installed. So I installed them manually, after which everything worked like it should.
 I hope that the problems I encountered were caused by the (mis)use of "expert" install, because without in-depth knowledge in Debian they would have been hard to fix. So I must encourage you to use the "normal" installation, if possible.
 **NOTE:** Install of Ubuntu 6.06 went well without any problems.
   **Xorg configuration**

 Xorg will work with the "trident" driver. I suggest that you add option
 VideoRam "8192" to avoid any problems. I experienced Xserver lockups on my other Linux (and FreeBSD) installations when "VideoRam" was not explicitly specified.
  My [/etc/X11/xorg.conf]("http://users.utu.fi/sjsepp/ubuntu/ubuntu-xorg.conf") is here for reference.
   **Connecting to network**

  This laptop has only limited means to connect to outside world. Only built-in possibilities are the modem (winmodem, slow...), paraller port (plip, about 40KB/s) and the USB 1.1 port (~400KB/s). As the USB works poorly with older 2.6.x kernels (see [Hardware problems]("http://users.utu.fi/sjsepp/ubuntu/contents.html#hardware_problems")), use of USB-to-USB network cable could be problematic.
  Therefore I suggest that you get yourself a decent network adapter, because you won't get far with the built-in modem or plip connection. If you want only wireless networking then I suggest that you borrow a standard Ethernet adapter (10/100Mbps) from someone until you have your Wireless card configured and working. Even though Ubuntu 5.10 and 6.06 seem to have all basic wireless tools on the installation CD, I wouldn't want to configure wireless networking on any Linux distro without first having a working Internet connection at hand.
  Alternatively you could use "plip" (bi-directional paraller port cable) to connect to the Internet through another Linux computer. I've configured "plip" on this laptop and my desktop just in case my ethernet adapter dies someday. Plip links through Windows box do not work - not at least according to Plip-HOWTO. Note that plip link is not feasible for everyday use, as DMA support is only experimental. It does not matter for the client, but the server will be brought to it's knees. Even my 800Mhz Athlon desktop slows down considerably when data is transfered through the plip link. If you decide to try "plip", check paraller port setting in BIOSes of both computers. Bi-directional mode should work best.
   **Powersave features**

   **APM support**

  With Ubuntu I have not tried APM. In my previous Linux installations, however, I did use APM. APM battery monitor worked, as did two different powersave modes only with minor glitches. Those two powersave modes were named "suspend" and "standby". They were not really that useful: they reduced battery consumption by only 50% or 75%. So you could not leave the laptop just lying around in powersave mode and forget about it. This might be useful in a limited fashion in some cases.
  This laptop has problems recovering from reboot. After a reboot the computer will hang at the "Compaq"-screen. If I remember correctly, this can be fixed with right kernel options in "APM support", as I managed to fix this on some of my custom kernels. If you use a recent 2.6.1x kernel and ACPI instead of APM this problem should not be relevant any more.
   



---

### Post by blackenedbloodx on 2008-01-18
with the live CD just put it in the disc drive and reboot. then click start or install ubuntu and it will load up. after you click the icon on the desktop to install, it has really simple instructions. at the partitioner you are given a little slider that lets you choose the percentage of the hard drive you want for linux. just let it complete without interruptions and it will be fine. if there is a problem in starting up with the CD and i am misreading than im sorry. im still kinda new to this myself :D

or just follow jeffus. he's a pretty smart cookie :)

---

### Post by jeffus_il on 2008-01-18
I looked in your manual, to see which key you have to hit to enter the bios setup at boot, can't find it, try <delete> soon after you turn the machine on,  else try HP support of the documentation disk that came with the machine.

---

