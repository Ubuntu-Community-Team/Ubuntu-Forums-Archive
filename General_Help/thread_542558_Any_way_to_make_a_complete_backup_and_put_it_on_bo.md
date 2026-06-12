---
title: "Any way to make a complete backup and put it on bootable dvd?"
date: 2007-09-04
forum: General Help
---

### Post by thegreenblob on 2007-09-04
Like the topic says...

I reinstall a lot cause I always get my system filled with clutter and stuff I don't need and it's just easy to reinstall to get rid of it. :lolflag:

But, every time I do I gotta install the programs I do use, and my vid card, and wireless card.

So... right now I have my system exactly how I want it. Is there any way to backup my entire system as it is right now and put it on a bootable dvd(s) and make it install from it? Or anything similar? Thanks for any help.

---

### Post by posterboy on 2007-09-04
I have used mondoarchive for years, very happy with it. Quickly, note that my experience with it has been on FC6. I learned that, unlike FC6, it's in the repos, just apt-get install mondo. I HOPE it works as well here as it did there. It will do a bare metal install, or just go get one file, as you need.

---

### Post by thegreenblob on 2007-09-04
Ah. Thanks.

This seems to do what I want it. Made a backup dvd of my system. :D

I'm actually surprised it all fit on 1 dvd though. lol.

---

### Post by chrome307 on 2007-09-04
Will the backup include all your drivers as well?

Also does the program having a GUI or is it just command line?

I also wanted to back this up to a DVDR - space permitting.

---

### Post by thegreenblob on 2007-09-04
Can't answer most of those questions cause I haven't tried to install from it yet. Though probly will later for the hell of it. lol.

But here's a screenshot of it. Runs in the terminal but looks like a GUI. lol.

[[IMG]http://img122.imageshack.us/img122/2772/screenshotjoeubuntujx0.th.png[/IMG]](http://img122.imageshack.us/my.php?image=screenshotjoeubuntujx0.png)

---

### Post by chrome307 on 2007-09-04
Excellent - thanks for the screenshot :)

I think I'll try it myself just to have a copy lying around ' fingers crossed' I won't need to use it :)

I've just used AptOnCD to backup all the Repository entries and additional DEB packages on my PC - fits nicely on a CDRW.

I seem to get an error message and the application fails to run for me :(

[IMG]http://i12.tinypic.com/4toyfqw.jpg[/IMG]

---

### Post by posterboy on 2007-09-05
GreenBlob: Yes, I did a full backup using mondo yesterday, also. I have not yet rebooted, and tried to start up using the DVD, have you? Did it crank up? Does it offer interactive? etc. etc. 
Thanks

---

### Post by thegreenblob on 2007-09-06
> **posterboy said:**
> GreenBlob: Yes, I did a full backup using mondo yesterday, also. I have not yet rebooted, and tried to start up using the DVD, have you? Did it crank up? Does it offer interactive? etc. etc. 
Thanks

Yeah. I booted up with the dvd. There's an option to format and install from the dvd, and to compare the dvd with your current system. I haven't installed using it yet though.

---

### Post by posterboy on 2007-09-06
GreenBlob: Yup, curiosity got the best of me, I booted from the DVD and restored one file I didn't care about. Worked perfectly. I sincerely hope I never need that "nuke" feature, but I did once on FC6, and it bare metal restored my hard drive. Pristine restore.

---

### Post by bean77 on 2007-09-19
I just used mondo and I got this error after burning was complete:

**Boot+data floppy creation failed.  However, FYI, you may burn /root/images/mindi/mondorescue.iso to a CD and boot from that instead if you wish.**

What did I do wrong?

---

### Post by posterboy on 2007-09-19
Nothing. Today, kernels simply won't fit on boot floppies, unless you have some kind of opto-mag drive. Not a problem. What you are interested in is that the CD or DVD will boot. Safe to ignore those messages.

---

### Post by bean77 on 2007-09-19
Ok great!  So if (God forbid) my computer exploded tomorrow, I could just insert this disk into a new machine and have everything exactly as it was?

---

### Post by posterboy on 2007-09-19
The answer to that is, well, maybe. I have done this, a bare metal install, (on FC6), however, I have also encountered issues when the hard drive sizes were wildly different. Solved that by doing a fresh install, then using "interactive" to restore everything I had.

---

### Post by bean77 on 2007-09-19
Thanks for the tip.  I am still very new to Ubuntu and I literally could make this into a full time job, learning everything there is!

---

### Post by posterboy on 2007-09-19
I'm suspicious that I may have already done that. I'm 71 years old, retired, and I would be ashamed to admit the number of hours I spend tweaking, googling for help, trying this and that. The learning experience has just been so absorbing.

---

### Post by bean77 on 2007-09-19
LOL-me too...I have invested so much into this machine it's ridiculous.  My babies are starving and dirty!

(OK, not really)

---

### Post by posterboy on 2007-09-19
Lol!

---

