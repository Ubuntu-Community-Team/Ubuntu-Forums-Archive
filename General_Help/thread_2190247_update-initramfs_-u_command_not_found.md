---
title: "update-initramfs -u command not found"
date: 2013-11-26
forum: General Help
---

### Post by bookie2 on 2013-11-26
Hi guys 
I have looked at lots of threads but none seem to solve the simple question...
I have Ubuntu 12.04 after upgrading and I don't like Unity, so I installed gnome..
I have tried to set login/logout splashes and this is where it goes pearshaped.
When I try to apply Changes and run #sudo update-initramfs -u as seen on many threads I get...update-initramfs command not found?!

I then shutdown my Ubuntu and low and behold my splash is there...even though I haven't run update-initramfs?!
But no splash login on start just the standard Ubuntu splash?

Can anyone get me started in the right direction...

I upgraded from 10.04 and had a working boot splash which was set via grub customizer...now I have a debian boot splash after adding Gnome...
Need some help here....lol

bookie2

---

### Post by ajgreeny on 2013-11-26
What do you get if you try to run the command** man update-initramfs**?

It should show you the manual and if it does not you must be missing the package **initramfs-tools** from your system, so install that and try again.

---

