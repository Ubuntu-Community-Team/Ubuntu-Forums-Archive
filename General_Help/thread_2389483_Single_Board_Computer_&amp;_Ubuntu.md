---
title: "Single Board Computer &amp; Ubuntu"
date: 2018-04-17
forum: General Help
---

### Post by timc00k on 2018-04-17
I can download Ubuntu from this site and install it on my desktop without any issues.

Using the same copy of Ubuntu, is there any Single Board Computer that I can buy and install the same copy of Ubuntu on it?  

Thank you

---

### Post by QIII on 2018-04-17
Hello!

There are a few x86/x86_64 SBCs out there that would be able to install just about anything you'd care to.  But they are quite expensive.  Here's an example from [UDOO]("https://shop.udoo.org/usa/udoo-x86-ultra.html").

I'm going to assume that you are talking about one of the less expensive ARM boards like the Raspberry Pi or Odroid.  In that case, no: If you download an x86/x86_64 version of Ubuntu from Canonical it won't work.  (Canonical does have an ARM version of Ubuntu Server available for download by the general public, but there is no guarantee it will work on any particular SBC because each has its own particular hardware and you might not get suitable drivers.)

However, many SBC manufacturers provide a port of Ubuntu that is tailored to their boards.  I've had a couple of R Pis and Odroids that ran the manufacturer's versions of Ubuntu.  For all intents and purposes, they have worked just like the x86 versions.

Right now I have an R Pi that powers a large-format picture frame.  I installed the R Pi version of Ubuntu MATE on it and run video slideshows with zooming, panning and fade-in/out using omxplayer (which uses H.264 hardware acceleration -- great for video too!).  There would certainly be some x86 software from Canonical's repos that wouldn't work, but both Canonical and R Pi supply ARM ports for a great deal of it.  The experience of running it is indistinguishable from an x86 version of Ubuntu MATE.  I even update it remotely with Ansible Tower using the same playbook as all of my other Ubuntu/Debian machines.  That is, it can be administered on a network just like any other machine.

There are a lot of us here who run Ubuntu on ARM devices, so you'll have access to help!

Cheers!

---

