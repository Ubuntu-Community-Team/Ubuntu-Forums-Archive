---
title: "Time Issue"
date: 2007-08-03
forum: General Help
---

### Post by dareofficer on 2007-08-03
Hello, I have Fiesty Fawn up and running on my pc.  I have VMWARE running Trixbox in the background.  The program works fine however it gain time??  I can't figure it out, after a terminal fix with date --set and the right time, it shows up right after a few hours it starts to gain time?

---

### Post by apetresc on 2007-08-03
I'm a bit confused by your problem. Is it the virtual machine that is gaining time, or is it the host OS? I have no idea what "trixbox" is, so I can't help you if the problem is showing up there, but if the problem is with Ubuntu's clock, consider running an NTP client and hooking it up to a cron to have it periodically update your clock. Detailed instructions [can be found here]("http://doc.ubuntu.com/ubuntu/serverguide/C/NTP.html"), or easily enough with a bit of Google'ing around. Hope this helps!

---

### Post by dareofficer on 2007-08-04
The problem is with the Virtual Machine.  The program Trixbox, is CentOS operating system.  The time issue is with the CentOS program.  I can drop to terminal only in that, no Gui for the CentOS.

---

### Post by Hikaru79 on 2007-08-04
Ah! I understand your issue now, and with a bit of Googleing around I think I've found a solution. The problem has to do with Linux's frequency scaling (for the sake of power consumption) is confusing VMWare about how fast time is really passing.

A discussion and solution/workaround can be found here: [http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=1591)

Good luck!

---

### Post by dareofficer on 2007-08-05
Thanks, got it going!:)

---

