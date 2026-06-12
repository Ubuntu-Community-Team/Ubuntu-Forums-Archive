---
title: "Unresponsive server at times"
date: 2013-11-08
forum: General Help
---

### Post by Sapph1r3 on 2013-11-08
Hi There,
We have a webserver running Ubuntu 11.04.
From time to time we find that we lose connectivity to it.
We receive replies from ping attempts, however websites are unreachable and we are unable to connect via webmin.
Are there any suggestions on where we could start looking or any ideas what the problem might be?
This server has been running for years and only recently started displaying this behaviour.
Please let me know if any further information is required.
Thanks,
Sapphire

Edit: noticed on the motherboard that one of the capacitors is starting to swell a bit. (don't know how to insert image on forum)

---

### Post by tgalati4 on 2013-11-08
Install *htop* and monitor the CPU load.  Perhaps the machine is too busy to serve web pages.

---

### Post by Sapph1r3 on 2013-11-11
This server is administered remotely via webmin.
Would this application work through webmin as I see it works through terminal?
It has been running as websites for a few years now, and only recently been giving this issue.
The problem appeared to have improved when we removed the SSL option, but still exists.

---

### Post by Sapph1r3 on 2013-11-21
Please can anyone help with this...the server has become unresponsive yet again.
The only way to get it back is to do a hard reboot, which I don't like...
Are there any places I can start looking to pin point the problem?
I am new to Ubuntu/Linux and only have the basic skills in how to navigate in the system.
Any advice would be greatly appreciated as this situation is very strange to me.
It ran fine for years without any problems.
One of the changes that was made before the problem started was that someone added SSL (https) then the problems started with this box and another one we newly built.
Upon removing the https from both boxes, the new one has been stable for months, while the webserver will give occasional issues.
It will be stable for a month or a few weeks the be unreachable.

---

### Post by tgalati4 on 2013-11-21
Check the log files in /var/log and post any relevant error messages.  Don't use webmin, log into your server with *ssh* and run *htop* then report what the CPU loads are.

After a server has been running for several years, things can get backed up.  Perhaps you are running out of disk space?  Check the size of your log files.  Sometimes they need deleting.

SSL shouldn't cause a problem unless the CPU is too loaded to perform the encryption.

Forget everything else, a swelled capacitor needs attention.  When it bursts or shorts, your system will go down for good.

---

### Post by Sapph1r3 on 2013-11-28
Thanks for the response and sorry for late reply...I thought I'd get an email when a response is posted.
I've copied the log files that were written to either on that day or since then and will be going through those.
I've yet to try the ssh access, but via webmin cpu load averages show as being low. (I will try the ssh when  I am able)
On the capacitor, this issue has been reported but I need to prove that it is not something else before exploring replacement.
Thanks again

---

