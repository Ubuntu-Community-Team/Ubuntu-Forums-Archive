---
title: "Secondary Monitor confusion"
date: 2008-06-16
forum: General Help
---

### Post by lost09 on 2008-06-16
I am trying to use an Envision secondary monitor with a Toshiba laptop running Ubuntu 7.10. The last time I tried this, things rapidly escalated into a hopeless mess (laptop monitor stopped working, etc) such that I had to wipe my hard-drive and reinstall the OS. In fact, if I start the computer with the secondary monitor plugged in, output is permanently redirected to it (at horrible resolution). 

Can anyone please explain how to spill the desktop onto the secondary monitor, without losing the main display, and with the ability to spill-on/off at will? 

Many thanks.

---

### Post by Pjotr123 on 2008-06-16
All I can say is, I had a hard time with that in 7.10 as well. Ubuntu 8.04 however, has a completely new system of recognition of video hardware, so that now using a secondary monitor is easy and painless.

So I'd say: consider a switch to 8.04. Do it the safe way, like this:
[http://ubuntutip.googlepages.com/upgrading](http://ubuntutip.googlepages.com/upgrading)

After the installation of 8.04, this command may prove useful:
gksudo displayconfig-gtk

Greeting, Pjotr.

---

### Post by lost09 on 2008-06-16
Thanks; I have class now, but I'll certainly try to upgrade later this evening. I'm not sure how the process works, though. Is it like reinstalling the operating system, or merely changing some things about the current one? And what is this "/home" partition of which it speaks?

---

### Post by Pjotr123 on 2008-06-16
If you don't know what a separate home partition is, then you probably don't have one on your computer. :-)

---

### Post by lost09 on 2008-06-17
I received the following error upon checking for updates via Update Manager: 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I think I can still upgrade to 8.04, but what does the above mean?

---

### Post by lost09 on 2008-06-17
Due to internet troubles, I have had to restart the download twice. Will this cause problems?

Also, following the link in the previous error message did nothing to lessen my confusion. Any help would be infinitely appreciated.

---

### Post by lost09 on 2008-06-20
Alright, I've about had it up to my neck with this external monitor nonsense. The technical people at my university told me to simply plug it in and select "detect displays" under "screen resolution". This had absolutely no effect. The closest I have come to getting it working was starting the computer with it plugged in, but that resulted in the computer apparently being tricked into believing that only one monitor exists (deselecting "clone screens" had no effect). 

I am on my knees begging for help here, as I've been trying off and on to get this working for months, to no avail. 

I am, however, successfully running 8.04 now.

---

### Post by lost09 on 2008-06-20
I tried tampering with the BIOS settings, but it seems I'm still stuck with cloned screens regardless of my actions. Also, the resolution is off. 

Someone, anyone, please help! *collapses*

---

### Post by lost09 on 2008-06-21
Bump.

Also, Envy doesn't seem to help. :(

---

### Post by lost09 on 2008-06-21
Anyone out there?

---

