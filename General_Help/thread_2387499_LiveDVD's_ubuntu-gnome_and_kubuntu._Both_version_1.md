---
title: "LiveDVD's ubuntu-gnome and kubuntu. Both version 16.04.4"
date: 2018-03-19
forum: General Help
---

### Post by anon_private on 2018-03-19
Hi,

I am still having trouble connecting to the internet, and staying connected.

Can anyone suggest a method that I can use with the LiveDVD's to connect and remain connected to the internet?

I am connecting via wi-fi, and the signal is strong.

I have a stable connection to the internet using the installed kubuntu ver 14.04

Advice please

Ps. With ubuntu-gnome, when I boot the OS from the DVD drive after pressing the try ubuntu option I am faced with a log in prompt. What do I type here? I believe that I may have have hit escape to start the desktop, but I am not sure. I was trying various options. Advice at this stage also requested.

---

### Post by TheFu on 2018-03-20
Gather information.
* what wifi chips does the machine use?  Are the correct drivers used?  Are there settings you need to make?
* what is different between the 14.04 wifi setup and the liveCD setup?
* what access point is being used? Are there known issue with linux connecting to it?  I've seen terrible problems with netgear APs.  
* If it comes to it, are you willing to swap out the AP?  How much effort are you willing to spend on this? If it can be fixed forever for $80, is that something you'd consider?

Can you run with **wifi-info** script to capture the computer-side information?  That would be the most helpful at this point.

---

### Post by anon_private on 2018-03-20
Question 2 seems the most probable.
Q3. I have no trouble connecting with kubuntu 14.04
Q4 No

There must be a command that will give the required information, e.g iwconfig

I am hoping it is something simple such as: the live DVD has power management on; or, IPv6 needs to be set to 'ignore'

I am looking for an up to date version of Linux that just works. Sooner or later, I will need to migrate from kubuntu ver 14.

---

### Post by TheFu on 2018-03-20
> **anon_private said:**
> 
I am looking for an up to date version of Linux that just works.

I don't think that to be likely.  The HW involved is likely old and few people are still using it ... cannot tell for sure without the requested facts.  Things that used to work and break often are due to newer versions of drivers that were released to support newer versions of the hardware.   While that isn't the only reason, it is the most common.

Really - to get any better help, the **wifi-info** script needs to be run and results posted.  Search for links to it in the "Networking" subforum here.

I migrated most of my remaining 14.04 systems last month. Some were good, clean, migrations  and a few were broken until I manually fixed each of the issues.

---

