---
title: "System Auto-boot on a schedule (or something similiar)"
date: 2007-04-26
forum: General Help
---

### Post by SadaraX on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: hibernation, standby, sleep, booting, auto [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am looking for a method to make my Linux system startup at a specify time. If this cannot be done from a cold boot, can the system wake up from hibernation or sleep? My goal is to have the hard drives not spinning so it will be quieter while it is not being used. Optimally I would love to have the system-fans and the CPU fans no spinning either until needed. Can anyone think of a way to do this?

Extra details:
I have a dedicated linux machine using MythTV that records every morning around 5:30 am. I leave the machine on during the night so it can record in the early morning, but it makes a fair amount of noise. I have a cron-job set to turn off the machine after it finishes recording. Optimally I would like the machine to boot up just before it has to record.

---

### Post by firefly2442 on 2007-04-26
You might want to look and see if Wake-on-Lan would work:

[http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)

I know nothing about it but at least it's a starting point.

Good luck. :)

---

### Post by wjston on 2007-04-26
> **SadaraX said:**
> **This post could be related to an Ubuntu bug filed at**: hibernation, standby, sleep, booting, auto [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am looking for a method to make my Linux system startup at a specify time. If this cannot be done from a cold boot, can the system wake up from hibernation or sleep? My goal is to have the hard drives not spinning so it will be quieter while it is not being used. Optimally I would love to have the system-fans and the CPU fans no spinning either until needed. Can anyone think of a way to do this?

Extra details:
I have a dedicated linux machine using MythTV that records every morning around 5:30 am. I leave the machine on during the night so it can record in the early morning, but it makes a fair amount of noise.** I have a cron-job set to turn off the machine after it finishes recording**.

I have two systems that record during the day and I would appreciate it if you could share how you set up your cron job to shutdown your systems after recording.

>  Optimally I would like the machine to boot up just before it has to record.

I could not set up my systems to wake on alarm using the bios like some have suggested; however, I solved this issue by purchasing a digital timer ($16.00 Can.) and setting the Bios to wake after power outage. I then set up my digital timers to shutdown at a time I knew the systems would be down (in my case I have the timers shutting off at 3:00 A.M. on Monday to Friday).  I then have the timers come on approximately 10 minutes prior to my first scheduled recording, which allows MythTV sufficient time to gather any scheduling information. This has worked flawlessly for me over the past six months, but I would like to configure each system to power down when it is idle.

Hope this helps

---

### Post by majoridiot on 2007-04-26
you might see if this will work for you... [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

if your mobo will comply, mythtv can wake itself up and shut itself down on its own. :D

---

### Post by thelinuxguy on 2007-04-27
The BIOS wakeup function on your motherboard should do it. For changing the wakeup time without getting into the BIOS, nvram-wakeup is available in the repositories. Give it a try.

---

