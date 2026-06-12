---
title: "Server stops responding for several minutes"
date: 2018-05-14
forum: General Help
---

### Post by futuretense on 2018-05-14
I’m running Ubuntu on a ODROID C2 single board computer 


```
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 3.14.79-117 aarch64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage
Last login: Thu May 10 02:00:02 2018 from 172.16.68.56
root@odroid64:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.4 LTS"
root@odroid64:~#
```
The server runs PiHole,  which provides DNS and ad blocking for my entire network. My router assigns this as the DNS server for all DHCP clients. The server also runs OpenVPN, but there are no connections open when I am having the following issue:


Several times a day, for a couple of minutes I can’t browse the internet.  I quickly discovered I couldn’t ping any sites, but I could ping with IP address, such as Google’s DNS server 8.8.4.4.   I figured there was a problem with my PiHole DNS server so I tried a SCP terminal connection, but that wouldn’t start.  Then I tried pinging the server itself, and that wasn’t responding.  After a few minutes I was about to go power cycle the unit, but then the ping started responding, and everything was working correctly again.  I’ve no idea what happened.  Maybe the computer crashed and rebooted, maybe a service crashed and restarted, it’s a mystery.  This has happened to me several times in the last couple of days.


Is there a log file somewhere that I can examine the time period where things stopped and started working again that might give me a clue as to why the server is non-responsive?  I’m running this headless, but I suppose I could plug in something to the HDMI port and see what it looks like when it goes down.  Are there log files where I might be able to upload them and give the times I’m having the issue so someone more knowledgeable than I poke through them?

---

### Post by papibe on 2018-05-14
Hi  futuretense.

Since scp fails to start, I'd would look at the system logs at /var/log, particularly syslog.

I would create a ssh connection from another machine, setup a tmux session, and run:
```
tail -f /var/log/syslog
```
and monitor any system message remotely.

Hope it helps. Let us know how it goes.
Regards.
 
BTW, I'm using pi-hole in a docker container for my home LAN ;)

---

