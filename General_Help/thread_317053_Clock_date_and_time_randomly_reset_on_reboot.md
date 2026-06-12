---
title: "Clock date and time randomly reset on reboot"
date: 2006-12-11
forum: General Help
---

### Post by pjstadig on 2006-12-11
Hi,
I have a very odd problem on my Dell XPS laptop.  Most often, when I reboot my date and time will be set to some random value.  It is rare that when I boot my laptop the date and time are accurate. Sometimes the date is a month ahead (i.e. it should be Dec. 11, but it's Jan. 7), but sometimes it is actually a couple of months behind.  There is no rhyme or reason to it.

I'll tell you what I'm pretty sure it is not:
[LIST=1]
[*]I do not have Windows installed, so this is not the UTC/localtime problem with dual booting
[*]I have the timezone set properly, and if I didn't my laptop would be consistently off by a couple of hours; it will be set to a different random time each time I boot, and not just off by hours, but by months.
[/LIST]

I do not have NTP installed.  I have a Core Duo processor (if that matters).  I suspect that perhaps it is related to the bootup process that tries to sync the clock.  I have a wireless connection and occasionally I do not have a hard wire plugged in, and perhaps it is not able to sync over the wireless (for lack of connection at boot).  Is there a way to just disable the bootup clock sync?  I don't see it in the Services Preference panel.  I'd prefer to just set my date/time in the BIOS and leave it alone, unless there is something else going on here.


Thanks,
Paul

---

### Post by macogw on 2006-12-12
If you don't have NTP installed, I don't see how it could be trying to sync with a server, so web connection's not the issue.

---

### Post by pjstadig on 2006-12-12
The way I understand it Ubuntu syncs once with NTP servers when you boot.  This feature is installed automatically regardless of whether you have the NTP package installed.  When you install the NTP package your system will sync with an NTP server periodically while it is running.


Paul

---

### Post by Scorpuk on 2006-12-12
Is the laptop old?

If it is it could be the cmos battery at fault.


Anywho to check the quickest way would be:

1. set time to current before shutting down.
2. reboot and go into the system bios to check the time.
3. let the computer reboot into ubuntu and check the time.


Any differences between 1 and 2 then its the bios at fualt / cmos battery.

Any difference between 2 and 3 then something fishy in ubuntu. :)

---

### Post by Cippa Lippa on 2007-09-21
I am having the same problem on ubuntu 7.04 with kde-core installed.
Every time I reboot my time is changed of between one and two hours, never more, but at random.

Does anybody have any idea why this might happpen?

Cippa

---

### Post by pjstadig on 2007-09-21
I have since fixed my problem.

When I booted into BIOS to check the system clock I saw the time advancing at a much faster rate than it should. It was ticking off a minute every second or so.

This indicated to me that it was a hardware issue. I called Dell, and they had me open up my laptop, remove the CMOS battery, and re-insert it. This fixed my issue. My laptop is newer, so I don't know what the problem was. It didn't seem to be a bad battery, because I didn't have to replace the battery. My laptop seemed to just be stuck in some "twilight zone" mode and needed to be reset.

It's been working normally ever since.

Paul

---

### Post by cakmin on 2007-09-21
I also have this problem and it has occurred twice every time I boot my computer since last night. Thank you for pointing out about the cmos problem. My laptop is a quite old one, Compaq Presario 700 made in 2001 if I remember correctly. Hopefully I can fix it.

---

### Post by Cippa Lippa on 2007-09-23
I am dual booting and the problem happens only with Linux, not with windows...

---

### Post by darren_07 on 2007-10-02
i have had this problem.. Im using a Dual boot (linux is on and external USB drive) when i load linux it is nearly always 2 hours or so behind.  
If i change the clock time in Linux when i boot back into windows the Time is realy really messed up.. It swaps AM to PM and is about 2 hours different..

When i change it back in windows it messes up linux... 

"Time is the death of us all"
:confused::confused::confused:

cheers
D

---

