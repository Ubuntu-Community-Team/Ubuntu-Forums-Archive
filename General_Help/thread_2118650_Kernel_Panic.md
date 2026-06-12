---
title: "Kernel Panic"
date: 2013-02-21
forum: General Help
---

### Post by RideTheSpiral on 2013-02-21
I've got Ubuntu 12.04 installed on my Lenovo Y560 that is coming up on its third year with an Intel® Core&#8482; i5 CPU M 460 @ 2.53GHz, 4gB ram, ATI Mobile Radeon (Forgot which version), with ubuntu installed on an SSD and /home on a 500gB hard disk. 

About four months ago, I went to play a video through HDMI and as soon as I plugged in the cord, it literally fried the ATI chip. It goes all glitchy upon boot and flexing the chassis a little bit will allow ubuntu to boot and most of the artifacts will subside, but once I let go, it locks up and gets extremely hot. This I assume is the BGA of the Radeon card coming loose. 

I'm now stuck using the Intel graphics with the ATI card disabled both in BIOS and Ubuntu. This is fine with me, and is not the problem I'm currently wishing to deal with. Just thought I'd give a little background info.

The problem is that sometimes I'm unable to boot because of a Kernel panic. I can get the laptop to boot by holding the power button to shut down and booting up again. Sometimes it will do the panic 2-3x in a row. This has happened ever since I reinstalled Ubuntu hoping that it would fix what I now know is a hardware problem with the Radeon card. Before I reinstall Ubuntu, I thought I would post here asking for help. I decided to finally snap a picture of the panic screen and am attaching the picture here. The quality isn't the greatest since I snapped the picture with my phone, but everything still seems legible. If needed I will take a new picture with my canon when it happens again.

If there are any more details I can provide, please just ask me and I will do so ;)

---

### Post by blendmaster345 on 2013-02-21
The call trace has many references to 'Radeon', which is being loaded in a module. Try disabling the radeon module, perhaps?

---

