---
title: "Are these messages is syslog relevant to my system freeze?"
date: 2015-08-10
forum: General Help
---

### Post by budworthtdog2 on 2015-08-10
My system has been freezing lately. The whole thing, no mouse or keyboard action. It's not super common, it's happened maybe three times in the past month but considering it only happened once in a blue moon in the past it seems unusual. These are the last messages recorded in the syslog before the last freeze. The time stamps on them seem like they may have been recorded a few minutes before it actually froze but I could be wrong. Maybe these are relevant to why the system froze but maybe they are not. Could these point me in the right direction to find out what's been causing my computer to lock up?  
   

  	 	 	 	   Aug 10 19:44:55 ******** kernel: [78874.170087] INFO: NMI handler (perf_event_nmi_handler) took too long to run: 1.100 msecs
 Aug 10 19:44:55 ******** kernel: [78874.170092] perf interrupt took too long (10842 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
 Aug 10 19:45:40 ******** kernel: [78918.947602] perf interrupt took too long (10769 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
 Aug 10 19:46:21 ******** kernel: [78960.777041] perf interrupt took too long (10700 > 10000), lowering kernel.perf_event_max_sample_rate to 12500

---

### Post by VMC on 2015-08-10
This type of freeze was reported last year. Not sure if any help though:
[http://ubuntuforums.org/showthread.php?t=2253552](http://ubuntuforums.org/showthread.php?t=2253552)

What type of mouse are you using? Can you change out the mouse to see if it improves.

---

### Post by tgalati4 on 2015-08-11
NMI's are Non-Maskable Interrupts, and those are generally bad.  They are hardware interrupts that the CPU and BIOS do not know how to handle.  You can set your BIOS to ignore them or to halt when they happen.  First I would clean out the machine and reseat the RAM and cables.  If this is a laptop, then it's possible that the motherboard has small fractures from flexing.

If the above boot message happens during every boot, then that is the kernel's way of adapting to your hardware's CPU and motherboard front-side bus speed. The kernel thinks it is taking too long to respond to an NMI so it is reducing the time between checks.  This can reduce performance slightly.  This may be normal for your hardware, or something has degraded (like a motherboard capacitor) which causes more noise and interferes with correct operation.

I presume that your computer was working OK for a long period of time, and now these freezes are starting to happen?  Or, was this a brand new install of Ubuntu?

How old is the computer?  What is the make and model?

Keep a terminal open at all times and examine the following command immediately after a freeze:

```
dmesg | tail -50
```

Post any error messages.

---

