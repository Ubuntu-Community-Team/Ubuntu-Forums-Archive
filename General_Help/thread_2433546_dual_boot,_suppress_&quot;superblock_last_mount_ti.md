---
title: "dual boot, suppress &quot;superblock last mount time is in the future by less than a day&quot;?"
date: 2019-12-20
forum: General Help
---

### Post by mathog on 2019-12-20
Yesterday I upgraded the linux side of a dual boot Windows 7/ Ubuntu 16.04LTS system to Ubuntu 18.04LTS.  The RTC holds localtime (or problems keep popping up in Windows.)  In 18.04 now when it starts it emits this message for /dev/sda5 once, sometimes twice:

```
Superblock last mount time is in the future. (by less than a day, probably due to the hardware clock being incorrectly set)
```

It never did that for 16.04LTS.  This is coming from the Kernel which must be checking the RTC against that superblock.  Is there some way to tell the kernel that the RTC is local time?  I looked for a kernel parameter to do that but didn't find one.

Yes, I can suppress this by making the linux side use UTC but then Windows is a mess (even with the registry hack which supposedly lets it use UTC too.)

It also takes about twice as long to boot Ubuntu as it used to, but not sure if that is related to this message or not.

Thanks,

David Mathog

---

### Post by oldfred on 2019-12-20
Hardware clock issues may be due to failing coin battery on motherboard?

       [http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows](http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows)
Clock and some boot settings like fsck, login,   tmp retain time.
/etc/default/rcS
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no 
sudo hwclock --localtime --adjust

---

### Post by mathog on 2019-12-20
> **oldfred said:**
> Hardware clock issues may be due to failing coin battery on motherboard?

Checked that.  Rebooted into the BIOS and it showed the correct local time.

I think the issue is just that the superblock gets a UTC time stamp (even though the machine is set to use local time), the RTC is local time, and at boot the kernel compares the two at a very early stage and warns.  This is probably systemd insisting on stamping a UTC time even though the machine is set elsewhere to use local time.

---

### Post by Impavidus on 2019-12-21
> **oldfred said:**
> Hardware clock issues may be due to failing coin battery on motherboard?

       [http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows](http://askubuntu.com/questions/90504/why-does-time-change-in-ubuntu-after-installing-windows)
Clock and some boot settings like fsck, login,   tmp retain time.
/etc/default/rcS
# Set UTC=yes if your hardware clock is set to UTC (GMT)
UTC=no 
sudo hwclock --localtime --adjust

The answers in that link are outdated. See [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876). I think this changed with systemd, somewhere between Ubuntu 14.04 and 16.04.

---

### Post by mathog on 2019-12-29
This is an odd problem.  It gives that error most of the time, but not all the time.  Regardless of whether or not the error appears looking at rtc after login the time is always as expected to within a minute when compared to my watch.  Perhaps the change is that in the kernel the "time is different" window has been narrowed somewhat so that being (for instance) 45 seconds off now triggers the warning when previously it did not?

---

### Post by Yellow Pasque on 2019-12-30
> It gives that error most of the time, but not all the time.

Is /dev/sda5 an NTFS partition? Does the message only occur when you've booted into Windows between Ubuntu boots?

> Yes, I can suppress this by making the linux side use UTC but then Windows is a mess (even with the registry hack which supposedly lets it use UTC too.)

Hmm. I never had an issue with Windows once I set the registry key. I always set my machine's clock to UTC time and use the registry key to make Windows stop messing with it. Are you using Quad word (QWORD) if it's a 64-bit version of Windows?

---

