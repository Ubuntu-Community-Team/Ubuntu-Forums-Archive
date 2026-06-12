---
title: "[SOLVED] Random lockups"
date: 2007-11-16
forum: General Help
---

### Post by samurailink3 on 2007-11-16
I've been having random lockups, and I want to see whats causing the problem. Where can I look? What can I do? It seems to only occur when I'm running compiz fusion, sadly enough... Using metacity, I haven't had a problem yet. Maybe the graphics card is causing overheating? I'm not sure. The lockups are pretty severe. Its not a normal compiz lockup where the screen sticks and I have to kill compiz through a terminal, the entire machine locks, freezes (including the cursor), then either reboots or shuts off. No shutdown process that I can see, just lock, then dead. Anyway, any help on the matter would be much appreciated. Thanks!!

---

### Post by bobbybobington on 2007-11-16
I have the same prob. It happened for the first time yesterday and then again today. I'm guessing it may be from a new update?

---

### Post by samurailink3 on 2007-11-16
I've been getting it ever since the gutsy upgrade... maybe something in the gibbon?

---

### Post by bobbybobington on 2007-11-16
what computer do you have? I have the inspiron E1505
when was that last gutsy update?

Edit: I just noticed this is my 300th post. Tonight we dine in ubuntu!

---

### Post by samurailink3 on 2007-11-16
No way! Same here! Dell E1505!! I think the last big update was about 2 weeks ago... but I'm not entirely sure on that...

---

### Post by samurailink3 on 2007-11-16
Hah! Yes we do dine in Ubuntu! Maybe it has something to do with the nVidia 7300 Go and Compiz Fusion... When I play games though wine or just normally (UT04), I don't encounter problems, its only when compiz is running....

---

### Post by bobbybobington on 2007-11-16
well it's definitely hardware related...  I'll try and see if any bugs have been submitted yet.

---

### Post by bobbybobington on 2007-11-16
iirc there was a compiz update a while back. Maybe it broke something

---

### Post by samurailink3 on 2007-11-16
Ok, cool. I'm glad its not just me...
*edit*
That could have done it. It would make sense.

---

### Post by bobbybobington on 2007-11-16
Hmmm... i couldn't find anything on launchpad, but I'm sure this bug will show up on it relatively soon. I also looked through my log files to see look for something, but I don't know the time the lock ups occurred so i really couldn't find anything. Next time though I'll make note of the time and check the logs.

---

### Post by samurailink3 on 2007-11-16
I will do the same, and update here when I get the time. Any idea what I would be looking for?

---

### Post by FuturePilot on 2007-11-16
What are the specs of your computer?

---

### Post by Namakemono456 on 2007-11-16
You guys are having too much fun alone :P
Post your hardware plz.

---

### Post by samurailink3 on 2007-11-16
2GB Ram
Intel Centrino Duo 2.4Ghz
DVD+-RW
nVidia 7300 Go
160GB HD

Its the Dell Inspiron E1505

---

### Post by bobbybobington on 2007-11-17
1 gig ram
120 gig HD
intel core2duo T5600 (1.83 Ghz)
GeForce Go 7300

---

### Post by FuturePilot on 2007-11-17
Yep, there seems to be a bug in the latest Nvidia driver that propagates itself on machines with dual core CPUs and GeForce 7xxx cards. I'm not sure if the Beta 100.14.23 fixes this (I've heard mixed reports) but I do know for sure that if you install the 100.14.09 it should stop the freezing. The bug was introduced in the 100.14.11 driver.

---

### Post by samurailink3 on 2007-11-17
Cool! Will install this then report back after a day or so to post the results.

---

### Post by samurailink3 on 2007-11-18
Ok! The other driver fixes the lockup issue. Hopefully nVidia gets around to fixing this soon.

---

### Post by Paul S on 2007-11-20
> **FuturePilot said:**
> Yep, there seems to be a bug in the latest Nvidia driver that propagates itself on machines with dual core CPUs and GeForce 7xxx cards. I'm not sure if the Beta 100.14.23 fixes this (I've heard mixed reports) but I do know for sure that if you install the 100.14.09 it should stop the freezing. The bug was introduced in the 100.14.11 driver.

100.14.23 did not work here, I had to go back to 09.  The recently released 169.04 fixes it, so that's what I'm using now.  But, it added a corruption bug, so now I had to add 
```

        Option  "UseCompositeWrapper"   "True"
```

to the screen section of /etc/X11/xorg.conf.

  However, I'm also having resume problems since upgrading to gutsy.  It'll work once or twice then reboots rather than resume.  If I shut off compiz, it'll suspend / resume perfectly.  But, I'd rather use compiz.  I've been experimenting and seem to have success if I use Alt-F2 to run the command "sudo pmi action suspend" instead of hitting the suspend button.

E1505
Core2Duo T5500
Nvidia GeForce 7300 Go

---

