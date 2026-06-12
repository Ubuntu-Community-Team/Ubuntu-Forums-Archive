---
title: "How to install a PCI USB Host Adapter in Ubuntu 7.04"
date: 2007-05-09
forum: General Help
---

### Post by frankie68 on 2007-05-09
Hi,

I just installed Ubuntu 7.04 on a Dell XPS PII 400Mhz. So far so good but as the machine is quite old it had only 2 USB 1.1 slots so I decided to equip it with a PCI USB 2.0 host adapter.

I bought a noname USB adapter but it does not come with Linux drivers. The adapter chipset is from NEC and that's about all I know.

I plugged the adapter in a free PCI slot and booted the box however, the adapter is not recognised and the system does not seem to react when a USB device is plugged into it.

The integrated USB 1.1 works since the beginning.

I have tried to find a "How to" to add such USB adapter in Linux the whole afternoon but could not find anything so I guess I am searching in the wrong direction. I could not find any help in the doc neither.

So my question is: where do I start? Is there a tool to detect the adapter (hardware) and then install drivers? How does this work?

Of course I already thought I could re-install the whole box and I bet the install would detect everything right but I guess there must be something more elegant before the hammer.

Thanks for your help,

Frank

---

### Post by frankie68 on 2007-05-11
Hi there,

OK, don't ask why but after taking off the card in despair of finding some useful information and plugging it in again... miracle, it is recognized and works as a breeze.

Anyway, in the meantime, I made some research and if you are like me wondering how to load a driver in Ubuntu (or Linux), the command is "modprobe" "drivername". In fact, to be absolutely correct, the driver is called a module that is loaded with the kernel. To load the module at each boot just add it to /etc/modules with your preferred text editor (need to be root).

Oh, yes, I got the info from "The Official UBUNTU Book" ISBN 0-13-243594-2.

BTW I have now two boxes running under Ubuntu 7.04 with Automatix2 (if you don't know what Automatix2 is, just google it, it's another brilliant surprise of the open source community) and I am just amazed how fast this was to install a box with all the apps I need.  Nothing to compare with my last install of XP !!!!

Final comment, if you have an old Pentium II and don't want to dump it, just get a cheap fast ATA 133 disk (with the interface). Don't forget to run hdparm with the right parameters and you give a new life to your old box....

---

