---
title: "hotplug"
date: 2004-11-27
forum: General Help
---

### Post by chapman2 on 2004-11-27
I've installed Ubuntu Warty and am very pleased with it.  However, booting has become a problem;  my system hangs right after "hotplug subsystems".

I've searched the forums, and bug reports, but can't quite find an answer.  As I remember the answer I found posted was that a usb device might be the problem, and adding the device to /etc/hotplug/blacklist will solve it.  But there is no output after "hotplug subsystems" so I have no idea what device is causing my problem, (I put hw_random, pciehp, & shpchp in blacklist).  Where do I find a log of what devices hotplug was trying to load?

P.S.  I can start ubuntu if I boot into windows, or any linux livecd and then reboot into ubuntu. :-k

---

### Post by az on 2004-11-27
Look at 
/var/log/messages
/var/log/syslog
/varl/log/kern.log

---

### Post by kris kincaid on 2004-11-30
I am having a similar problem. My system hangs at "starting hotplug subsystem", but the only problem is I can't get past it. I am unable to boot into my fresh new Ubuntu system.

Any ideas for bypassing it? I have searched this site and I have Googled for an answer. I must be the only one!!  :-(

---

### Post by jiyuu0 on 2004-11-30
Ctrl + C
to skip the boot-up service

For more info:
[http://kitech.com.my/ubuntu/4.10/index.html](http://kitech.com.my/ubuntu/4.10/index.html)

---

### Post by kris kincaid on 2004-11-30
jiyuu0, thanks for the reply. It helped me figure out one part of the puzzle!!

For anybody else having a similar problem, here is what I did. As Ubuntu loaded, I waited until the "starting hotplug subsystem" came up then I hit Ctrl C several times. This allowed the system to continue to boot. Once I had logged in, I could not connect to the internet. I have no idea why. I tried to enable the network device in the Network Settings configurator (?) but the check mark would not stay. Just for the heck of it, I typed "/etc/init.d/hotplug restart" in a terminal window to see what would happen. Voila! Now everything works.

I am pretty new to all this, and I apologize for my simple explanation. I hope it helps somebody! :)

---

### Post by cobbe on 2004-11-30
[QUOTE=kris kincaid]I am having a similar problem. My system hangs at "starting hotplug subsystem", but the only problem is I can't get past it. I am unable to boot into my fresh new Ubuntu system.

Any ideas for bypassing it? I have searched this site and I have Googled for an answer. I must be the only one!!  :-([/QUOTE]

I got the same problem, but if i reboot it's work.

/cobbe

---

### Post by chapman2 on 2004-12-02
I think I've solved my problem.  As I've said, after booting a live linux cd I was able to boot into ubuntu. 

 I discovered that booting some live cd's would have no effect.  The cd's that allowed me to boot into ubuntu used an older version of hotplug.  The cd's that wouldn't allow me into ubuntu used version 0.0.20040329.  Ubuntu warty uses version 0.0.20040329-11ub.  I upgraded to hoary which uses 0.0.20040329-16ub.  Now everything seems ok.  I've booted successfully into hoary for the past 2 days now.


 \\:D/

---

### Post by kris kincaid on 2004-12-02
Chapman2,

Thanks! Upgrading hotplug has solved my problem also.

Man these forums are great!   =D>

---

