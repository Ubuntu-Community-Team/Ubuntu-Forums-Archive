---
title: "I can't boot from almost all CD/DVDs.."
date: 2007-02-06
forum: General Help
---

### Post by presbp on 2007-02-06
There is apparently a known issue that the JMicron RAID controller does not work correctly unless the drivers are installed. This JMicron controller controls my CD/DVD drives so I cannot boot a CD/DVD from them that don't have the drivers for the JMIcron installed.

I think the Ubuntu LiveCD had them because I could run that but I have tried running Puppy Linux and LinuxFromScratch and no avail. Is there a way to fix this that won't require alot of time and caffeine? I would rather not have to purchase an external DVD/CD drive just to boot CDs/DVDs. Also I have heard that USB external CD/DVD drives also have issues with booting and stuff.

I know this isn't a general Ubuntu help but I always get more help in the general forum

---

### Post by ^rooker on 2007-02-06
Is that RAID adapter on your mainboard? 
I mean: older boards have on-board IDE and RAID-controller PCI cards - newer boards have onboard IDE and often separately a RAID controller also onboard.

If that is the case, you could simply connect your DVD/CD drive to the plain IDE controller onboard.

---

### Post by presbp on 2007-02-06
it emulates PATA IDE but it's main purpose is RAID I think.  

It is onboard

---

