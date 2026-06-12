---
title: "Ubuntu crashes - graphics driver problem?"
date: 2024-07-25
forum: General Help
---

### Post by kona365 on 2024-07-25
Hi.  

Sorry, please forgive me, I'm rather inexperienced (just an end user) and only have basic knowledge of Ubunbtu so looking for beginners help.

I have a problem with this fairly new (to me) NUC style computer that I have with the latest Ubuntu installed.  Only use it for general firefox browsing and thunderbird email.  System details report below.  

I suspect the graphics driver keeps crashing.  

The machine is OK for the first half hour or so, but if I try anything intensive, the machine will either freeze entirely with a large amount of disc activity (requiring a long press on power switch) or will kick me back out to the log in screen.  When I say 'intensive', I mean viewing a youtube video, or a 360 panorama, at which point it often freezes for 30 seconds or more.  

I have done multiple searches and tried different things (I think I have attempted to use x org graphics driver ???) to no avail.  

Is the machine just not up to running the latest Ubuntu?  Happy to be told that it just isn't.  I thought it might be a memory problem (4gb), but I installed Lubuntu 22.04 a year or so back in the hope that that may be less resource hungry but that had the exact same issues with the crashing.  

Such a shame, as I really like the open source ethos and now need the NUC style machines (for limited space reasons).  I have been using ubuntu for last two decades on older full tower style machines, running ubuntu, handed down to me without any problem like this before at all.  

The same spec machine (I have two of them) runs windows 10 superbly.  So my limited understanding is that it's a graphic driver problem.  

Is there a log file somewhere on Ubuntu that I can look at (and possibly report here) to see why the crashes are happening?

Any help or suggestions would be greatly appreciated.  

Thanks,
K



# System Details Report
---

## Report details
- **Date generated:**                              2024-07-25 08:37:11

## Hardware Information:
- **Hardware Model:**                              Lenovo ThinkCentre M93p
- **Memory:**                                      4.0 GiB
- **Processor:**                                   Intel® Core&#8482; i5-4570T × 4
- **Graphics:**                                    Intel® HD Graphics 4600 (HSW GT2)
- **Disk Capacity:**                               500.1 GB

## Software Information:
- **Firmware Version:**                            FBKTDBAUS
- **OS Name:**                                     Ubuntu 24.04 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.8.0-39-generic

---

### Post by currentshaft on 2024-07-25
I'm sorry to tell you, but you need more than 4 gigabytes of memory to run a modern desktop OS in 2024. You can confirm by running "free" or "top" when this happens to observe respective system resources.

Fortunately, RAM is very cheap these days.

---

### Post by kona365 on 2024-07-25
Hi Currentshaft.  Thanks for replying.

Would that also be the case for Lubuntu 22.04, which also demonstrated the same problems when I installed that?

---

### Post by tea for one on 2024-07-25
> **kona365 said:**
> Would that also be the case for Lubuntu 22.04, which also demonstrated the same problems when I installed that?
I would expect Lubuntu 22.04 to run perfectly with 4GB RAM.
There must be something else at play here?
Download a Lubuntu 24.04 iso and make a bootable USB.
Then, run a "live" session for a few hours to see if any freeze/crash occurs?

---

### Post by kona365 on 2024-07-25
Hi Tea for one. 

It definitely continued under Lubuntu when I clean installed Lubuntu 22.04 last year.  

Hoped that a full clean install of Ubuntu 24.04 lts might have solved it, but not so.   

The only thing that is different to any normal install is that I need a special driver for my rather strange AU wifi adapter - specifically [https://github.com/morrownr/8821au-20210708/](https://github.com/morrownr/8821au-20210708/)

Might that be that be the cause of the issue perhaps?  If you think so, is there a recommended usb wifi adapter that Ubuntu supports  with native drivers that I might purchase?

---

### Post by tea for one on 2024-07-25
I doubt if the wifi driver is causing any crashes.
Did you run a "live" session before installing Lubuntu 24.04?

---

### Post by kona365 on 2024-07-26
Hi Tea for one.  Thanks for your help and sorry to use up your time.

Hmmmm - I have just tried to create a bootable live Lubuntu USB key, and had multiple problems.  I can't get this machine to boot from USB no matter what I do.  Told you I was a beginner.  Tried different disc managers (rufus, etcher, image writer), different USB keys, different boot BIOS priority settings, different USB sockets and... it wont boot from USB.  Can't explain this, as I know it worked fine when I installed Lubuntu from USB  last year and Ubuntu 24.04 in April this year.  Not sure I would have been able to install the necessary wifi adapter driver anyway onto a live lubuntu disc.  

Sorry, I can't test a live Lubuntu session.  

Anything else you can suggest before I give up and format / install Win 10?

---

### Post by tea for one on 2024-07-26
> **kona365 said:**
>   I can't get this machine to boot from USB no matter what I do
This is a PC/UEFI/BIOS problem
> **kona365 said:**
>  Anything else you can suggest before I give up and format / install Win 10?
Reset UEFI/BIOS to default
Disable Secure Boot
Disable TPM and other similar security settings 

Create your bootable usb with one of the following:_
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
Startup Disk Creator (included in Ubuntu)

Any progress?

---

