---
title: "System rebooting unexpectedly on &quot;signal 15&quot;"
date: 2007-04-01
forum: General Help
---

### Post by pappo on 2007-04-01
My system is as follows:

$ lspci|grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JP [Radeon X800XT]

$ uname -a
Linux Ubuntu-gamer 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

I just installed the ATI drivers ( ati-driver-installer-8.32.5-x86.x86_64.run) from the Linux Format LXFDVD90 DVD.

When I come back to my system,in the morning, I keep finding it back at the login screen, which means it rebooted itself sometime during the night.

I looked at some of the log files and found this:
$ sudo cat /var/log/messages|grep signal
Mar 31 07:40:07 Ubuntu-gamer exiting on signal 15
Mar 31 10:18:48 Ubuntu-gamer gconfd (pappo-5404): Received signal 15, shutting down cleanly
Mar 31 10:19:13 Ubuntu-gamer exiting on signal 15
Mar 31 18:19:21 Ubuntu-gamer exiting on signal 15
Mar 31 19:07:06 Ubuntu-gamer gconfd (pappo-5246): Received signal 15, shutting down cleanly
Apr  1 07:37:59 Ubuntu-gamer exiting on signal 15

The system runs about 10 hours and then restarts.

My questions are:
1.  What other log files might help me figure out what is causing the "signal 15" reboots ?
2.  How do I return to my original ATI drivers ?  Can I just recopy the original xorg.conf file back in ?

Regards,
pappo

---

### Post by kinson on 2007-04-05
I think I'm having a similar problem. It hasn't happened before. But it happened twice today in the span of a couple of hours.

My /var/log/syslog is as follows(part of it):
```
Apr  5 07:38:34 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr  5 07:38:34 localhost anacron[1716]: Job `cron.daily' terminated
Apr  5 07:38:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr  5 07:38:56 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Apr  5 07:39:17 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 07:39:23 localhost dhclient: No DHCPOFFERS received.
Apr  5 07:39:23 localhost dhclient: No working leases in persistent database - sleeping.
Apr  5 07:40:06 localhost anacron[1716]: Job `cron.weekly' started
Apr  5 07:40:06 localhost anacron[2296]: Updated timestamp for job `cron.weekly' to 2007-04-05
Apr  5 07:40:07 localhost exiting on signal 15
Apr  5 07:40:08 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr  5 07:40:08 localhost anacron[1716]: Job `cron.weekly' terminated
Apr  5 07:40:08 localhost anacron[1716]: Normal exit (2 jobs run)
Apr  5 07:43:55 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 07:44:01 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr  5 07:44:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 07:44:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 07:44:33 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Apr  5 07:44:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:44:56 localhost dhclient: No DHCPOFFERS received.
Apr  5 07:44:56 localhost dhclient: No working leases in persistent database - sleeping.
Apr  5 07:50:00 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:50:08 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr  5 07:50:18 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr  5 07:50:32 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr  5 07:50:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr  5 07:50:56 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr  5 07:51:01 localhost dhclient: No DHCPOFFERS received.
Apr  5 07:51:01 localhost dhclient: No working leases in persistent database - sleeping.
Apr  5 07:53:41 localhost shutdown[2950]: shutting down for system halt
Apr  5 07:53:41 localhost init: Switching to runlevel: 0
Apr  5 07:53:43 localhost gconfd (kinson-5104): Received signal 15, shutting down cleanly
Apr  5 07:53:43 localhost gconfd (kinson-5104): Exiting
Apr  5 07:53:43 localhost gconfd (kinson-2987): starting (version 2.14.0), pid 2987 user 'kinson'
Apr  5 07:53:43 localhost gconfd (kinson-2987): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr  5 07:53:43 localhost gconfd (kinson-2987): Resolved address "xml:readwrite:/home/kinson/.gconf" to a writable configuration source at position 1
Apr  5 07:53:43 localhost gconfd (kinson-2987): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr  5 07:53:43 localhost gconfd (kinson-2987): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr  5 07:53:43 localhost gconfd (kinson-2987): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr  5 07:53:45 localhost kernel: [17221578.920000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr  5 07:53:45 localhost kernel: [17221578.920000] apm: disabled on user request.
Apr  5 07:53:51 localhost sdpd[4862]: terminating...   
Apr  5 07:53:51 localhost hcid[4858]: Exit.
Apr  5 07:53:51 localhost kernel: Kernel logging (proc) stopped.
Apr  5 07:53:51 localhost kernel: Kernel log daemon terminating.
Apr  5 07:53:51 localhost exiting on signal 15
Apr  5 20:03:53 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr  5 20:03:53 localhost dhclient: bound to 192.168.1.3 -- renewal in 971709014 seconds.
Apr  5 20:03:53 localhost kernel: Inspecting /boot/System.map-2.6.15-28-386
Apr  5 20:03:54 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr  5 20:03:54 localhost kernel: Loaded 23072 symbols from /boot/System.map-2.6.15-28-386.
Apr  5 20:03:54 localhost kernel: Symbols match kernel version 2.6.15.
Apr  5 20:03:54 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Apr  5 20:03:54 localhost kernel: [17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007

```

