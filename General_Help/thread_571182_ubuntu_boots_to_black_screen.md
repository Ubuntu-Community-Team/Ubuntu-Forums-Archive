---
title: "ubuntu boots to black screen"
date: 2007-10-09
forum: General Help
---

### Post by amadeus266 on 2007-10-09
I've been running Feisty since its release and recently I have not been able to reboot my machine due to never getting to the login screen. If I restart the machine a number of times it will work and work well (even Compiz-Fusion runs smoothly) but this is really getting on my nerves. I have tried reconfiguring xorg.conf and even booting to the install cd and copying the xorg.conf to my usb stick and then rebooting into rescue mode and copying the xorg.conf to the hard drive and rebooting with the same problem.

specs:
amd athlon 64
ATI AIW 9200
528 MB ram
WD 40G IDE HDD

---

### Post by nikhilk on 2007-10-09
Maybe your home partition is full. Check using
```
df /home
```

---

### Post by dcstar on 2007-10-09
> **nikhilk said:**
> Maybe your home partition is full. Check using
```
df /home
```

Or the root partition........

---

### Post by amadeus266 on 2007-10-09
Plenty of room...
```
adam@adam-desktop:~$ df /
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             37911148   5004168  30981192  14% /
adam@adam-desktop:~$ df /home
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             37911148   5004168  30981192  14% /
adam@adam-desktop:~$ 


```

This has been going on for about 3 weeks. I don't recall it starting immediately following any updates though.

BTW this is Feisty 32bit using default aTI drivers. !!!Now my shift-a doesn't work (I can't type capital a)!!!

Edit: Fixed my Shift-A problem - bad setting in ccsm.

---

### Post by dabl on 2007-10-09
> **amadeus266 said:**
> 
 If I restart the machine a number of times it will work



That sounds more like a hardware issue than operating system -- hard drive or thermal-related, maybe.  Sometimes hard drives can degrade in a way that causes them, when cold, to spin up too slow for the BIOS to "catch" -- if you can push the "warm reset" button and then it boots correctly, I would start getting suspicious of the hard drive. Or else maybe there's some component that no longer likes to work when it's cold?  :cry:

---

### Post by amadeus266 on 2007-10-09
> **dabl said:**
> That sounds more like a hardware issue than operating system -- hard drive or thermal-related, maybe.  Sometimes hard drives can degrade in a way that causes them, when cold, to spin up too slow for the BIOS to "catch" -- if you can push the "warm reset" button and then it boots correctly, I would start getting suspicious of the hard drive. Or else maybe there's some component that no longer likes to work when it's cold?  :cry:

I wish it were that simple but this happens warm or cold. This machine is only 2 years old, the video card is closer to 4. The bios starts fine, then I see the boot screen, animations and all, then black screen. I have checked for overheating problems as well but even after running CF with all the bells and whisltes plus Open Arena for over an hour, my video card is barely warm to the touch and all fans are running properly. Processor temp never goes over 102F and case never goes above 106F. When I get home from work today, I am going to disassemble it and check all connections and clean it up. Maybe that will help.

---

### Post by nikhilk on 2007-10-09
Did you take a look at /var/log/message? You might find a clue in there.

---

### Post by amadeus266 on 2007-10-09
Nothing related in there only references to my dvd drive which has had issues for months before this problem started. (Can't boot from a dvd but can boot from a cd)

---

