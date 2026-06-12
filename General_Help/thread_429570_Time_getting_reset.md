---
title: "Time getting reset"
date: 2007-05-01
forum: General Help
---

### Post by manoj_paul_joseph on 2007-05-01
Hi,

I am on Ubuntu 6.06. My timezone is GMT+5:30.

My BIOS time matches the time on my timezone. Quite often, after a reboot, it gets reset to time -530.

I keep having to resynchronize with a time server. Is this a known issue? Does anybody have a clue?

manoj@mowgli:~$ uname -a
Linux mowgli 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

Regards,
Manoj

---

### Post by dcstar on 2007-05-01
> **manoj_paul_joseph said:**
> Hi,

I am on Ubuntu 6.06. My timezone is GMT+5:30.

My BIOS time matches the time on my timezone. Quite often, after a reboot, it gets reset to time -530.

I keep having to resynchronize with a time server. Is this a known issue? Does anybody have a clue?

manoj@mowgli:~$ uname -a
Linux mowgli 2.6.15-28-386 #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007 i686 GNU/Linux

Regards,
Manoj

Right-click the date and time panel data and go into Preferences, change the UTC setting and see if that helps.

---

### Post by manoj_paul_joseph on 2007-05-02
> **dcstar said:**
> Right-click the date and time panel data and go into Preferences, change the UTC setting and see if that helps.

Currently UTC is unchecked. Are you asking me to turn it on?

I am not on UTC timezone!

-Manoj

---

### Post by seamuso on 2007-05-02
I was having the same problem .. try [ [COLOR="Red"]this[/COLOR]](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)

---

### Post by manoj_paul_joseph on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43661](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43661) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **seamuso said:**
> I was having the same problem .. try [ [COLOR="Red"]this[/COLOR]](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)

Thanks, that seems to be it!

UTC was set to yes. And adjtime mentioned UTC in the third line..
manoj@mowgli:~$ cat /etc/adjtime
0.000000 1121000000 0.000000
1121000000
UTC

However restarting hwclock fails with this error message:
    select() to /dev/rtc to wait for clock tick timed out

Might be running into bug #43661 

-Manoj

---

### Post by Apostata on 2007-07-06
The UTC=no switch doesn't work for me.

I recently wiped off my / and installed Ubuntu Feisty 64-bit. At first boot, I thought I had it licked. I sent myself an email and all was good. Then, after rebooting, it set itself back to +5:00. Everything I've done to change this to -5:00 (Toronto...I've even tried New York) does not work.

I can't believe it's 2007 and I can't get my OS to tell the right time.

---

### Post by Ayuthia on 2007-07-06
I think that I changed my time by going to adjust Date & Time and set it to where I was located and made sure that the time was correct.  Once I did that I went to the Terminal and typed:
sudo hwclock --localtime

---

### Post by Apostata on 2007-07-06
No luck here. I went to the Time/Date settings in KDE, unchecked the time-server box (just in case), re-selected Toronto to make sure the local time was correct (12:26pm) and then used your command:
> sudo hwclock --localtime
Password:
Fri 06 Jul 2007 04:26:23 PM   -0.094233 seconds


---

### Post by Ayuthia on 2007-07-06
You might try:
sudo hwclock --systohc

That is supposed to set your hardware clock to be the same as the system time.

---

### Post by Apostata on 2007-07-29
> **Ayuthia said:**
> You might try:
sudo hwclock --systohc

That is supposed to set your hardware clock to be the same as the system time.

Unfortunately, no, that doesn't work either.

---