I'm running a Azureus, rhythmbox, gaim, firefox at that time. Nothing much else.

I see a couple of those "signal 15" entries.. :(

any ideas guys? :(

Cheers,
Kinson

---

### Post by rozojc on 2007-04-05
I am too having the same problem... I am just trying out my new laptop, it hand't happened before, but now it's becoming a common thing... The only new things I've done is using Azureus, but I'm not sure if that has anything to do with it...

I noticed that whoever started this thread started it 4 days ago, really, is there NO ONE who can give a little bit of help?

ps/
Apr  5 13:30:40 Maxwell gconfd (rozojc-10083): Received signal 15, shutting down cleanly
Apr  5 13:30:41 Maxwell gconfd (rozojc-10083): Exiting

---

### Post by rozojc on 2007-04-05
I just read that this could actually be a Gnome 2.16 bug... [https://launchpad.net/gnome-session/+bug/65971/comments/6](https://launchpad.net/gnome-session/+bug/65971/comments/6)


Any ideas? I mean, I could, install kubuntu desktop... but I installed ubuntu cause I prefer Gnome... is this really a bug? Any1 knows how to handle this?

---

### Post by pappo on 2007-04-05
I searched the forums and found that back in 2005 and 2006 this occurred alot.  Some people fixed it by turning off anacron and cron, but that leads to a lot of problems with tasks not starting when you need them.
I ran Ubuntu Hoary before and never had a problem.  It seems to be an issue with Ubuntu 6.06 and 6.10 versions.
I got fed up with coming back to my PC and finding it had reset back to the login screen, so I removed Ubuntu and am now trying PCLinuxOS and OpenSUSE 10.2 

I will keep checking back to see if it gets fixed, but until then it makes Ubuntu too annoying to use.

Good luck to everyone.

---

### Post by kinson on 2007-04-05
Funny thing is that it only started happening yesterday. I don't know what happened :( I can't remember whether I downloaded any updates from the ubuntu auto updates. But it really is irritating, cause I use my pc for an alarm clock.

It kept rebooting on me, so obviously I had nothing to wake me up :( It did it twice within the space of 20 mins yesterday...so its quite worrying

I'm hoping for a solution to this soon, and I'm also waiting for Feisty. So hopefully its released soon.

Cheers,
Kinson

---

### Post by kinson on 2007-04-06
I think I might have solved my problem. It wasn't restarting, but actually logging me out of session(or whatever its called).

It was my graphics driver that suddenly went beserk.(It was working fine before). The moment I tried to go change my screen saver, or start glxgears, it would kick me back to the login screen.

My guess is that my "reboots" were actually the screensaver kicking it, then mucking up and sending me back to the login screen.

So once I reinstalled the drivers(though [envy]("http://www.albertomilone.com/nvidia_scripts1.html")) then its back to normal(I hope).

Hopefully it doesn't happen again. Hopefully this can help someone solve the problem too :)

Cheers,
Kinson

---

### Post by babarhaq on 2007-04-13
Hi all

Guys I had the same problem on ubuntu 6.10. It rebooted every now and then with signal 15. Reading from this thread I had the hint that its something to do with screensaver. All I did was go to System -> Perference -> Screensave and selected none. It fixed the problem at least it seems like.

Babar

---

### Post by holyskeleton on 2007-07-22
same with feisty fawn. maybe it has something to do with powernowd.

---

### Post by gray380 on 2007-07-23
Hi there!

Several days ago I had a same problem. I use the Ubuntu since version 5.10. Since then I have used only updates.

The suspected records in /var/log/messages looks like this:

> Jul 23 09:58:27 linuxbox syslogd 1.4.1#20ubuntu4: restart.

Add. info:

> $ uname -a
Linux linuxbox 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

$ cat /etc/issue
Ubuntu 7.04 \n \l


Any assistance?

brg,
Serhiy.

---

### Post by gray380 on 2007-07-25
That was  a hardware problem.

---

