---
title: "Unusually high power consumption with Xubuntu 12.04, but not with Ubuntu 12.04"
date: 2013-05-28
forum: General Help
---

### Post by igor.sinkovec on 2013-05-28
About 8 months ago I installed Ubuntu 12.04 LTS on my wife's Dell Mini 9, and it was running reasonably well, apart from sometimes freezing when waking up from suspend. In an effort to speed it up a bit, I just recently replaced Ubuntu with **Xubuntu** 12.04 LTS. It's running better, not crashing or freezing at all. However, the **power consumption is unusually high**. The average at idle is more than 16W, which gives about 1.5h battery life - a big difference to the usual 3-4h with Ubuntu. I estimate normal power consumption should be around 7-8W, what other Dell Mini 9 users are reporting.

In all my efforts to find what could be causing high consumption and eating the battery, I couldn't find anything. I used Powertop and Powerstat. According to Powertop all is good. I also tried the i915 rc6 kernel parameters that we all used since the power regression bug after v2.6, but it wasn't any better.

Does anyone have any ideas how I could find out what's drawing so much power?

---

### Post by ohnonot on 2013-05-29
i noticed this thread before and it's just getting older so i'll give you a bump to the top although i'm no expert in these matters.

where do you get the info how much power your machine consumes? is it being justified somehow, why it consumes what it consumes?
i would say, high cpu usage and bright display and lots of fan activity?
the first, you surely checked? the fan could mean your cpu governing does not work properly (throttling cpu frequency when not needed).
with the display, the usual stuff: reduce screen brightness when on battery, shorter timeout for switching off backlight...
but xfce4-power-manager, which is handling these things on xubuntu and many other distros, has a good reputation!

---

### Post by igor.sinkovec on 2013-05-30
Thanks for your reply, ohnonot. 

I got the power readings from **Powerstat**. I accept the readings to be correct because the battery time is reduced by approximately the same ratio to the difference in power consumption in comparison to the previous Ubuntu installation and reports on power usage of other users of this same laptop. In short, *the power readings make sense*. 

High power consumption is however by no means justified. I performed the measurements when the computer was running idle. CPU was around 5%, screen brightness at or near minimum, no apps open, and the machine doesn't even have a fan. CPU frequency throttling also works properly, according to **Powertop**. I'm no novice to GNU/Linux, I have been using various distros for several years and done my share of tinkering with them. However, this issue with high power drain with Xubuntu on a small laptop beats the hell out of me. No idea what's going on.

---

### Post by ohnonot on 2013-05-31
just to establish one fact, did you completely install xubuntu, i mean from scratch with some install media? as opposed to installing xubuntu desktop on top of ubuntu?

[interesting review here.]("http://www.notebookreview.com/default.asp?newsID=4578")
seems like this is a great piece of hardware, though a bit dated.
right now i have no other advice to offer but to try another lightweight distro.

but it seems others have better advice:

Researching on pm-utils will probably help you.
Yes. pm-utils, cpufreq and coretemp.
Another package you would want to look at is Laptop Mode Tools. 
For doing quick things on my laptop I use puppy-Linux

[http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)

