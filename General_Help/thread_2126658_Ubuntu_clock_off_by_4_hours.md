---
title: "Ubuntu clock off by 4 hours"
date: 2013-03-17
forum: General Help
---

### Post by EricDallal on 2013-03-17
I have the following problem in Ubuntu:
Whenever I start the OS, it shows a time that is off by four hours. When I log in, the problem is fixed.

This results in the following problem in Windows (I have a dual boot system):
When I go into Ubuntu and then into Windows, the time is off by four hours. When I fix the Windows time and restart without going into Ubuntu, the is still right.

The BIOS time is also correct. This is rather annoying. Any ideas?

---

### Post by ac5jw on 2013-03-17
Hello, I have been installing a lot of Linux Ubuntu and other OS lately.  I have seen similar situations with the time.

Usually, I notice that the installation reveals a default setting for Universal Time Coordinated, or UTC.  If you see such a default setting during installation, you may choose to leave it alone because you will have a chance to change the time to your local time soon enough in the actual installation choices you are given, or even later after booting the system to complete the installation.  I prefer to set my clock in Ubuntu with multiple locations at once, so I can easily click on the clock and see all the times displayed.

I hope it helps.  What you are describing sounds pretty normal to me.  And it has an easy fix through the clock time on the desktop or even in the Settings area.  Be prepared to use your password to unlock the options if you wish to change something !

Good luck !

Raleigh - ac5jw

---

### Post by ac5jw on 2013-03-17
Hi, I am sorry I did not answer your whole question.  I have not been trying dual-boot scenarios yet, so I do not know about the effect of Windows time on your installation.  That will be a mystery for me.

R

---

### Post by sanderj on 2013-03-17
> **EricDallal said:**
> I have the following problem in Ubuntu:
Whenever I start the OS, it shows a time that is off by four hours. When I log in, the problem is fixed.

This results in the following problem in Windows (I have a dual boot system):
When I go into Ubuntu and then into Windows, the time is off by four hours. When I fix the Windows time and restart without going into Ubuntu, the is still right.

The BIOS time is also correct. This is rather annoying. Any ideas?

See [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts) for instructions.

HTH

---

### Post by Frogs Hair on 2013-03-17
Windows was four hours ahead for me on Friday and the trouble shooter indicated Windows update . I selected fix and ran the update manager and the time reset. The IE 10 update is what I received.

---

### Post by Irihapeti on 2013-03-17
Windows assumes that the BIOS is set to local time (unless a rather obscure fix has been applied). Therefore, Ubuntu and any other Linux on the same machine needs to be set so that it also assumes that the BIOS is set to local time.

To do this, edit /etc/default/rcS as root and change the line:

```
UTC=yes
```
to
```
UTC=no
```

Then reboot. You might need to adjust your time along the way, but once it's done it should stay like that.

I'm running 12.04.2.  I'm assuming that it's the same in 12.10.

---

### Post by EricDallal on 2013-03-17
Thanks, Irihapeti. That sounds promising. I'm currently transferring my files from my old to my new computer so I'll try this in about 4.5 hours.

---

