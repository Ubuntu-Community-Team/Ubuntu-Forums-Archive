---
title: "How do I recuperate my system 7.10 after a wrong screen declaration"
date: 2008-03-26
forum: General Help
---

### Post by ouwe_man on 2008-03-26
Hi,

I'm trying to help my brother in the netherlands with his Ubuntu system. He bought a Siemens display, capable of doing 1500 plus dpi. Without paying any attention to special drivers en what have you, he specified the resolution and hoped for the best....

He can not enter the options screen any more so what to do next and above all how to do it.

I have tried with Knoppix and a live ubuntu disk but my linux talents are very limited and I'm now waiting for an answer from a specialist on this forum

Thanks in advance

John

---

### Post by thedarkwinter on 2008-03-26
Hi.

I am assuming that the problem is that his graphics aren't working?

You can try run

sudo dpkg-reconfigure xserver-xorg

in a terminal, see if that can fix it.

Otherwise, manually edit /etc/X11/xorg.conf to change the resolution and/or driver

You can often change the driver to 'vesa' to go in with low graphics mode and change the settings.

hope that helps...

---

### Post by ouwe_man on 2008-03-26
Hi,

Indeed there are no graphics, not even the login screen so no options to get into a command screen. That's why I wanted to use Knoppix, rescue or ubuntu-live. I can see the xorg.conf file but I can not save it....

Any Idea?

John

---

### Post by strabes on 2008-03-26
Hit ctrl+alt+backspace to get to a terminal screen. Log in and then enter the command that thedarkwinter wrote.

---

### Post by cdenley on 2008-03-26
> **strabes said:**
> Hit ctrl+alt+backspace to get to a terminal screen. Log in and then enter the command that thedarkwinter wrote.

Or use ctrl+alt+f1 to switch to the terminal. If xserver is running, ctrl+alt+backspace will kill it then it will respawn. If xserver isn't running, I don't think ctrl+alt+backspace will do anything.

---

### Post by ouwe_man on 2008-03-26
Thank you all for your help but my brother is still not out of his problems....

It is difficult to do things by phone with 5 hours time difference and a non english speaking person. Things get misspelled and problems are created instead of repaired.

Tomorrow we<ll try again....

for now thanks to all of you

John

---