[http://www.howtogeek.com/55185/how-to-maximize-the-battery-life-on-your-linux-laptop/](http://www.howtogeek.com/55185/how-to-maximize-the-battery-life-on-your-linux-laptop/)

---

### Post by Dedoimedo on 2013-05-31
Do you have an Intel CPU?
Could be an Intel idle driver going wonky.
Can you please check what C-States you have and values under:
/sys/devices/system/devices/cpu/cpu<X>/cpuidle/state.

Dedoimedo

---

### Post by igor.sinkovec on 2013-05-31
@ohnonot: It was a fresh install of Xubuntu.

@dedoimedo: thanks for joining. The CPU is Intel Atom N270. Not understanding exactly which values you need I'm pasting everything (values in parentheses are different for cpu1):

```
cat /sys/devices/system/cpu/cpu0/cpuidle/state0/*
desc: CPUIDLE CORE POLL IDLE
latency: 0
name: POLL
power: 4294967295
time: 160997, (cpu1: 81793)
usage: 643, (cpu1: 413)

cat /sys/devices/system/cpu/cpu0/cpuidle/state1/*
desc: MWAIT 0x00
latency: 1
name: C1-ATM
power: 4294967294
time: 1313710047, (cpu1: 3464648847)
usage: 320265, (cpu1: 242897)

cat /sys/devices/system/cpu/cpu0/cpuidle/state2/*
desc: MWAIT 0x10
latency: 20
name: C2-ATM
power: 4294967293
time: 28297845999, (cpu1: 2846109367)
cat usage: 1998167, (cpu1: 1884889)

cat /sys/devices/system/cpu/cpu0/cpuidle/state3/*
desc: MWAIT 0x30
latency: 100
name: C4-ATM
power: 4294967292
time: 6183711150, (cpu1: 458758365)
usage: 7049790, (cpu1: 6916061)

```

I hope this makes sense.

---

### Post by Dedoimedo on 2013-06-02
Do you have a comparison with the ubuntu install btw?
Under cat /proc/interrupts, is there any core specifically doing anything more than the others?
Dedoimedo

---

### Post by igor.sinkovec on 2013-06-20
Sorry guys, I've been offline for a couple of weeks due to a big move to the other side of the world. 

Dedoimedo, no, unfortunately I don't have a comparison with the previous installation of Ubuntu. 

This is the output of cat /proc/interrupts:

```
           CPU0       CPU1
  0:    2695837          0   IO-APIC-edge      timer
  1:        836          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:      33169          0   IO-APIC-fasteoi   acpi
 12:    1583470          0   IO-APIC-edge      i8042
 14:     120869          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
 16:      43912          0   IO-APIC-fasteoi   uhci_hcd:usb5, jmb38x_ms:slot0, mmc0, i915
 17:     133041          0   IO-APIC-fasteoi   eth1
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:       1841          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 43:         89     837113   PCI-MSI-edge      eth0
 44:        117          0   PCI-MSI-edge      snd_hda_intel
NMI:       2202       8915   Non-maskable interrupts
LOC:    4729517    5593706   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:       2202       8915   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:    3283179    3315549   Rescheduling interrupts
CAL:        244        212   Function call interrupts
TLB:      44209      45080   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         59         57   Machine check polls
ERR:          0
MIS:

```

This doesn't mean much to me, I hope you can make more sense out of it.

Cheers

---

### Post by igor.sinkovec on 2013-06-27
Just recently I did a test with a live image of Linux Mint 13 Maya with Xfce, which is also based on Ubuntu 12.04, and I got the same battery life as with the Xubuntu install, approx 1.5 - 2 hours.

---

### Post by Dedoimedo on 2013-07-02
Did you try to change the power settings for your network card?
Can you try Ubuntu 12.04 live cd again, to see what it reports now.
BTW, there have been some kernel changes between 12.04 to versions .1, .2 and such.
Dedoimedo

---

### Post by igor.sinkovec on 2013-07-05
> **Dedoimedo said:**
> BTW, there have been some kernel changes between 12.04 to versions .1, .2 and such.
Dedoimedo

Hmm, that's interesting - I didn't know that. I downloaded Ubuntu and Xubuntu live images of all three versions (.0, .1, .2) and will try them as soon as I can find the time. I will report my findings.

Igor

---

### Post by Dedoimedo on 2013-07-09
Can you dump all sysctl params in your installed distro and live cd and compare?
Dedoimedo

---

### Post by igor.sinkovec on 2013-08-20
When testing with 6 LiveCD images, namely Ubuntu & Xubuntu, versions 12.04, 12.04.1 and 12.04.2 I got more or less the same power performance with all of them - half the usual battery life. I don't want to commit any of them to the disk and look for any differences because it's just too much of a hassle. I've been putting this off for more than a month now and it's about time to admit the present situation will just have to be "good enough".

Thank you all for participating.

Igor

---

### Post by Dedoimedo on 2013-08-20
So out of curiousity, what's the difference in sysctl settings between the older, installed image and the ones you checked lately?
Dedoimedo

---

### Post by GameGuru on 2013-08-20
And to just point out one cause, especially since the full current install and all Live CDs are giving the same battery life, perhaps your battery life is coming to an end.  I have had a couple laptops and as the battery dies it does lose time so maybe this last install happened at a time when your battery decided to start giving up it's life.

---

