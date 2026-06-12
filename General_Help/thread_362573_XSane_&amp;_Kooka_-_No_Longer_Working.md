---
title: "XSane &amp; Kooka - No Longer Working"
date: 2007-02-15
forum: General Help
---

### Post by myke on 2007-02-15
Hi.   I've used Edgy for a while with very little problems including with my scanner, a  Canon Lide60, which has worked perfectly in both dapper and edgy.  I've also used both main scanner programs, Xsane & Kooka, alternately and both have easily recognized and used my scanner.  However, after the last suggested auto upgrade through adept (which I think was only updating the Linux headers), neither program will launch at all.   My scanner is recognized but after launching either program, they detect the scanner and then crash.   I restarted my pc and booted it with the previous linux headers from grub but it didn't help.  

Is there anything else that an upgrade might have possibly done to keep Xsane or Kooka from launching?   It's not a problem with the scanner .... I've tried both with the scanner connected and unconnected ... and it is detected when connected ... neither program will launch at all.

Kooka comes up with KDE crash screen and Xsane simply stops loading and shuts down when trying to launch.   I've even tried reinstalling each and still neither will launch  at all.   I even found another program thru synaptic called "quiteinsane" and it won't launch either.   Could it be a problem with the sane libraries?    No broken dependancies are detected by either adept or synaptic so I don't know what else to do.

Any help or ideas?

---

### Post by myke on 2007-02-15
For some reason ... & I don't know why ... after the kernel upgrade, it apprantly affected a setting with my Samsung printer which in turn affected the scanner software even though the printer never stopped working.   After poking around the forums a while, I found this thread:

[http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697]("http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697")

I used the chmod solution and commenting out one line in a root file and now both kooka & xsane are working again.

Specifically, this is what was suggested and what fixed my problem & hey ... I don't know what the kernel upgrade had to do with it but I'm just glad the solution turned out to be relatively simple:

you'll find xsane now executes as root. (This is also true if you have a multifunction printer, but see below instead of this step.) To fix this, since you don't want to run xsane as root, do the following:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

---

