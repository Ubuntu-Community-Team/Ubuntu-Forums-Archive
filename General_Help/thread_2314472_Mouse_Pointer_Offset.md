---
title: "Mouse Pointer Offset"
date: 2016-02-21
forum: General Help
---

### Post by careycj0219 on 2016-02-21
Sometime within the last 6 months or so, my system seems to have developed a misalignment between the actual mouse pointer location and what is shown on screen.  I've searched around and tried the below, but so far no luck.  I have a TV connected to this machine, but my primary means of accessing it is via ssh and vnc.

I have plugged in a mouse and confirmed that the offset exists on the TV screen as well, so it does not appear to be a VNC issue.

Failed attempts to fix the problem:
[LIST=1]
[*][http://askubuntu.com/questions/469341/ubuntu-14-04-mouse-pointing-problem](http://askubuntu.com/questions/469341/ubuntu-14-04-mouse-pointing-problem)
[*]sudo nvidia-xconfig
[*]sudo dpkg-reconfigure --force vino
[/LIST]


Thanks in advance for any help.

Ubuntu 14.04.4 LTS

---

### Post by careycj0219 on 2016-02-28
Any thoughts on whether reinstalling the desktop environment might fix the issue?

---

### Post by v3.xx on 2016-02-28
Could it be ..

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1306550](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1306550)

There are a couple of work-a-rounds at the bottom.

> Any thoughts on whether reinstalling the desktop environment might fix the issue? 

You could install an alternate desktop for testing.  A simple one is the "Flashback" desktop, it won't bring in a lot of crap.  That's assuming you run Unity.

---

### Post by careycj0219 on 2016-03-07
Finally bit the bullet and reinstalled lightdm and gdm, which fixed the problem.

sudo apt-get remove --purge lightdm gdm
sudo apt-get install lightdm gdm

Hope this helps someone else...

---

