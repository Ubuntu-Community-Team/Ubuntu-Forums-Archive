---
title: "Ubuntu 6.06 freezing using X, but not command line."
date: 2006-11-04
forum: General Help
---

### Post by Cable on 2006-11-04
I installed Ubuntu on a friend's computer today.  It has a bit of mixed hardware, as it was put together from a few parts laying around.  It's a P4 1.8 GHz with a Radeon 7200.  It installed fine.  However, when starting Ubuntu, the login screen shows and you log in.  Then it *starts* loading the desktop...and doesn't finish.  It'll either do one of two things:

1)  It will load the top and bottom panels (no applets, just the panels themselves) and **maybe** the background, then nothing else...but the mouse can still be moved.

or

2)  It will do as above, but it will also hard lock (no ctrl+alt+backspace or anything else will fix it)

I can boot it into recovery mode and use the command line just fine, so I believe it's a graphical problem.  I know the fglrx drivers won't work with the video card as it's too old.  I tried changing the "ati" line in xorg.conf to "vesa" (I'm pretty sure that's right) and it did the same thing.  I'm stumped.  Any ideas?

---

### Post by amohanty on 2006-11-04
Can you post the contents of /var/log/Xorg.0.log

AM

---

### Post by Cable on 2006-11-04
I will when I get the chance, but the computer is a friend's and I'm not at his house at the moment.  Next time I'm there I'll try to do that.

---

### Post by amohanty on 2006-11-04
You could also try a 
sudo dpkg-reconfigure xserver-xorg 
default through everything and see if that works.

AM

---

### Post by Cable on 2006-11-06
We just tried installing a different video card and reconfiguring X and it did the same thing. I can't embed the file in this post or attach it because it's both too long and too large.  I can email it though, so pm me your email address and I'll email you the log file.

---

### Post by amohanty on 2006-11-06
To shorten it, delete it as sudo and then restart X to oly have logs that matter for one startup, then post back. If its still too large, I can send you my email address.

Not that I am paranoid or anything, just that if I am unable to help you, the log will come in handy to somebody else who can.

AM

---

