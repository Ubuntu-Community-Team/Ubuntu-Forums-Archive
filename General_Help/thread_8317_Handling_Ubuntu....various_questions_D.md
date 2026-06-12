---
title: "Handling Ubuntu....various questions :D"
date: 2004-12-16
forum: General Help
---

### Post by paradox on 2004-12-16
Hi!

I have some questions for handling some Ubuntu aspects.

1) I see /etc/init.d dir contain various scripts. At boot hotplug run by default, but in older machines this introduce an important overhead. I try this command:

sudo chmod a-x hotplug

but after this, naturrally, at boot i receive a message like this: "hotplug permission denied". I can erase this message among lines infos at boot? 
After this, for exemple, ethernet card don't work (it's normal...), but i insert all necessary modules in /etc/modules file...

2) Using hotplug i receive this message at boot: 

modprobe: FATAL: Error inserting pciehp: /lib/modules/2.6.8.1-3-i386/kernel/drivers/pci/hotplug/pciehp.ko  Operation not permitted

and 

modprobe: FATAL: Error inserting shpchp: /lib/modules/2.6.8.1-3-i386/kernel/drivers/pci/hotplug/shpchp.ko  Operation not permitted

hu?!?

3) How i can disable sync with ntp.ubuntulinux.org at boot? 

4) At boot i receive this line infos: cd open failed. Why?

5) I try sudo apt-get install j2sdk but java environnement is'nt found (i have uncomment all network resources in /etc/resources.list). How i can found j2sdk for ubuntu?

TNX for your attention :D

---

### Post by Rancoras on 2004-12-16
Check out [www.ubuntuguide.org](www.ubuntuguide.org) .  I think most of your questions will be answered there.  It's a great resource.

---

### Post by jdong on 2004-12-16
Hoary has a new implementation of Hotplug with Grepmap... It essentially cuts Hotplug time down by half -- sometimes even more on old computers!

I'm debating whether or not that qualifies as a backport....

---

### Post by paradox on 2004-12-16
At the moment i haven't Hoary, only Warty (i have very bad line and i cannot upgrade all system...). Anyway i have still this problems:

1) Fixed :D

2) Fixed :D

3) How i can disable sync with ntp.ubuntulinux.org at boot?

4) At boot i receive this line infos: cd open failed. Why?

5) I try sudo apt-get install j2sdk but java environnement is'nt found (i have uncomment all network resources in /etc/resources.list). How i can found j2sdk for ubuntu?

TNX for your attention

---

### Post by Rancoras on 2004-12-16
[QUOTE=paradox]3) How i can disable sync with ntp.ubuntulinux.org at boot?[/QUOTE]

From the page I linked before:

[http://www.ubuntuguide.org/#synchronizingclocktooslow](http://www.ubuntuguide.org/#synchronizingclocktooslow)

---

### Post by paradox on 2004-12-16
[QUOTE=Rancoras]From the page I linked before:

[http://www.ubuntuguide.org/#synchronizingclocktooslow](http://www.ubuntuguide.org/#synchronizingclocktooslow)[/QUOTE]

yes, tnx, i don't see there line... :D

Remain only two final problems :D (cd failed is'nt a problem properly but j2sdk humm....i search .deb package :D)

---

### Post by jdong on 2004-12-16
rm /etc/rcS.d/S57ntpdate

I think it's S57... It's in /etc/rcS.d, ends with ntpdate.

---

