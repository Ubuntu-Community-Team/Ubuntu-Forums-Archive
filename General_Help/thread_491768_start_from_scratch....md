---
title: "start from scratch..."
date: 2007-07-04
forum: General Help
---

### Post by LinRook on 2007-07-04
whats up everybody.. first off id like to introduce myself, my name is jason. now that that's outta the way...
ive been trying to get my pci lucent winmodem to work with 7.04 for about 2 weeks, off and on. im not sure if im really making any progress, so i was wondering if someone could kindly start me off from scratch.  things like, what driver will i need, how to install it properly(thats kinda where i got hung up), and configure it correctly.  any help is appreciated.. directing me to another thread or walkthrough would be fine also

---

### Post by DagMan on 2007-07-04
Hi Jason.
I don't have a Lucent Winmodem but was suprrised it isn't supported out of the box.  Perhaps it is and there's a module that needs to be loaded or a deamon that needs to run.  I found the following threads in the tips and tricks section.  They all look like they are older than 7.04 but often times this doesn't matter.
[http://ubuntuforums.org/showthread.php?t=332947](http://ubuntuforums.org/showthread.php?t=332947)
[http://ubuntuforums.org/showthread.php?t=198730](http://ubuntuforums.org/showthread.php?t=198730)
[http://ubuntuforums.org/showthread.php?t=290963](http://ubuntuforums.org/showthread.php?t=290963)
[http://ubuntuforums.org/showthread.php?t=6361](http://ubuntuforums.org/showthread.php?t=6361)


Hey... I just looked in the restricted modules package and it includes a driver for lt winmodems.  Try pasting this into a terminal and see if it makes a differance.
```
sudo apt-get install linux-restricted-modules-`uname -r`
```


Good luck with it.  I hope something there helps.

---

### Post by LinRook on 2007-07-04
so i guess it turns out that there are already the drivers that i need installed because when i entered that into the terminal....
```

j@jason-desktop:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.20-15-generic is already the newest version.
linux-restricted-modules-2.6.20-15-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
so now i just need to know why is it whenever i try to dial out with ppp nothing happens, nothing even attempts to dial.  if anyone has any suggestions that would be great.. thanks for the help so far by the way

---

### Post by LinRook on 2007-07-05
can anyone please tell me why my modem wont dial out.  it appears that i have the right drivers for it, so i've hit the wall.. i dont know what else to do to get my modem working

---

### Post by orb9220 on 2007-07-05
Did you try and post this in the Networking & Wireless thread? There may be help there.

---

### Post by LinRook on 2007-07-06
oh ok, sorry.  i was unaware this was off topic

---

