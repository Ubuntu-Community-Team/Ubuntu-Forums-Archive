---
title: "Nautilus will no longer load"
date: 2015-05-31
forum: General Help
---

### Post by RebelwithoutaClue on 2015-05-31
14.04 with all packages updated until it broke.

When I boot I get the login, I enter my password and the sound (manually returned) plays.

Then nothing. Sometimes a mouse pointer, sometimes not.

Previously I had a black desktop with docky and the side and top menus.

I've tried repairing all packages from the grub menu to no effect.
Pretty much all the options have been tried to the same end.

If I try low graphics mode I get no mouse and cannot get past the warning because I cannot affect the OK button.

I have ab Nvidia card that has never caused any issues previously.
I have a bluetooth USB transceiver connected which Ubuntu took to better than my Windows install.

When I do the safe boot thing, forgive the terminology, I'm doing it from memory I notice something like...

Buffer I/O Error Sector sr0, 714
and them
Buffer I/O Error Sector sr0, 592

The numbers may differ, as I say, it's from memory.

On the discourse site someone suggested it could be Plymouth, which means nothing to me.

---

### Post by dino99 on 2015-05-31
what are you testing with your cd/dvd ? (aka sr0)
how have you made that ubuntu installation ?
if you have an issue, then glance at your logs to find some usefull warnings/errors to dig around the problem (/var/log/dmesg and xorg.0.log)

---

### Post by RebelwithoutaClue on 2015-05-31
DVD /RW drive had a photo DVD in it.
CD/RW was empty.

The install was made when 14.04 was released from CD about a year ago.

How do I view my logs?

My Windows install cannot read my Ubuntu partition

---

### Post by dino99 on 2015-05-31
hope you talk about a real install, not a wubi one from windows (it's no more used nor maintained)
 
open a terminal, and run:

> sudo gedit /var/log/dmesg
sudo gedit xorg.0.log

---

