---
title: "System intermittently hangs"
date: 2013-12-19
forum: General Help
---

### Post by fortec on 2013-12-19
I am having issues with my Ubuntu system intermittently hanging. It has been doing it for several months and I have tried a lot of things from teh forums but nothing has worked. Updated & downgraded NVidia drivers, changed bios settings, even tried reinstalling.Still just intermittently hangs. Sometimes it is just lightdm/gnome (I can still SSH into the system), other times it is a hard hang and only a power reset works.

I need help in determing root cause because obviously I am missing something. I can't seem to find in the logs anything that points to the problem.

Below is the OS/window manager info:

uname -a output:
Linux gorkon 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


lsb_release -a output: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


gnome-shell --version output: 
GNOME Shell 3.8.4

Attached is the lspci, lsusb and lshw outputs, as well as the kern.log and dmesg output.

In the kern.log it shows WHEN it hangs but I dont see anything that points to WHY. The timestamps of the hangs I just experienced today are: Dec 19 14:14:55 & Dec 19 15:05:09 (second time I was just closing gedit when it froze).

Any and all help will be appreciated. Where else should I look? Do you see something in the logs that I am missing? etc...

THANKS!

---

### Post by fortec on 2013-12-21
Any ideas or advice? Anyone? Bueller? :)

---

### Post by PaulBx on 2013-12-22
Sounds like a hardware problem to me (due to the intermittent nature). Have you tried another OS on the machine, before assuming Ubuntu has anything to do with it? Try running Puppy Linux from a CD for a while to see if that hangs too. How often does it hang anyway?

---

### Post by tlwest on 2014-01-31
It's certainly possible that it is a hardware problem, but there seem to be many people with hardware problems. I am seeing similar hard crashes, with nothing untoward in the log files, and I just got off the phone with my daughter who is having similar problems. We all began noticing this some months ago, about 12.04 LTS? There is an open bug report, but there doesn't seem to be a pattern except that linux has gotten unstable in 2013. Video drivers, anyone? Any suggestions for a systemic data collection process?

---

### Post by fortec on 2014-01-31
I am thinking about just going back to a pre-12.04 LTS release. These intermittent hangs are getting annoying and I don't know where else to look since the logs are pretty much useless.

---

