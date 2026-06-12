---
title: "I have a machine that has stopped working."
date: 2024-10-04
forum: General Help
---

### Post by jgw on 2024-10-04
I have a machine that stopped working.  It left this message:

```

/dev/sda2: contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
	(I.E., WITHOUT -A OR -P OPTIONS)
fsck exited with status code 4
The root firesystem on /dev/sda2 requires a manual fsck

BusyBox V1.30.1 (Ubuntu 1:1.30.1-7ubuntu3.1) built-in shell (ash)
Enter "help' for a list of built-in commands.

(initramfs) --
sh: --: not found
(initramfs) fcsk
sh fcsk: not found
(initramfs) exit
/deb/sda2 Contains a file system with errors, check forced.
Inodes that were part of a corrupted orphan linked list found.

/dev.sda2: UNEXPWECTED INCONSISTENCY: RUN fsck MANUALLY 
	(i.e., without -a or -p options)
fsck exited with status code 4
The root firesystem on /dev/sda2 requires a manual fsck
```

I cannot get to a terminal so that I can do the manual fsck that its asking for.  I have tried to re-boot and press f7 in the hope that will do something but it does nothing so I can't even try to do anything.  This is a 20.04 ubuntu system (I have put off upgrading it but, maybe, I should do that but maybe not now?

I found out that I can get to a menu of sorts:
continue startup 
system information
change language

diagnostics (f2)
boot menu (f9)
computer setup f(10)
network boot (f12)
Utilities
run UEFI Applications

I am not sure what each does or might do.

Anyway, any thoughts would be appreciated - thank you...............

---

### Post by yancek on 2024-10-04
Do you have an Ubuntu 'live' DVD or USB or any Linux that you can boot and run fsck on sda2?

---

### Post by jgw on 2024-10-05
What I can do is take the 1tb sdd out of this machine and put it in another and THEN run fsck on it.  I will make a run at that just to see what happens.   

The only thing I currently have is the 1tb sdd - nothing else, all drives have been removed.  I think I am going to just install 24.04.9 then update it all to 24.04.9  I would try and install 24.04.9 but its not available (24.04.10 is but its not ready (neither is 24.04.1 but there are no other choices)

---

### Post by jgw on 2024-10-05
I have tried, literally, just about everything that can be done and failed each step of the way.  I have now gone to another machine, put a blank ssd in it and am creating ubuntu on it and then putting that into that machine and see what happens.  Should come right up!  Then I can goto the other ssd and get whatever I can use and transfer it.

---

### Post by bobunderwood99 on 2024-10-05
Are you shutting down (power off) your computers before you remove/replace your SSDs?

---

### Post by jgw on 2024-10-06
First, I am in a learning thing here.  Second, I am also learning to read EVERYTHING that I should be doing.  For instance, to install ubuntu onto a system what one is supposed to do is to build the bootable stick.  Then put it into the machine to get the new ubuntu and then turn it on.  THEN after all of that its time to (in my case) plug in the ssd I am going to use to become the ubuntu for the system.  I have been fighting just getting that done and then read it all again and then figured out that I was plugging stuff in and nothing was happening.  Just ignored the plug it in, start the machine, and THEN plug in the ssd!  Between old age and dementia and lack of a brain life gets interesting. 

Anyway, I am going to call this done and open another one about installing ubuntu as I am getting some very strange things that make no sense.  This one was a whining about something that was, basically all my fault and I apologize for that and any time I may have used up.  But I do appreciate anybody who has responded and tried to help.

---

### Post by bobunderwood99 on 2024-10-06
Do **not** ever plug in (or remove) a SSD while the system is powered on. You run a very high risk of damaging the drive and/or the motherboard.

---

