---
title: "How to install XP onto a virual machine"
date: 2008-01-12
forum: General Help
---

### Post by timboellis on 2008-01-12
Any help here I have tried virtualbox to run XP on it on my Ubuntu Gutsy however I get Virtualbox kernal driver not installed and then i tried Qemulator but cannot make head or takes of that all I want to do is give it a 5 gig HDD and boot from a XP iso

---

### Post by luisromangz on 2008-01-12
There is a VirtualBox repository out there, so its very easy to install and have the kernel driver working properly.

deb [http://www.virtualbox.org/debian/](http://www.virtualbox.org/debian/) gutsy non-free

---

### Post by freymann on 2008-01-12
> **timboellis said:**
> Any help here I have tried virtualbox to run XP on it on my Ubuntu Gutsy however I get Virtualbox kernal driver not installed

 So why not install the virtualbox kernal driver?

 I'm pretty sure I had to do that. I just went to System>Administration>Synaptec Package Manager and searched for what it said wasn't there. In my case, it uninstalled one thing and installed what was required and I was off to the races!

---

### Post by Maikelv on 2008-01-12
Go to synaptic , search for "virtualbox" and install the kernel driver , and the application.

In VB make a new virtual machine (pretty straightforward) and click preferenced. Go to CD/DVD rom , make it mount your cd drive. 

Insert your windows cd and click "start". While booting you might have to press F12 and choose boot from CD.

---

