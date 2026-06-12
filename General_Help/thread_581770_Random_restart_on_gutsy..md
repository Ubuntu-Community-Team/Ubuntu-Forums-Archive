---
title: "Random restart on gutsy."
date: 2007-10-19
forum: General Help
---

### Post by bravesfan on 2007-10-19
So I come home from work today and the machine is sitting at the login prompt. I've searched logs and don't see any sign of a reboot or machine failure. The machine is firewalled off with no services running. I am running compiz and that's about it.

Has anyone had this problem, know what the issue might be, or know a certain place I can grep to look for an unexpected reboot?

Thanks.

---

### Post by fain on 2007-10-24
random rebooting could mean a bad power supply or maybe the power went out in your house for a short time.

---

### Post by mfdc1969 on 2007-10-24
I have just had a similar issue with my desktop - it just "shut-off" while tovid was encoding a DVD. It fails to restart, booting up only as far as GRUB and then "pop" the power goes out again, and again, and again.

I'm certain this issue is not related to Gutsy, which I just installed 2 days ago. It also happened a few months ago when it had XP/Fiesty dual boot. I deleted all info from the HDD and installed Gutsy without XP and it seemed to run so well until 10 minutes ago. If it is a power supply or other hardware issue I expect that some record of it may be in the logs?

Now, I want to remove the HDD and pop it into an external USB enclosure and search the logs from my laptop. 

Can either of you suggest where/which logs I should start searching to try and learn more about my system failure?

Any comments/suggestions would be greatly appreciated!

Thanks,
Mike

---

### Post by fain on 2007-10-24
The power supply failure would not be in the logs because it wouldnt have time to write anything to the disc b4 it shutdown. Maybe "lm-sensors" would be compatible with your motherboard. It might log voltage problems.  The best way would be to get it checked out with power supply tester. They are not too expensive you can get them on ebay or tiger direct. I'm sure the local computer shop has one. 


Also check inside your case for dust build up on the processor heat sink, power supply fans and other areas. Over heating can cause this too. Get a can of oxygen read the instructions carefully and blow it out. You don't want to get any liquid in there and dust from a regular blower could kill your pc too.

Hard drive failure could cause random reboots too. Theres a number hardware related problems that do this. As there is software problems too.

These things usually take quite a lot of troubleshooting and trial and error can get expensive. You can either buy the testers for each of the suspected components or start replacing components out until the problem goes away. You might just take it to that local computer shop and pay them 50 bucks to see whats wrong. They have all this equipment already.

---

### Post by cytg on 2007-10-24
test it out with a livecd ? maybe even "ultimate boot cd" ?

[http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

---

### Post by mfdc1969 on 2007-10-26
Thanks for the link to the UBCD - it looks great but I can't keep the system up long enough to use much of anything.

I turned on the computer - there wasn't much wind pushing out the back of the PSU, which I cleaned yesterday. So it booted to BIOS and I watched the System Health Stats for 3 minutes until the power popped off. 

All voltages monitored by the BIOS Health are within 1% and the System Temp stays between 25 - 27 degrees C (sorry for the metric but that's Canadian eh!).

The CPU temperature was a much different story:

- start @ 25 degrees C
- 52 degrees C after 1 minute
- 62 degrees C after 2 minutes
- then at 67 degrees C I noticed a white flashing underscore overtop of the temperature and it powered off

So it seems to me that the CPU is not being cooled - am I correct? 

If so that means a new CPU fan and if it still persists replace the PSU as it's probably not pulling the warm air out of the case. Sounds like I have to get busy and fix some hardware issues so I can get back to enjoying my new Gutsy!

Thanks for all you help!

Mike

---

### Post by Namakemono456 on 2007-10-26
I had the same problem on Feisty Fawn, just some pointers though.

1. I spent $70 on a new Acer 500W power supply because someone said that was the problem, didn't fix it.
2. I spent $60 on an LG CD-Drive because someone said that night fix it, it didn't.
3. I spent $140 on a new WD raptor drive because someone said that would fix it, it didn't.

What i did learn though after getting Gutsy to install successfully is that the video drivers were causing my problems. Check your card.

---

### Post by mfdc1969 on 2007-10-26
Thanks for the cautionary note - I think I will let a local shop diagnose the issue so as to limit my expenses but I want to be knowledgeable when I walk in and ask for help.

I have an nVidia GeForce TC6200 64MB DDR which the restricted modules picked up right away. Under Dapper I configged the xorg.conf myself but this time I allowed Gutsy's Restricted to do it all for me. 

The high CPU temps stated in my previous post occur and I lose power ***before*** the OS even loads - doesn't that rule out any driver issues? 

I guess a simple test would be to remove the video card and boot to BIOS and watch the temps again and see if it happens again?

---

### Post by Namakemono456 on 2007-10-26
Sorry didn't pay attention to your post :P I would think that your CPU isn't getting any cooling, did you check the fan at all and see if it was seized? Otherwise are you overclocking it or did you recently upgrade it and your motherboard doesn't support the CPU?

---

### Post by mfdc1969 on 2007-10-26
No worries - thanks for your help!

I did upgrade the CPU but that was a year ago and it ran fine. I only upped it from an AMD 3500+ to a 3800+ and it ran Dapper and XP for over 8 months. The mobo manual says it's compatible.

I cleaned all the fans, removed the CPU fan and blew out the CPU heatsink too... all I can think of is now this is a matter of the cpu fan/heatsink not doing it's job or the PSU fan not pulling the air out of the case.

---

### Post by fain on 2007-10-26
Just asking, did you use any thermal grease?

---

### Post by mfdc1969 on 2007-10-26
The upgrade was done by the retailer under warranty service - so I can't really say what was done for certain. I was told the CPU and mobo were replaced.

I am taking it in to different repair shop tomorrow to see what they can discover. I have been quoted a $35 diagnosis fee - seems fair to me.

---

### Post by fain on 2007-10-27
Ya i believe the repair shop here charges 50 dollars. So 35 seems about right. If they would charge that, i might take my pc to them once in a while. Ya probably not though, I love getting my hands dirty.

---

