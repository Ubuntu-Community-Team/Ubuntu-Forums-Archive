---
title: "Web browsers hard locking up the computer.  So bad that the kernel don't even panic."
date: 2013-08-02
forum: General Help
---

### Post by MechaMechanism on 2013-08-02
So how do I diagnose this.  Maybe X is locking up badly and thats why I get a frozen computer.  But I think the kernel locks up too because the hard drive activity light no longers show activity even after long strethces of time.  Also I can not SSH into the machine at all.  Keyboard lights flash quickly and key and mouse are unresponsive.  I have to power cycle the computer to bring it back online.  Sometimes while coming back online it locks up again right before the login screen. Sometimes I half to power cycle a few times to get a working computer.  Do a google image search or other web site with lots of pics and videos will lock up the machine, all other software the computer functions normally.  Only web browsing and pretty much with image loaded sites like youtube and google image search and probably flickr.  Ubuntu foums seems safe.  I use my own DNS, Bind and am wondering if bind is being made to crash the computer on certain sites.  But why the heck would browsers crash the computer.

Please help me as I can not use the internet on the desktop but only on my laptop.  My disk drives are all healthy according to disk utility.  Hardware clock shows as being very accurate and NTP shows no big jumps in time.  Have healthy battery backup.  Computer about 5 years old and in good hardware shape.

P.S.  When locking up the screen displays the screen frozen with no input accepted.  Like something is still putting video on the monitor but in no way does the keyboard or mouse or SSH work.

---

### Post by carl4926 on 2013-08-02
I'd probably run a memory check

---

### Post by akakingess on 2013-08-02
Sounds like a RAM issue at first glance...

E

---

### Post by CharlesA on 2013-08-02
Definitely sounds like a kernel panic. If this just started happening, it might be a good idea to test the hard drive for errors with the manufacture's utility to make sure it is in good shape.

+1 to memory check too.

---

### Post by MechaMechanism on 2013-08-04
Memory check successfully passed, I used the memtest86 in the grub menu.  Disk utility shows hd smart status as healthy for 2 disk with 3rd disk as having a few bad sectors (all disk in a raid setup).  Usually the problem only shows up when there is anything to do with the network such as web browsing, email or if the networks disconnects or goes offline then the computer freezes.  So maybe the network card or networking code might be triggering a faulty hardware or really bad bug.

I will try a live cd and see if I can't reproduce the problem and see if it's a hardware problem in the main board.  I will also replace that dying disk too as it's from about 2005, the other 2 disk are healthy and from 2009 or 2010.

What's strange is the networking hardware/software seems to trigger it.  I thank you all for your replies.  One of you mentioned kernel panic, is there anyway to log something this severe?

---

### Post by CharlesA on 2013-08-04
It should be in the syslog, depending on well the kernel panic occured. Otherwise, take a picture of the screen when it happens as it usually displays what happened.

---

### Post by MechaMechanism on 2013-08-07
> **CharlesA said:**
> It should be in the syslog, depending on well the kernel panic occured. Otherwise, take a picture of the screen when it happens as it usually displays what happened.

When the screen freezes it just look like a screen shot, there is no corruption in the screen.  One time during boot it locked up and displayed the output and said something about not syncing.  I replaced a dying disk and now with three healthy disk in a lvm array it still happened.  It only is triggered by networking, such as opening web browsers and thunderbird or it will freeze if the network goes offline, always triggered by anything to do with the network.

I'm curious about the syncing thing though and is there anyway to setup logging to log kernel panics to it's own log instead of syslog.

It may be that the lvm array has corruption and so I have backed up my machine and I am going to reinstall from scratch with the new hard drive in place.

Any suggestions appreciated.

---

### Post by CharlesA on 2013-08-07
I don't know of any way to log a kernel panic to its own log.

Hope the reinstall fixes the issue you are having.

---

### Post by MechaMechanism on 2013-08-07
> **CharlesA said:**
> I don't know of any way to log a kernel panic to its own log.

Hope the reinstall fixes the issue you are having.  Thank you.  I was using 12.04 and I have decied to install 13.04.  If the problem remains then I will have to have a repair shop check the hardware for failing components.

---

### Post by Thomas_Dejanovic on 2013-09-03
Hi all,

just like to add my 2c to this thread.  I'm having the same problem with my desktop machine at work.  

Upgraded to 12.04 and my machine freezes at least once a day.  Keyboard and mouse are unresponsive.  Audio out is looping over the last 0.5 seconds of music.  Cannot ssh into the machine or ping it.  No activity.

The only way to recover is power cycle the machine.  I've re-built the machine twoce.  New motherboard, new memory, new hard drives.  12.04 is the common denominator.  One of my co-workers also upgraded to 12.04 but he has an nvidia graphics card so we cannot rule out his problems being nvidia related.

looking for answers, any suggestions would be great otherwise I'm moving back to 10.04.

Regards, Thomas D.

---

### Post by erasmusp on 2013-09-03
Hi Thomas,

I had that exact symptom on one of my PCs, but a Windows 7 one. It turned out to be graphic driver related. It started happening quite often when I updated the NVidia driver to the latest. I managed to "fix" it by rolling back to an older driver... I know you are using Ubuntu but, as I said, my symptoms were exactly the same - sound repeating it self and PC frozen solid.

---

### Post by CharlesA on 2013-09-03
> **erasmusp said:**
> Hi Thomas,

I had that exact symptom on one of my PCs, but a Windows 7 one. It turned out to be graphic driver related. It started happening quite often when I updated the NVidia driver to the latest. I managed to "fix" it by rolling back to an older driver... I know you are using Ubuntu but, as I said, my symptoms were exactly the same - sound repeating it self and PC frozen solid.

Done that. I'm currently stuck at Nvidia driver 314.22 because the newer drivers cause constant hard locks.

---

