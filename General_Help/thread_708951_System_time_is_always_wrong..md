---
title: "System time is always wrong."
date: 2008-02-26
forum: General Help
---

### Post by Darknite12 on 2008-02-26
Hello Everyone, 

I have run into this problem, that is terribly annoying.  My hwclock shows the correct time
```
$ hwclock
Sun 24 Feb 2008 08:41:34 AM EST  -0.957124 seconds
```

but my System time is incorrect.

```
$ date
Sun Feb 24 08:12:11 EST 2008
```

There no specific pattern to the time difference, the system time just lags behind.  The longer it goes without being corrected, the bigger the time difference is (it always lags behind, it never goes ahead or anything like that).  This leads me to believe that its not a Time Zone problem.  I have read other post that give some insight on the problem, [http://ubuntuforums.org/showthread.php?t=219340](http://ubuntuforums.org/showthread.php?t=219340).  But this has not resolved my issue. 

I have AMD Athlon 64 Processor 3200+ and have installed the Ubuntu 7.10 64bit kernel

```
$ uname -a
Linux cisco 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```

Previously I had installed the normal i686 kernel (not 64bit) and I did not have this problem.  This tells me that its not the BIOS clock,  (besides the motherboard is new)

I have edited the /etc/rcS so that the utc = no

```
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

```

Has anybody ran into this problem.  Please let me know.  Any help will be appreciated.

---

### Post by geraldm on 2008-02-27
the system time uses a jiffy counter to track its time, and that does tend to vary after a while.
You can set the system time with the  command "date"

Gerald

---

### Post by astrotech226 on 2008-02-27
You can also set the machine to keep it's clock in sync with an ntp server.  This is almost mandatory if you are maintaining a number of servers or you end up with all sorts of problems.

---

### Post by Darknite12 on 2008-02-27
Thanks for the reply,

geraldm: The system time changes if I don't adjust it and it shouldn't change that much.  I haven't adjusted since the time of this post and look at the time difference between the system clock and the hardware clock.

```

date
Wed Feb 27 20:14:34 EST 2008

```

```

hwclock
Wed 27 Feb 2008 10:11:29 PM EST 

```

Setting the system time with the date command is something I want to avoid, since it really should not work like this.

astrotech226:  I will give ntp a try.  It was never necessary when I had the i386 kernel, this only happens when I install the x64 kernel.

Please anybody else have any suggestions????

---

### Post by mbsullivan on 2008-02-28
Hi Darknite12,

(1) If you just want to sync your hwclock -> sysclock, you can do it with:

```
sudo hwclock --hctosys
```

(2) Rather, if you want to use an NTP server to sync both, use the following procedure:

```
sudo ntpdate ntp-1.mcs.anl.gov
sudo hwclock --systohc
```

This NTP server is based out of Argonne National Lab, outside of Lemont, IL. If your sys clock keeps slowly losing time, I'd probably just periodically update with an NTP server. The easiest way to do this would be to do it on bootup / X Windows session start. If you really want to automate it, you could schedule it as a cron job so that it will be scheduled to execute periodically without your input.

Hope this helps!
Mike

---

### Post by Mr. C. on 2008-02-28
> **Darknite12 said:**
>  It was never necessary when I had the i386 kernel, this only happens when I install the x64 kernel.

This is the interesting data.  Its hard to know the reason for why the kernel's clock has drifted so far.  I can think of a number of reasons why it can happen, but no easy answer that you can directly apply.  Its possible there's a bug in the kernel code that maintains the system time on the x64 platform for the release you are running.  There may also be buggy device driver that is locking out interrupts for a long period of time, causing the periodic interrupt clock from missing some ticks.  That drift is pretty substantial, so its worth investigating further.

While ntp will certainly facilitate keeping the clock in time, just as a mother pushes along her children to keep pace, its only masking an underlying problem. 

Time to start collecting data and checking the kernel archives and mailing lists.
MrC

---

### Post by Darknite12 on 2008-02-28
mbsullivan:

I would not like to do this.  I would really like my system clock to work without the help of ntp.  Why was it working before when I used the i386 kernel and now with the x_64 kernel, it won't keep up?  Although for now your solution has facilitated the syncing of the clocks but I would really like to get it working without the help of ntp.

Mr. C.
I guess this is more or less what I wanted to hear.  If its an issue with the kernel, where should I check to see if this issue has been fixed?  Thank you for taking the time in responding

---

### Post by SunnyRabbiera on 2008-02-28
every so often I see my clock going astray, but thats why I keep it synched with the net.

---

### Post by astrotech226 on 2008-02-28
What is the output of this after the machine has been on for a while and you start to see the drift?
```

sudo cat /proc/interrupts
```

I agree that this should be fixed, but I certainly hope you are using ntp, especially in a server environment.  If not, your time will never be really accurate anyway.  Your hardware clock can't keep completely accurate time.  So the ideal situation is to sync your system clock to ntp and have it set your hardware clock when you shut down.

---

### Post by Mr. C. on 2008-02-28
> **Darknite12 said:**
> mbsullivan:

I would not like to do this.  I would really like my system clock to work without the help of ntp.  Why was it working before when I used the i386 kernel and now with the x_64 kernel, it won't keep up?  Although for now your solution has facilitated the syncing of the clocks but I would really like to get it working without the help of ntp.

Mr. C.
I guess this is more or less what I wanted to hear.  If its an issue with the kernel, where should I check to see if this issue has been fixed?  Thank you for taking the time in responding

System's that care about time accuracy use NTP.  Don't feel concerned about it.

You might want to check the linux kernel mailing list archives, and some of the existing bugs:

[http://marc.info/?l=linux-kernel](http://marc.info/?l=linux-kernel)

Example searches:

[http://marc.info/?l=linux-kernel&w=2&r=1&s=clock+drift&q=b](http://marc.info/?l=linux-kernel&w=2&r=1&s=clock+drift&q=b)
[http://bugzilla.kernel.org/buglist.cgi?quicksearch=clock+drift](http://bugzilla.kernel.org/buglist.cgi?quicksearch=clock+drift)

If you don't find something that helps workaround/resolve, post a message to the kernel list and describe your issue; someone's bound to help you get more data to narrow down the issue.

MrC

---

### Post by Darknite12 on 2008-03-01
astrotech226:  The funny thing is that, my hwclock is dead on, it doesn't drift at all.  What drifts is my system time.
```

sudo cat /proc/interrupts
           CPU0
  0:   23005906   IO-APIC-edge      timer
  1:         58   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:      16274   IO-APIC-edge      i8042
 14:        218   IO-APIC-edge      ide0
 15:     793980   IO-APIC-edge      ide1
 20:     429831   IO-APIC-fasteoi   sata_via, eth0
 21:        197   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, ehci_hcd:usb5
 22:         94   IO-APIC-fasteoi   VIA8237
NMI:          0
LOC:   23005857
ERR:          0

```

This is the correct time
```

$ hwclock
Sat 01 Mar 2008 12:44:07 AM EST  -0.142159 seconds

```

This is the wrong system time

```
$ date
Fri Feb 29 23:43:52 EST 2008

```

So as you can tell, at this instance its a little more than an hour behind.  I have to manually set the system time forward to the right time.  I mean the hwclock is DEAD ON, how come the system clock drifts by sooooo much.

Mr. C.:
Thanx for the references, I'll see what I can dig up.

---

### Post by Mr. C. on 2008-03-01
> **Darknite12 said:**
> 
Mr. C.:
Thanx for the references, I'll see what I can dig up.

Let us know what you find. These bugs are always tricky to find short of debugging the kernel.  Having spent enough time in clock.c interrupt code, I can tell you for certain its a bundle of joy!

---

