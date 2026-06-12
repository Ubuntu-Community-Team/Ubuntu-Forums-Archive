---
title: "Freezes After Suspend"
date: 2013-05-10
forum: General Help
---

### Post by Onesimus on 2013-05-10
I have done a clean install of 13.04 (64 bit) on my Samsung R530 Laptop.  Everything is working fine except for Resuming from Suspend.  It resumes but after approx. 1-2 minutes the whole computer locks up.  No keyboard and no mouse.  The only option is a hard reset.  This freeze happens approx. 50% of the time.

Does anybody know how to resolve this ?  Is it a known issue ?

---

### Post by 2F4U on 2013-05-10
Did you look into the system log file if there are any errors recorded? What is your hardware configuration? What graphics card and driver do you use?

---

### Post by Onesimus on 2013-05-10
My Hardware details are:
   Processor: Intel Core 2 Duo CPU T6600 @ 2.20Ghz x 2
   Graphics: Mobile Intel GM45 Express Chipset
   RAM 3GB

Dual Monitor Setup

Not sure how to provide further information.

---

### Post by Onesimus on 2013-05-10
It has just produced a Crash Report, but not sure how to get all the details from the window to my browser.
One line has
PulseList
   Error: command ['pacmd', 'list'] failed with exit code 1; No PulseAudio daemon running, or not running as session daemon

Linux Kernel is: 3.8.0-19-generic x86_64

---

### Post by Onesimus on 2013-05-12
bump

---

### Post by esoh on 2013-05-13
Hi,

I have exactly the same issue.
After resuming from suspend, the laptop runs normal and after a few seconds it freezes completely. The screen does not change anymore and no more input is possible. This happens every time, my standby time takes longer than about 30 mins. After a shorter standby time, the system resumes normaly.
Looking into the syslog, the two lines before freeze are:

AptDaemon: INFO: Quitting due to inactivity
AptDaemon: INFO: Quitting was requested

But I don't know if this is really the root cause. 

My Laptop is an ASUS K70IJ with Intel graphics.

Hopefully anyone can help because this is really annoying.

Regards, Stephan

---

### Post by Onesimus on 2013-05-14
I have now installed Ubuntu 13.04 (32bit) hoping that it might resolve the problem.  It seemed to be running much quicker, more responsive, the cursor didn't stutter as previous.  Suspend and Resume seemed OK.  However, when the laptop resumed today, it froze almost instantly.

I have a feeling that it might have something to do with the wireless, but it's only a guess.

I got the same crash report indicating that the PulseAudio daemon wasn't running.

Regards

---

### Post by Onesimus on 2013-05-16
Anyone got any ideas how to resolve this, or for me to interrogate my machine to get a better idea what's causing this issue ?

---

### Post by Onesimus on 2013-05-20
Anybody ?

---

### Post by mimasterix on 2013-06-07
I have the same problem on a Thinkpad x200s that only started after I upgraded to 13.04 from 12.10.  It does not happen every time I resume from suspend, but it seems to happen almost exclusively when I am on my work WiFi (at a university), which uses WPA2 PEAP with MSCHAPv2 inner authentication.  I don't think that it has happened when I'm on my home network using regular WPA authentication.  Using the wifi kill switch to turn off the wifi before resuming does not always prevent it from freezing, though.  Using the kill switch before suspending might help more, although I haven't tested it enough.  

One way that I have found to prevent it from freezing is to wait for a couple of minutes after I have resumed from suspend before entering my password to unlock it.

---

### Post by Onesimus on 2013-06-07
I give your suggestion of waiting a couple of minutes before entering my password a try, and let you know.

But many thanks for replying to my thread - I had given up all hope of a response (!)

---

### Post by mimasterix on 2013-06-07
Sure.  I hope that we can get to the bottom of this so it can actually be fixed and we don't need a workaround like this.

---

