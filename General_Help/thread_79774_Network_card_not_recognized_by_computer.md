---
title: "Network card not recognized by computer"
date: 2005-10-20
forum: General Help
---

### Post by Flame0001 on 2005-10-20
I've gone through as many tutorials and walk-throughs and forum posts as I can in order to get my network card (WMP11 v2.7) to work. I've gotten the bcmwl5 driver to install, it's just that when I do 'ndiswrapper -l' it says that it's installed, but nothing about hardware.

One thing I noticed while going through the device manager was that it's listed underneath my Sony DVD Burner...

I've taken out the card, booted the computer, turned it off, put it back in, rebooted, but to no avail.

Just as a note, I'm completely new to Linux as a whole (although not computer illiterate), so try not to assume I know much at all about Linux... the ndiswrapper installation wiki did that >_<

Thanks in advance,
Zach

---

### Post by mlomker on 2005-10-20
[This is]("http://ubuntuforums.org/showthread.php?t=25683") probably the best Broadcom thread.

---

### Post by Flame0001 on 2005-10-20
Probably tried going through that walkthrough about 5-7 times, each starting from Step 0.

Any other suggestions?

---

### Post by mlomker on 2005-10-20
Try a different driver...some work and others don't.  Broadcom is odd because they don't write the drivers for their own cards--each company that uses their chips writes their own.  I went out of my way to avoid Broadcom on my new laptop and get an adapter with a native driver.

Could try contacting the last poster in [this thread]("http://www.ubuntuforums.org/showthread.php?t=41081").

---

