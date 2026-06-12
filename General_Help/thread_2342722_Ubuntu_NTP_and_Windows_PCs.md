---
title: "Ubuntu NTP and Windows PCs"
date: 2016-11-09
forum: General Help
---

### Post by gridlockd on 2016-11-09
Let me preempt my post by saying I don't know much about Linux, I have assumed my environment from a previous sysadmin that is no longer available as a resource.

I have "inherited" a fairly large domain consisting of windows PCs and a PDC/BDC that are Ubuntu 14.04 with Samba on top.  I have realized that there is about a 20-25 min. time discrepancy across the network, and after investigating, I find that none of the windows pcs are syncing time with the anything.  they all show the source as "Local CMOS Clock".  I have gone through all the typical w32tm config options on the workstations with no success.  I did some reading and started working with the ntp.conf on the PDC.  It is syncing time to an outside source, I was able to verify that, but the machines are still not looking at it.  I feel like I am overlooking something small, but I can't figure it out.  Any help is appreciated!

Here is my current ntp.conf, if someone sees something I don't please let me know.

driftfile /var/lib/ntp/ntp.drift

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


server 0.north-america.pool.ntp.org
server 1.north-america.pool.ntp.org
server 2.north-america.pool.ntp.org
server 3.north-america.pool.ntp.org

server ntp.ubuntu.com

restrict -4 default kod notrap nomodify nopeer noquery
restrict -6 default kod notrap nomodify nopeer noquery

restrict 127.0.0.1
restrict ::1

broadcast 10.255.255.255

~John

---

### Post by TheFu on 2016-11-09
On Linux, keeping time sychronized is most often accomplished through NTP.  Clients have to be setup to query a server or 5 if you want them to keep time.  I don't think a PDC/BDC has anything to do with that.  There are other methods of time keeping on Unix systems, but those aren't used under normal situations.  NTP is almost always sufficient for non-real-time systems.  IME, it is odd for a clock to be off more than 10msec.

I've had issues with Windows keeping time since around 1995.  For the last 7+ yrs had to point my Windows machines at the internal NTP server here and sync every 15 minutes.  Every hour wasn't sufficient. Every week (the Windows workstation default) was a joke.  Strangely, the exact systems that couldn't keep time running Windows have been millisecond accurate running Linux.

On Windows, in a corporate network, using 100% MSFT solutions, I've seen time off by 5 minutes. That was (is?) the MSFT standard for time keeping. 5 minutes, srsly?!!!!  Anything over a sec off has to be a joke.

BTW, if there is virtualization involved, everything is handled differently.
[http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista](http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista)

In short - tell Windows to use the NTP server.  Should be 2 regedit entries, if my memory is correct.

---

