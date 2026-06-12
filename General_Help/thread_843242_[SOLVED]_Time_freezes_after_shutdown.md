---
title: "[SOLVED] Time freezes after shutdown"
date: 2008-06-28
forum: General Help
---

### Post by Umang on 2008-06-28
Hi!
My internet connection was down for a few days, and that helped me notice something very awkward with the time on my computer.

I realized that if I shutdown the computer at 9:30 PM yesterday and switched it on this morning, it would still show 9:30 PM yesterday. I figured that this was due to the fact that it wasn't able to connect to the internet and synchronize the time. 

BUT, I have set my time configuration to Manual, not synchronized with any internet server. I did have it synchronize sometime back, but I shifted to Manual at least a month ago.

Just to verify it hasn't been fixed, I upgraded my computer completely (I'm on Hardy) yesterday, shut down my computer this morning at 10:55, and disconnected the modem while switching on the computer at 2:00 PM today. When the login screen came, I got the time as 10:55 AM.

There are two problems now: 
1. Why doesn't Ubuntu use the system clock while the computer is switched off?
2. Why does it synchronize with the internet even when I'm on Manual mode?

What should I do? Anything I should check? How?

Thanks a lot in advance!

Umang

---

### Post by lisati on 2008-06-28
When your computer is switched off, the time is usually kept ticking over by a battery-powered system, which normally operates independently of the OS.

There might be a problem with your machine's BIOS settings or its CMOS battery, but I'm not sure exactly how to check the latter.

---

### Post by Umang on 2008-06-28
I haven't really done anything to the BIOS settings, and I don't remember this happening eariler.

How and what should I check in the BIOS settings?

---

### Post by Gunman1982 on 2008-06-28
If I recall right then the cmos battery is not only responsible for powering the clock in your system but for saving the bios preferences too (at least the ones changed and not default). But a failing cmos battery resetted the clock to 12:00 am, 1.1.1970 at least it did that in the days I bothered checking (10 years ago?).

But its still the first place to check imo. So check if you change something in bios (boot order of boot devices) then turn off the computer, maybe leave it off for 5-10 minutes, boot up again and check if those changes still active in the bios. If not then your CMOS battery is probably empty.

---

### Post by prshah on 2008-06-28
As suggested by the others, a failing CMOS battery is definately the first thing you should check. Some BIOS display backup battery voltage (it should be between 2.4~3.2v if it's good; 3.0v is ideal). If not you will have to open up the case, take out the battery (like a small silver colored coin, about 25mm in dia, usually model # CR2032) and check with a digital multimeter. Note that removing the battery will reset all cmos settings to defaults. Or you can just replace the battery without bothering to check it, and see if the problem recurs.

Sometimes this problem can be because a bios "refresh" is not performed when required, eg. after updating the BIOS. To "refresh" the BIOS, go to CMOS setup (typically Del or F2 during startup) and then choose option equivalent to "Load BIOS defaults". Note that here again, all the settings will be reset, so it's good if you have someone who knows about bios settings with you to change any required settings.

If none of these are the problem, then it's likely you have a failing motherboard.

---

### Post by Umang on 2008-06-28
Here's what I did:
Changed the BIOS setting of first boot device from Floppy to USB-CDROM (I have no clue what USB-CDROM is, but I know there's no harm, since I'm going to set it back to Floppy before anything can boot after 10 mins).

Switched off the computer, including power supply.

Waited 10 full minutes. Switched on the computer, checked the first boot ... setting, it was still USB-CDROM. Changed it back to Floppy.

I also did one more thing, in the CMOS settings I could check the system clock. I remember it being 9:something before switching the computer off. When I rebooted, it was 10:01. I think it did change by 10 minutes, though I can't be 100% sure since I didn't look at the clock too seriously before switching the computer off.

So there's no problem with the BIOS as far as I've understood, but I don't know about BIOS settings, so I'm not sure. Also, I know no one who I can get to look at the computer for a few weeks who'll know about BIOS. So I'm scared to reset. But from my understanding, the problem is in Ubuntu.

Any ideas?

---

### Post by Gunman1982 on 2008-06-28
Do you power down the computer by clicking on shutdown or on suspend?

---

### Post by Umang on 2008-06-28
> **Gunman1982 said:**
> Do you power down the computer by clicking on shutdown or on suspend?
Shut down. I don't have a Suspend button, for reasons I just don't know!

---

### Post by Gunman1982 on 2008-06-28
Probably because you have a Desktop PC and not a Laptop.

Mhh can you execute the commands 'sudo hwclock' and 'date' in a console and show what they say?

---

### Post by Umang on 2008-06-28
```
umang@ubuntu-desktop:~$ sudo hwclock
[sudo] password for umang: 
Saturday 28 June 2008 04:54:31 PM IST  -0.761986 seconds
umang@ubuntu-desktop:~$ date
Sat Jun 28 17:05:20 IST 2008
```

And if it helps,
/etc/default/rcS:
```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no
```

Yes, I'm on a desktop.

---

### Post by Umang on 2008-06-29
So, I checked the CMOS clock before booting when I switched on the computer today and it was the time I had shut it down yesterday.

I moved to Ubuntu only in April, (and still dual boot with WinXP), but on Windows I never had the clock synchronize. It used to work fine. The time would go off by five to ten minutes over a period of time, but it never used to freeze like this. This is only a recent problem.

I don't want to reset BIOS/CMOS settings or take any hardware out myself. Any other thing I can do to check what the problem is? I can change one paticular setting or check it if that helps, but I'm scared of reseting it.

Thanks,

Umang

---

### Post by Umang on 2008-07-04
OK. Just a quick question. Obviously my system clock stops after I shutdown.
Is this a bigger problem than just the time? I mean, is something else failing also?
Any other method of figuring what's wrong, without reseting BIOS or opening up my CPU?

Thanks!

---

### Post by Umang on 2008-10-05
Old thread, but might be worth sharing that replacing the CMOS battery fixed the problem. I finally decided to take action when all the COMS/BIOS settings were being reset every time I booted and I couldn't boot without getting a CMOS checksum error. The time would not only stall, but it would reset to 1/1/2000.

Thanks everyone!

Umang
> **Umang said:**
> 
Is this a bigger problem than just the time? I mean, is something else failing also?

---

