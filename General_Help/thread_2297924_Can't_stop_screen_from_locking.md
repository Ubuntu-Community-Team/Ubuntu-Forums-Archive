---
title: "Can't stop screen from locking"
date: 2015-10-07
forum: General Help
---

### Post by richlion2 on 2015-10-07
Hi, 

a bit of a nuisance, I've installed Kubuntu 15.04 on my laptop and could not get any way to stop the screen from locking. 
I installed this version on a PC and the same problem, I checked various thread, some of them are pretty old. I also can see
some sort of a bug description, but related to an old problem:
[https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1287255](https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1287255)

So actually what can I do? I change all my settings to disabled and nothing. I also tried this command in the terminal:
 sudo xset s 0 0
and nothing. I attached a screen with my settings in the Power Management. 

Any suggestions?

Regards, 
Ryszard

---

### Post by TheFu on 2015-10-07
No clue, but check the clock is correct in NTP, system and CMOS. Just a guess.

---

### Post by richlion2 on 2015-10-08
Am I the only person with such a problem?

---

### Post by richlion2 on 2015-10-08
> **TheFu said:**
> No clue, but check the clock is correct in NTP, system and CMOS. Just a guess.

What's NTP?
System, what exactly?
CMOS - since my previous Kubuntu version which was 14 was working, then I don't suspect that is the culprit. 

Can't find any hints when searching for KDE Power Management problems. Very irritating, I can't go to make tea in the kitchen, screen locks, then goes off. It also has nothing to do with settings on my LCD screen, as I had all sleeps disabled for ages.

---

### Post by TheFu on 2015-10-09
Those are places where the clock is set and maintained, hence my "check the clock is correct" statement. If they do not agree, the clock can change and trigger the "time to lock this screen" event. It was just a guess.

Where?
/etc/ntp.conf
`date`
the CMOS clock.

---

### Post by richlion2 on 2015-10-10
This helped solve the problem:
kcmshell5 screenlocker

---

