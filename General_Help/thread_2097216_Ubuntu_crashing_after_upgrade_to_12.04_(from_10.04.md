---
title: "Ubuntu crashing after upgrade to 12.04 (from 10.04)"
date: 2012-12-22
forum: General Help
---

### Post by pearldrums on 2012-12-22
Hey guys, I don't even know where to start. Generally Ubuntu has been pretty solid for me. I've had minor bugs and stuff that I can work out, but I've never had problems with it crashing. After I upgraded to the latest LTS I've been experiencing crashes, and given that I've never had that I have no idea how to diagnose this. I'm not sure whats triggering them. Is there something similar to the event viewer in windows?

[B]
More information:[/B]

-**What i mean by "crashing"**: My screens will go blank and my box fan will go to max (I don't think CPU fan is included in this, but I'm unsure). Keys are unresponsive. The machine's physical power and restart buttons located on the box are unresponsive. I have to turn the power off on my power supply in order to shut it down.

-I have windows installed parallel and it is not crashing so **I believe it is Ubuntu related not hardware.**

-**It WILL crash. **Sometimes it happens shortly after I log in, sometimes it happens if I leave it on while I'm at work, but inevitably within around 24 hours it will crash.

-If it happens while I'm at my computer, it seems like it is always after I do something. It doesn't randomly do it while I'm reading an article, but while I'm clicking on something, opening something, trying to install an update, etc. This might be just coincidence.

Thanks for any help.

---

### Post by sudodus on 2012-12-22
This problem could be anything, but we have to start somewhere.

I had better luck upgrading from 10.04 to 12.04, but it took a lot of time, several months until I could do 'everything' in my new environment. Of course many things have improved too.

Back to your problem: Could it be, that you lost your swap, and the system crashes when it runs of of memory. Check with ```
top
```, probably on the fifth line, there is information about swap.

---

### Post by pearldrums on 2012-12-22
> **sudodus said:**
> Back to your problem: Could it be, that you lost your swap, and the system crashes when it runs of of memory..

Thanks for your help... heres what it says for swap:
Swap:  6032372k total,       44k used,  6032328k free,   326480k cached

---

### Post by sudodus on 2012-12-22
You have swap, that is not the problem.

It could be bad RAM, but one would guess that Windows would be affected by that too. Anyway, you can run ***memtest*** from the grub menu.

It could also be something wrong with the disk memory: a logical error (badly written record) or a bad sector (physically damaged) in the part of the drive that is used by Ubuntu.

Boot a live system from your Ubuntu install CD/DVD/USB drive, and avoid mounting any of the internal drives. Run ```
e2fsck -f /dev/sdxy
```
on the ext partition(s), where x would be a for the first drive and y would be 5 for the first logical partition, so for example /dev/sda5

You can check for S.M.A.R.T. status (usually in the BIOS, otherwise with some tool, for example smartctl) to check for physical errors.

You can also make sure that the system is up-to-date with

```
sudo apt-get update
sudo apt-get upgrade
```
and if necessary
```
sudo apt-get dist-upgrade
```

A next step might be to start looking at log files, but I am not good at understanding them. Let us hope someone else will help you with that ;-)

---

### Post by pearldrums on 2013-01-01
Sorry i haven't responded to this in any sort of timely manner, i wanted to try an put my computer through a few paces before giving a false positive. I'm not sure what apt-get update and apt-get upgrade do exactly (as it appears to me that they would be run with the update manager) but after running that code i haven't had a single crash (for over a week now). Thanks for your help!

---

### Post by sudodus on 2013-01-01
> **pearldrums said:**
> Sorry i haven't responded to this in any sort of timely manner, i wanted to try an put my computer through a few paces before giving a false positive. I'm not sure what apt-get update and apt-get upgrade do exactly (as it appears to me that they would be run with the update manager) but after running that code i haven't had a single crash (for over a week now). Thanks for your help!
Congratulations to a good and working system :KS

Yes, apt-get is a command line interface to the update manager. See ```
man apt-get
``` and it certainly helps to have an updated system.

---

