---
title: "Ubuntu problem when starting up, monitor loses signal"
date: 2017-01-30
forum: General Help
---

### Post by devar on 2017-01-30
A problem has occured on my Ubuntu Server install, suddenly this morning I was unable to contact the server by ping/ssh etc.
I tried rebooting it, still no dice. So I attached a monitor and keyboard to see what was going on, the system is booting OK, grub does it's thing, then all I get is a "Starting up ..." dialog, then the screen just goes to sleep! I'm not sure where to start with this one, nothing I've found online so far quite helps.
It does exactly the same thing if I get grub to load recovery mode, too.
The graphics hardware is simply Intel integrated, and since it should just be CLI (Server) I'm ruling out a sudden graphics driver problem.
Has anyone experienced this one or got any pointers? I'm at a loss.

---

### Post by devar on 2017-01-30
[I've run the boot-repair tool]("http://paste.ubuntu.com/23894243/"), choosing the "most common problems" fix, but that hasn't fixed it. After booting, the system still stops video output and I can't get any response from it remotely or locally from that point.

---

### Post by Keith_Helms on 2017-01-30
Try booting from an install disc/usb and see if that works and has video.  If not, I'd suspect a hardware problem.  If it does work, then check the logfiles such as /var/log/syslog and /var/log/kern.log on the hard drive for errors.

---

### Post by devar on 2017-01-30
Thanks Keith, I am able to get in with any live CD etc. I am ruling out a hardware fault.

After running the boot-repair-tool, I am now able to get into the boot recovery menu and get to a terminal via that, so, something on startup is at fault here.

---

### Post by devar on 2017-01-31
Progress!
I had to reset the console settings to get a viewable console, and add nomodeset to the grub boot config. The system then booted and was actually readable, but it did not pick up a DHCP configuration! (It did, however, if I again booted from failsafe).
If I attempt to renew the IP manually with dhclient or even 'sudo ifup eth0' but was getting permission denied errors even with sudo.

Turns out it was apparmor. This solution marked here [https://askubuntu.com/questions/310619/problems-running-dhclient](https://askubuntu.com/questions/310619/problems-running-dhclient) fixed that.

I did do an apt-get update/upgrade the day prior to this happening so I can only assume something that updated there caused these problems.

---

