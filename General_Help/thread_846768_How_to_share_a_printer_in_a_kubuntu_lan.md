---
title: "How to share a printer in a kubuntu lan?"
date: 2008-07-01
forum: General Help
---

### Post by ruipedroca on 2008-07-01
Hi,

I've got a kubuntu machine connected to a usb printer.
That same kubuntu machine is sharing, via nfs, some files with a second kubuntu machine.

**What do I need to do so that second machine can print to the printer attached to the first kubuntu machine?**
All the tutorials i find are between kubuntu and windozs...

All kubuntu machines are Hardy Heron.
The printer is a all-in-one HP J5700

Regards

---

### Post by txcrackers on 2008-07-02
Install the Gnome-based printer configuration package (*system-config-printer-gnome*) and use it on both the server and the client(s)- the KDE version is still apparently busted.

On the machine the printer's attached to, make sure to mark the auto-discovered printer as "shared". It should automagically show up in the other machines(s).

---

### Post by ruipedroca on 2008-07-02
Thanks, txcrackers! 

Works great!! Practically out-of-the-box!!

The only thing weird that happened was a small empty window that appeared after the installation, which i guess was because I use KDE and this tool was originally built for Gnome. 

Also, there's an entry in System/Printing which as no icon, but, nevertheless it works! I just had to restart the computer, go to the gui in System/Printing and select the printer.

Before, I've tried the KDE gui, but like you said, it just didn't work and it was much more complicated.


Thanks!!


Regards!!

---

