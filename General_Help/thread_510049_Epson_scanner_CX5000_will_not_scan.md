---
title: "Epson scanner CX5000 will not scan"
date: 2007-07-26
forum: General Help
---

### Post by Tucatts on 2007-07-26
I am using Feisty and the CX5000 drivers are there and the print function works fine. I had checked the driver Linux data base and this model is supposed to work. I have XSane Image scanner and Scanner utility installed and neither program will find or recognize that I have a scanner connected. If I can get the scanner to work I will be completely free from Windows! No more dual boot, ha ha. SO, has anyone had this experience and can offer some help?
Thanks,
Tucatts

---

### Post by yorkie on 2007-07-26
try this thread its for a cx6600 printer but the scanner part should be the same I used this advice and my printer/ scanner works ok
[http://ubuntuforums.org/showthread.php?t=38445](http://ubuntuforums.org/showthread.php?t=38445)

---

### Post by Tucatts on 2007-07-26
Yeah, that looks good, will give it a try. Many thanks!

---

### Post by carltonh on 2007-12-23
I have a CX5000 also.  Printing works fine, (but note that in non-Ubuntu distros, I had to choose the CX4800 driver in CUPS because 1. there was no CX5000 driver 2. the CX5100 didn't work. 3. the CX4800 driver did.) but I followed several different threads on making the scanner part work, trying both the "epson" and "epkowa" drivers.  None of the threads with directions worked per se for the CX5000, but they must have gotten me most of the way there.  Although at the end, typing "scanimage -L" made my scanner make a tiny noise for only a second, I decided to try "xsane" instead.

It worked!  I wish I could say which parts were the important parts to getting the scanner to work, but I don't know.  However, I do know that I commented out the "epson" driver in the (I think) /etc/sane.d/epson.conf file and used the epkowa driver in epkowa.conf.  Who knows, if I tried xsane earlier, it might have worked fine with the epson driver too.
---
Now that I thought to type "man scanimage" I see that the threads left me with the impression that "scanimage -L" would have copied the image.  So that was partly a newbie mistake.

---

