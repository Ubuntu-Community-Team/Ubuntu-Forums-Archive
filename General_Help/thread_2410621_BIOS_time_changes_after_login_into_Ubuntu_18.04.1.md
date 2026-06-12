---
title: "BIOS time changes after login into Ubuntu 18.04.1"
date: 2019-01-18
forum: General Help
---

### Post by cam17 on 2019-01-18
I have noticed that my Acers Bios time changes 5 hours in the future fom my EST time after I log into Ubuntu 18.04.1.

 Ubuntu shows the correct time but when I log out and go to the bios the time has changed to 5 hours in the future. 

Is there a correction for this?

---

### Post by Irihapeti on 2019-01-20
*Thread moved to **General Help***, as this isn't a security issue.

Your BIOS is probably set to local time, while the Ubuntu default is to assume that the BIOS is set to UTC. This problem usually comes up when dual-booting with Windows.

You can either tell Ubuntu to assume that the BIOS is set to local time, or get Windows to work with UTC. Probably, the former is easier. See 
```
man timedatectl
``` for details (it's one of the more easy-to-understand man pages!).

---

### Post by Impavidus on 2019-01-20
If you're not using Windows, it's probably best to keep BIOS time on UTC. It's what Linux is designed for and, in case you have multiple Linux systems installed, works better when you're changing time zones or daylight saving time.

---

### Post by cam17 on 2019-01-21
Why would Ubuntu use UTC instead of local time? Why would it change the BIOS setting for a workstation that does not dual boot?

---

### Post by CatKiller on 2019-01-21
> **cam17 said:**
> Why would it change the BIOS setting for a workstation that does not dual boot?
Why wouldn't it? The only reason *not* to have the hardware clock set to UTC is when you *do* dual boot.

Having the hardware clock set to UTC and adjusting the system clock to local time, or having the hardware clock set to local time and adjusting the system clock to UTC, are logically equivalent, as long as everyone knows which it is, but the former is slightly less likely to be messed up by daylight saving changes and is the way that everyone except Windows does it.

---

### Post by cam17 on 2019-01-21
If the hardware clock is not UTC in my case EST the BIOS clock or Hardware should remain EST. In this case what was occurring is Ubuntu was the time was set for EST and received NTP time corrections but would set my BIOS clock to 5 hours in the future on a non dual boot system.

Why is the problem occurring with the Ubuntu system since the BIOS clock was initially set to a local EST time and is correct and Ubuntu which has the correct clock time and time zone sets the bios 5 hours ahead.

---

### Post by CatKiller on 2019-01-21
> **cam17 said:**
> Why is the problem occurring with the Ubuntu system since the BIOS clock was initially set to a local EST time and is correct and Ubuntu which has the correct clock time and time zone sets the bios 5 hours ahead.

It's not a problem: it's *supposed* to do that. As I said. 

If you're in the BIOS all day and it annoys you that the BIOS isn't showing the local time, you can turn it off.

---

### Post by cam17 on 2019-01-22
The reason I believe it is a problem is when I set my BIOS to the correct EST time it is **incorrectly** changed by Ubuntu. If I had another operating system running it would then get the incorrect time from the BIOS also if I go into the BIOS itself it would not show the correct initially set time.

Ubuntu does not even need to use the BIOS time Ubuntu could get the proper time via Network time protocol once the user sets the time zone. Never having to change the BIOS time.

---

### Post by CatKiller on 2019-01-22
> **cam17 said:**
> The reason I believe it is a problem is when I set my BIOS to the correct EST time it is **incorrectly** changed by Ubuntu. 

No, it is **correctly** changed by Ubuntu.

> If I had another operating system running it would then get the incorrect time from the BIOS

There is only one operating system that naturally expects the BIOS to be set to the local time: Windows. Linux, OS X, the BSDs and Unixes all use UTC for the hardware clock. If you're using the operating system that doesn't play nice with others then, yes, you would probably tell Ubuntu not to use UTC either.

>  also if I go into the BIOS itself it would not show the correct initially set time.

If I have to go into the BIOS, I have far more pressing things on my mind than what time it's set to. Perhaps you're different, and you spend all your time at the computer in the BIOS staring at the clock.

> Ubuntu does not even need to use the BIOS time Ubuntu could get the proper time via Network time protocol once the user sets the time zone. Never having to change the BIOS time.

Ubuntu will **always** change the BIOS time, which is what you want: the real-time clock in the BIOS is *terrible* at keeping time. The difference is whether it changes the time to UTC or the local time.

It's a simple fix: just a simple entry in a text file. I'm not sure why you're still complaining about it. The behaviour is by design. If you want your computer to behave differently, change the text file.

---

### Post by cam17 on 2019-01-26
I disagree since Ubuntu is changing the time in BIOS incorrectly that is a problem. No operating system should change the configured BIOS setting of a previosly correctly set BIOS to a incorrect value. Time keeping is not an issue as every operating system goes to NTP network time protocol for a proper update time setting. 

This is a security issue with Ubuntu

---

### Post by #&amp;thj^% on 2019-01-26
> **cam17 said:**
> 
This is a security issue with Ubuntu
Please enlighten us if you would with "credible" documentation

---

### Post by CatKiller on 2019-01-26
> **cam17 said:**
> I disagree since Ubuntu is changing the time in BIOS incorrectly that is a problem. 

No, it is changing the time correctly. It sets it to UTC by default, but it is trivial to change it to setting it to local time. As you have been told, many times already.

> No operating system should change the configured BIOS setting of a previosly correctly set BIOS to a incorrect value. 

Every operating system should change to BIOS clock to the correct time. The hardware clock is really, really terrible as a clock, again as you've already been told.

> Time keeping is not an issue as every operating system goes to NTP network time protocol for a proper update time setting. 

And what happens if you're offline? The BIOS clock should be updated with the most accurate time whenever it is available because, again, the hardware clock is terrible at keeping time on its own. Which is what every operating system does.

>  This is a security issue with Ubuntu

It really, really isn't.

Seriously, why do you keep posting about this? The default is what it is, and for good reason. If you wish to change the behaviour for your machine from the default it is simple to do. You have been told this already many times. You want your hardware clock to be set to local time instead of UTC? Fine, do that. It's easy. You won't, however, change the default behaviour of every operating system - except one - by whingeing about it on some Internet forum. Edit the text file and go on with your life.

---

