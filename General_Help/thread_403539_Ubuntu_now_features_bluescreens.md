---
title: "Ubuntu now features bluescreens?"
date: 2007-04-07
forum: General Help
---

### Post by Pitxyoki on 2007-04-07
Ok, now this WAS strange...
I woke up a while ago, and I looked at my Ubuntu PC, just to check how were things with it...
And what did I see? It had restarted in the morning! By itself!
I WAS sleeping when this happened and there is no one else in this house.. So all I can imagine is that something has behaved badly here. Very badly.
I remember when this used happened when I used Windows XP... Usually it came with a nice BSOD and then it happily restarted... But now... What is the excuse?

I'm attaching the syslog... You can see what happened (there is apparently no info about it there) at Apr  7 07:03:59 on both logs.

If anyone can give any suggestion on what happened, I would appreciate.

/var/log/kern.log :
```
Apr  7 01:48:12 localhost kernel: [17225710.968000] end_request: I/O error, dev fd0, sector 0
Apr  7 01:48:12 localhost kernel: [17225711.000000] end_request: I/O error, dev fd0, sector 0
Apr  7 07:03:59 localhost kernel: Inspecting /boot/System.map-2.6.15-28-686
Apr  7 07:03:59 localhost kernel: Loaded 23277 symbols from /boot/System.map-2.6.15-28-686.
Apr  7 07:03:59 localhost kernel: Symbols match kernel version 2.6.15.
Apr  7 07:03:59 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Apr  7 07:03:59 localhost kernel: [17179569.184000] Linux version 2.6.15-28-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Feb 1 16:14:07 UTC 2007
```

/var/log/syslog.0 :
```
Apr  7 06:46:24 localhost ntpd[5120]: synchronized to 194.117.9.130, stratum 2
Apr  7 06:46:57 localhost ntpd[5120]: time reset -0.802844 s
Apr  7 06:52:14 localhost ntpd[5120]: synchronized to 194.117.9.136, stratum 2
Apr  7 07:03:59 localhost syslogd 1.4.1#17ubuntu7: restart.
Apr  7 07:03:59 localhost kernel: Inspecting /boot/System.map-2.6.15-28-686
Apr  7 07:03:59 localhost kernel: Loaded 23277 symbols from /boot/System.map-2.6.15-28-686.
Apr  7 07:03:59 localhost kernel: Symbols match kernel version 2.6.15.
Apr  7 07:03:59 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Apr  7 07:03:59 localhost kernel: [17179569.184000] Linux version 2.6.15-28-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Feb 1 16:14:07 UTC 2007
```

[EDIT]
I have been using Ubuntu Dapper since September 2006, and this was the first time something like this has happened. It had never restarted without any apparent reason before...
[/EDIT]

---

### Post by alkat on 2007-04-07
Couldn't it simply be a temporary power outage? It happened to me a couple of times...

Ale.

---

### Post by Lucifiel on 2007-04-07
From /var/log/kern.log:

fd0 = floppy disk.
It seems you've an I/O error for your floppy drive: likely means a problem with your floppy drive or floppy disk. Not very sure about the rest of the messages.

---

### Post by Lucifiel on 2007-04-07
From /var/log/kern.log:

fd0 = floppy disk.
It seems you've an I/O error for your floppy drive: likely means a problem with your floppy drive or floppy disk. Not very sure about the rest of the mess.

---

### Post by Pitxyoki on 2007-04-07
The fd0 errors are just from a double click I made over the Floppy Disk icon on Nautilus, by mistake. I was in front of the computer when that happened. Anyway, that was much before the restart.
I'd go more on the power outage... If we ignore that another computer that I have here right behind me, a 133MHz with Debian installed, did not have any issue at all and is running normally.

By the way, this computer is a 3.2GHz Pentium IV, 1GB RAM... Motherboard is an [ASUS P5GDC-V](http://www.asus.com/products4.aspx?l1=3&l2=11&l3=25&model=164&modelmenu=1).  It doesn't seem to be a temperature issue neither (sometimes I have to clean up the fans because they seem to accumulate a lot of dust from time to time), as the sensors applet reports everything is as it should (and at that time in the morning it was surely not so much hot that could cause malfunction to the computer).

---

### Post by Lucifiel on 2007-04-07
Although this is a guess, perhaps some software or process is actually restarting your pc? 

Also, "No module symbols loaded - kernel modules not enabled." doesn't look good. I'd suggest googling by pasting that entire sentence in, without the quotes and seeing what comes up in the results.

---

### Post by Pitxyoki on 2007-04-07
Can you please check if you do not have the same message on your kern.log? It seems to me this is a normal message:
[http://www.linuxquestions.org/questions/showthread.php?p=895954#post895954](http://www.linuxquestions.org/questions/showthread.php?p=895954#post895954)
[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-03/4294.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-03/4294.html)

As I said, everything seems to be working fine... Except for that mysterious restart.
lsmod prints the modules loaded into the kernel correctly... 
```
$ lsmod | wc -l
104
$
```

---

