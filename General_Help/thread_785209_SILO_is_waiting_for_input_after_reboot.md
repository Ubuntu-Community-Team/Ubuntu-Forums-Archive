---
title: "SILO is waiting for input after reboot"
date: 2008-05-07
forum: General Help
---

### Post by stovocor on 2008-05-07
Hello!

I just installed Ubuntu 7.10 (Server) on a T2000. After the installation the system did not boot properly until I set boot-device to "disk" and boot-command to "boot disk Linux" at the ok-prompt.

Unfortunately this only works when I am doing a "reset" from ALOM. After running "reboot" in my Ubuntu installation, the boot-command is set to "boot" and the system stops at the SILO prompt. There I have to press Enter to boot the system.

My question is: How do I configure the nvram or Ubuntu so I can reboot with the reboot-command?

TIA
 Stephan

---

### Post by mecki on 2008-05-08
hello stephan
this has nothing to do with the nvram.if you reach the silo prompt the system is already booting from disk, else your system would stop at the obp. so just wait some more seconds. On my enterprise 3000 i have to wait 30s then silo continues the boot process. Somewhere you can configure the waiting time for silo, but I don't know exactly where.

bye
Michael

---

### Post by stovocor on 2008-05-08
> **mecki said:**
> this has nothing to do with the nvram.if you reach the silo prompt the system is already booting from disk, else your system would stop at the obp. so just wait some more seconds.
What confuses me is the fact that the timeout does not appear if I do a "reset" from the ALOM. The boot-command seems different then.

> On my enterprise 3000 i have to wait 30s then silo continues the boot process. Somewhere you can configure the waiting time for silo, but I don't know exactly where.
The file is /boot/silo.conf, but even after waiting double the time specified there my system does not boot.

---

### Post by bgervasi on 2008-07-23
stovocor,

I see you running ubuntu on a t2000,  I to have the same problem on silo.  But my question to you is that, I have 8GB on my t2000 but in ubuntu in /proc/meminfo, it shows 1GB.  I opened up a ticket with sun telling them about this problem and they are throwing the ball to ubuntu.  Only that the showfru is actually showing 8GB but the OBP banner shows 1GB, which is before the silo.

----
Sun Fire T200, No Keyboard
Copyright 2007 Sun Microsystems, Inc.  All rights reserved.
OpenBoot 4.27.7, 1024 MB memory available, Serial #6xxxxxx8.
Ethernet address 0:14:4f:aa:xx:xx, Host ID: 83xxxxxx6.
---

Can you tell me if you are having the same problem?

Thanks

---

### Post by stovocor on 2008-08-11
> **bgervasi said:**
> 
I see you running ubuntu on a t2000,  I to have the same problem on silo.  But my question to you is that, I have 8GB on my t2000 but in ubuntu in /proc/meminfo, it shows 1GB.
[...]
Can you tell me if you are having the same problem?

Sorry, but here the total 8GB seem to be detected:

$ cat /proc/meminfo
MemTotal:      8276856 k

---

### Post by jormabe1 on 2008-09-13
[wedding dresses](http://www.jormabridal.com), [wedding dress](http://www.jormabridal.com), [wedding gowns](http://www.jormabridal.com), [bridesmaid dresses](http://www.jormabridal.com/gown.html)

---

### Post by Greettat on 2008-10-01
We should never remember the benefits we have offered nor forget the favor received.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

