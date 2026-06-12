---
title: "how to make a TRULY persistent Ubuntu live USB/DVD"
date: 2015-03-12
forum: General Help
---

### Post by lampface on 2015-03-12
hello guys thanks 4 reading. anyways what i wish to do is,
#1 ensure the USB keeps  all of my stuff, e.g documents packages settings ect.
#2 have user accounts, this is very important.
thanks for your help in advance.
[COLOR=#141823][FONT=lucida grande]&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#2972;&#1769;&#1758;&#1769;&#2972;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;
                                 lamp face[/FONT][/COLOR]
[COLOR=#141823][FONT=lucida grande]&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#2972;&#1769;&#1758;&#1769;&#2972;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;&#9644;[/FONT][/COLOR]

---

### Post by nerdtron on 2015-03-12
If you need a full Linux environment on a USB thumb drive why not do a full install?

You need two USB sticks, one for the live installer and another one as the "usb hard drive".
1. disconnect internal drives to prevent damaging your existing data.
2. Plug both USB on the computer and boot the installer usb drive.
3. Once you are on the live environment, install Ubuntu on the other USB drive.

You're done and you should have a full blown (and persistent) install on the usb drive. Just keep in mind the read/write speed is a little slower on a usb drive but everything should still work.

---

### Post by ian-weisser on 2015-03-12
A DVD cannot use persistence nor save anything - it's read only.

The Live environment is intended for testing and tryout - it's not intended to be a permanent solution, which it why it has so many limitations.
To get the full benefit of all Ubuntu's features (accounts, upgrades, storage, etc), you must actually *install* it.

However, you CAN install to a (different) USB stick instead of the hard drive, as nerdtron described above.
It's a real install, a full-featured system. Storage (on the stick), upgrades, accounts, everything.
Be sure to install to a USB2.0 (minimum) or higher USB stick plugged into a USB2.0 (minimum) port. Lower speed causes the system to run very slowly. USB1.1 is much slower than HDD for all the disk I/O.
Do not expect your USB stick's life to exceed a few months, sometimes more, sometimes less. The I/O load of running a full system off the stick wears out the memory.

---

