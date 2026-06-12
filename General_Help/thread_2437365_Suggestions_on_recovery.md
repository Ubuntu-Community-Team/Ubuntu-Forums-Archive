---
title: "Suggestions on recovery"
date: 2020-02-22
forum: General Help
---

### Post by 66corvette on 2020-02-22
Hello,
New to the forums and definitely an Ubuntu novice. Background ... I have a software company that had (key word) two Ubuntu 8.04 servers running happily for many years. I was not the hardware support partner, but he left the business and I had to take over the support functions. We got hit with Ransomware and now those two server will not let you login at the normal boot up prompt. I enter the userid and password and the machine sits for 60 seconds and then issues back the message about "timeout" and I'm back at the login prompt. Even trying a bad password gives me the same response. I can get into single user mode and login and can look around in the directories and I don't see any file that have been encrypted like the way they got my windows boxes. I feel like they may be OK, but this login issue has me concerned. Can anyone offer some things to look for that might affect the normal login process. 

These servers were on a network, but not connected to any of the windows servers (ie no drives mapped, etc).  Of course the hardware person who left was responsible for backup, but I have found out he did not do that at all. This issue is customer affecting and if I can't figure out what the bad guys did to these servers, I will need to scratch them and reload the newest version, but before that, I would need to try and extract all the config info for my Tomcat server, network configs and java setup. I have access to them through a KVM console, so I can spin them up without connecting them to my network. Thanks for any help you could suggest..............

---

### Post by TheFu on 2020-02-22
Dude 8.04 support ended over 5 yrs ago. At this point, for a business, new hardware is necessary to get HW support contracts.  

Backup whatever data you can and move to a supported release.  To do the backup, use any flash boot "try ubuntu" installation.  There is no viable upgrade path anymore.  Fresh install is the only option.

A server over 5 yrs out of support can be hacked. There were some attack vectors using DHCP and DNS a few years ago. No patches were created to 8.04 servers.  Out of support actually means - out of support.

You are passed needing to do a fresh install.  You'll never be able to figure out if an attacker did something or not without versioned backups to the time before and after the hack (if there was any).

Java is vastly different today than it was over 10 yrs ago. Those programs probably won't run without porting.  Most Linux deployments don't use Oracle's version, so whoever does the porting should probably be told to use the non-Oracle Java version.

While you are doing all this infrastructure work, it is time to move the services into a virtual machine.  Much more flexible to use virtualization.  Also, not being tied to any specific hardware means you can setup dev, test, preprod and production on any machines you have lying around. Good for testing out software and OS upgrades BEFORE touching production.  Also, please be certain to setup automatic, daily, "pulled", versioned, backups.  Any place that can be hit by crypto-malware needs all of those features.  Be certain that no clients can directly access the backups on a server and that file sharing is NOT used in any way for the backup solution.

---

