---
title: "This might be a dumb question but...."
date: 2008-03-10
forum: General Help
---

### Post by Whiffenpoof on 2008-03-10
I have Wubi installed with XP Pro, I select Ubuntu on boot, enter my name and password and a command line comes up. What do I do next? What do I enter into the command line to access the GUI/desktop?
How can I get into Ubuntu? Any answers?

---

### Post by ago on 2008-03-10
Might be that X is failing (i.e. the video driver is not correct)

Try to login and run:

sudo dpkg-reconfigure xserver-xorg

select the Vesa driver and leave the other settings. Then reboot. That should bring you to a graphical environment (even though one with limited resolution), from there you can try to install new drivers and what not.

Also, if you aren't doing that already, you may want to try 8.04. Usually new versions have better hardware support.

---

