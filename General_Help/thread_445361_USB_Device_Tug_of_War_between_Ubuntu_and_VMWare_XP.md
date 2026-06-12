---
title: "USB Device Tug of War between Ubuntu and VMWare XP?"
date: 2007-05-15
forum: General Help
---

### Post by Sparkypine on 2007-05-15
Bit of a Ubuntu n00b here but I'm proud of how far I've gotten so far.  I have Ubuntu 6.10 with VMWare Workstation v6 hosting XP SP2.  I am running XP in VMWare so that I can use it as a Vosky Call Center/Skype server.  Vosky does not have USB driver support for Ubuntu...and Wine just doesn't do USB.

After getting XP up and running and settled down, I attempted to install the Vosky USB device.  However, I had to go into the menus VM>Removable Devices>USB Devices and seize control of the Actiontec Vosky box.  However, it seemed that Ubuntu kept taking it back (?)  After every reboot I had to go in and seize control of that Vosky device.  I finally checked the "do not remind me again" box.  Now VMWare keeps control of the Vosky box.  I still see the Vosky instance in the Ubuntu Device Manager, but VMWare still seems to have control.

However, call quality stinks and the CPU shoots up to 100% while I am making a call..it settles back down after the call is ended.  Sound quality is also choppy during the call and cuts out.  My hunch is that maybe Ubuntu and VMWare are still trying to play tug of war.  Is it possible that Ubuntu is still attempting to seize control of that USB device and VMWare is just quickly taking it back...so that there's this eternal struggle between good and evil that ultimately spikes my CPU?  Is there a way I can tell Ubuntu to leave that particular USB port alone?

I know it can be a sound issue, Skype issue, Vosky driver issue, network issue, etc, etc. but, since I *had* trouble with the USB port, I thought I'd start there.  I have 1gig of RAM on the box and half is dedicated to VMWare.

---

