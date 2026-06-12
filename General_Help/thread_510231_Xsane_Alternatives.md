---
title: "Xsane Alternatives?"
date: 2007-07-26
forum: General Help
---

### Post by LinuxBob on 2007-07-26
Can anyone recommend an alternative scanning software to Xsane?  XSane dientifies my interntal T tuner card as the scanning device, which it obviously is not.  I have a networked HP 6610 All in one scanner (its own IP address).  Posted my problem with no resposne so now seek soem other software option.

I used another product with Linspire that worked without issues but cannot recall the name.

---

### Post by gobbles414 on 2007-08-13
Hey LinuxBob,

It has been my experience that whatever behavior Xsane is doing will be duplicated by every other scanning program in the system. I think that is because they all use sane as a backend? Anyway, When installing a couple of scanners recently, I came upon two different methods for fixing scanning problems:

(1) Launch your scanning program as root. Oftentimes, this will force the scanner to be recognized. The downside is that any scans you save will need to have the permissions changed from root to normal access. Also, Xsane will give you a message saying that it is unsafe to run as root. Unless your scanner is on a network, I think that you can ignore the message.

(2) This is more difficult to setup, but less of a pain to use once it's ready. Depending upon your setup, there are anywhere between one and three files that you need to edit slightly with a text editor as root in order to tell the system that your scanner exists. To help with that, run sane-find-scanner in terminal. To make sure that Ubuntu is identifying your scanner and not your TV card, you can check the code number that sane-find-scanner gives you against other HP scanners in the appropriate text files. One of the two sets of numbers should match exactly. I know that this doesn't make much sense now. But it will as you get deeper into this method. I'm sorry that I can't identify which file(s) you need to edit. Each brand seems to have its own file(s). I bet that an answer has already been posted in the forums. 

To answer your question, I recommend [gscan2pdf]("http://gscan2pdf.sourceforge.net") for most scanning needs.

---

### Post by gobbles414 on 2007-08-13
You might also want to look at the [Sane Documentation]("http://www.sane-project.org/docs.html").

---

### Post by gobbles414 on 2007-08-14
LinuxBob,

Just in case you missed it, david_2001 provided the following details in [another thread]("http://ubuntuforums.org/showthread.php?t=519730"):

*To stop sane confusing a TV tuner for a scanning device edit /etc/sane.d/dll.conf and comment out "v4l" (it should be the last line)... Not that I have any experience with networked scanners but does a "man sane-net" help?* I'd like to add to David's comments, that you probably will need to edit dll.conf using sudo.

---

### Post by dabl on 2007-08-14
My xsane recognizes BOTH my Hauppauge PVR-150 and my Epson Perfection scanner, but it always defaults to the PVR-150 and I always have to change it back.  But in Kubuntu (on the same hardware platform), the kooka package only recognizes the Epson scanner (a good thing).  I dunno -- maybe I'll try the edit of /etc/sane.d/dll.conf.

---

