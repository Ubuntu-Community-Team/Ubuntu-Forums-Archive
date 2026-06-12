---
title: "Two particular services not starting on boot"
date: 2005-08-10
forum: General Help
---

### Post by pkoufalas on 2005-08-10
G'day all.

I have two services that are not starting on boot.  I can start and stop them without a problem after boot using 

/etc/init.d/service start|stop

The two services are postgresql and wpa_supplicant.

I have checked that the symlinks are in /etc/rc5.d start and stop, and that they point to the right scripts in /etc/init.d

I initially used update-rc.d to move postgresql from S20 and K20 to S23 and K23, but that didn't help.

When shutting down, the kill scripts run, as init complains that the services aren't running.

Your help is appreciated.

Paul.

---

### Post by pkoufalas on 2005-08-10
I will check /etc/rc2.d again, but from memory, I think the Sxx start scripts for both services were in there...I recall being confused by a message related to rc2.d but the following mail list thread explains it.

Extract from [http://lists.samba.org/archive/linux/2005-May/013514.html](http://lists.samba.org/archive/linux/2005-May/013514.html)

And, don't forget that in Debian (from which Ubuntu is derived),
unlike almost every other flavour of Linux/Unix, almost all services
are started out of rc2.d (ie. the default initial run-level is 2 -
even for full graphical environment).

RedHat (and Fedora) seem to use the more usual Unixy run-level 3
for standard startup (and less usual 5 for graphical startup).

Debian have to do things "the Debian way" - just because.

Cheers,

Bob Edwards.

---

### Post by pkoufalas on 2005-08-11
I have checked /etc/rc2.d, and the symlinks are all in there.

I installed BUM and played with that, as it's not recommended to use update-rc.d for manipulating /etc/rc*.d, but that didn't help with my problem.

dmesg output doesn't even mention postgresql and wpa_supplicant.

Bit stumped here, I would really appreciate some help from someone familiar with sysv and init...

---

### Post by pkoufalas on 2005-08-21
Fixed.

p3scan was not being put into the background. So the startup scripts did not progress further than S20p3scan!!! I only put 2 and 2 together when I looked at the running processes

ps aux | grep p3

and switched to a virtual console CTRL-ALT-F1. I thought it was weird that I could see all of the p3scan daemon messages. I killed the S20p3scan process and the remaining startup scripts completed, leading to a login prompt on the virtual console.

To fix things, I edit the /etc/init.d/p3scan script to include 
--background --make-pidfile
for start-stop-daemon in the "start" section.

---

