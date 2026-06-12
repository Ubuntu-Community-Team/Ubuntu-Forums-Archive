---
title: "How to run ntpdate, then hwclock at boot"
date: 2007-12-16
forum: General Help
---

### Post by movrshakr on 2007-12-16
I have ntp set up on my machine (there is a minor problem with it, but that will be another thread).

I realized though, that ntp will fail (exit) if the system hardware clock is >1000 seconds different from the ntp-gathered time.  This can happen if you have a bad clock, or computer is off for months, or cmos battery is dead, or idiot manually set the hw clock wrong, etc.  So I began searching for a way to prevent  this, and found it at 
[http://nixtechnica.blogspot.com/2006/09/how-to-synchronize-time-with-ntp.html](http://nixtechnica.blogspot.com/2006/09/how-to-synchronize-time-with-ntp.html)
.
I implemented this: 
a. Created /etc/init.d/ntpdate file which contains: 
#! /bin/sh
echo "Synchronizing system time with Ubuntu Servers..."
ntpdate ntp.ubuntu.com
echo "Setting hardware clock to updated time..."
hwclock --systohc
.
b. Then this : sudo chmod 700 /etc/init.d/ntpdate
. 
c. Then this: sudo update-rc.d ntpdate defaults 90 

So this "kind of" works, except for the following problem which is my question for how to fix...

When I boot, and look at syslog, it says that ntpdate failed because the port was in use.  
----------------SYSLOG CLIP --------------------------
Dec 16 13:38:46 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 16 13:38:46 maximus ntpd[4940]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 16 13:38:46 maximus ntpd[4957]: precision = 1.000 usec
Dec 16 13:38:47 maximus kernel: [   37.618402] Failure registering capabilities with primary security module.
Dec 16 13:38:47 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 16 13:38:47 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 16 13:38:47 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 16 13:38:47 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 16 13:38:47 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 16 13:38:47 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 16 13:38:47 maximus NetworkManager: <info>  Activation (eth0) started... 
,
,
Dec 16 13:38:57 maximus NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Dec 16 13:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 16 13:38:57 maximus ntpdate[5304]: the NTP socket is in use, exiting
---------------- END SYSLOG CLIP --------------------------
Bottom line: how do I make the above solution work, or does someone have a different guaranteed solution to, at boot, run ntpdate (to set current system time right), then run "hwclock --systohc" to write a good time into the bios clock?
.
Sorry to be a little long, but I wanted to be clear.

---

### Post by movrshakr on 2008-01-08
SOLVED:

and for completeness, see the solution that worked here 


[http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr](http://ubuntuforums.org/showthread.php?t=647559&highlight=movrshakr)

Read all of it.  It is long.  Solution is in the last 10 or so posts.

---

