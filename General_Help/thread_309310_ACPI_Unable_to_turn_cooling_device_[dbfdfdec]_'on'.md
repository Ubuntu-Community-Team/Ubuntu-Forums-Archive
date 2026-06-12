---
title: "ACPI: Unable to turn cooling device [dbfdfdec] 'on'"
date: 2006-11-29
forum: General Help
---

### Post by bobosity on 2006-11-29
I've seen this asked before but not answered.

I'm getting the line:

ACPI: Unable to turn cooling device [dbfdfdec] 'on'

written to my syslog every six seconds. 

I've tried disabling ACPI. I'm not sure I did it right but it didn't help. A google search found this question being asked in other distro forums but no answers.

Search google code search for "Unable to turn cooling device" and you'll see that this error comes from a file called thermal.c. In there the error is related to getting a signal concerning the fan.

My system is fine. The fan works. I think this thing is trying to do something to a laptop and I have a desktop.

Oh yeah... This is on 6.10 on an AMD chip.


How do I make it stop?

---

### Post by bobosity on 2006-11-29
Hmmmmm.....

For those who don't know if this applies to you, open a terminal and type 'dmesg'.

I'd like to know if other people have this problem.

---

### Post by prensing on 2006-12-02
I see this too. I have previously notice it as well when I was running a Fedora kernel (on the same machine). The Fedora 2.6.17 kernel had the problem but an older one (pre 17, don't remember exact version) did not.

---

### Post by bl8n8r on 2006-12-16
Looks like booting with the 2.6.15-26-386 kernel takes care of the ACPI messages

# no messages
root@ubuntu:/# tail -10 /var/log/messages | grep ACPI
root@ubuntu:/#  

# cooling mode still active
root@ubuntu:/# cat /proc/acpi/thermal_zone/THRM/cooling_mode
cooling mode:   active

I'm going to change "default 1" in /boot/grub/menu.lst and just use 2.6.15

---

### Post by Papou on 2007-01-03
Hi bobosity,

I got the same message in log files every 6 sec.
It appears after upgrade from dapper to edgy.
I try many things arround acpi,acpid,apmd .... but never fix it.

I'm running AMD Athlon XP into HP pavilion ( Desktop ).

---

### Post by Papou on 2007-01-03
On my system, the message can be stopped by removing thermal module ( sudo modprobe -r  thermal ) ... but this command must be resend after each reboot ( even if thermal is not loaded .. ).

---

### Post by matala on 2007-01-08
I'm the same problem.
I have Edgy on AMD Athlon XP with Compaq Presario ( Desktop ).
Also for me the message can be stopped by removing thermal module ( sudo modprobe -r thermal ) ... but this command must be resend after each reboot. :confused:

---

### Post by absol_of_doom on 2007-03-10
very odd. i have a compaq with AMD XP processor and i cannot even boot ubuntu. when i run recovery mode, it says that same error message. however, windows XP runs fine. (i have it on dual-boot)

---

### Post by KarmaticStylee on 2007-08-22
*(I just installed Ubuntu for the first time and this is my first linux install so I am brand new to all of this.)*

I am getting the same problem, error is displayed in the log every 6 seconds.  My fans are running fine and my computer is not overheating.  I only noticed the problem because I was toying around with Ubuntu and when I went to the system log I noticed the error being spammed.  Aside from an extremely large log there is nothing wrong but I'd like it if I could stop it from happening somehow.


Exact error:
Aug 22 09:18:39 eric-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)

I'm running on a desktop with 3200+ AMD Athlon XP

EDIT/UPDATE: 
I found this: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550)
It suggested to try powersaved so I installed that.  I really don't know exactly how to use it though and the problem is still occurring.

---

