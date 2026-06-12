---
title: "Diagnosing disk IO spike causing server freeze"
date: 2013-09-04
forum: General Help
---

### Post by matthew1001 on 2013-09-04
I have a small low power server running Ubuntu to manage a few home automation bits and pieces. Every so often something is completely thrashing the hard disk (normally I notice that the hard disk LED is flashing permanently or that I can't SSH into it) to the point where the box is completely unresponsive.

The only resolution seems to be to restart the machine, after which everything goes back to normal.

The first time I hit the problem I decided to install sar to record some system activity that I could look back at after reboot, and also munin with a few plugins enabled (vmstat, iostat etc.) However, I had to disable munin as that just seemed to be too heavyweight for my small server with its slow processor.

Last night at midnight the hard disk started thrashing again. There's nothing in syslog to suggest what process started at midnight to cause the problem. However, looking at the historical data in sar it's clear that something started at midnight that caused the system load to spike massively. Here's the tail of the log file leading up to midnight (I used "sar -q -f /var/log/sysstat/sa03")

```
22:25:01            0       228      0.45      0.32      0.31
22:35:01            0       222      0.01      0.17      0.28
22:45:02            0       228      0.16      0.13      0.20
22:55:02            0       228      0.19      0.14      0.18
23:05:01            0       222      0.12      0.17      0.21
23:15:01            0       228      0.07      0.10      0.16
23:25:02            0       222      0.05      0.26      0.26
23:35:01            0       228      0.02      0.18      0.27
23:45:03            0       228      0.09      0.20      0.24
23:55:01            1       222      0.22      0.15      0.20
23:59:01            0       228      0.04      0.15      0.20
00:00:01            2       224      0.02      0.12      0.19
Average:            0       226      0.27      0.29      0.31
```

and here's the beginning of the file from the following day ("sar -q -f /var/log/sysstat/sa04"):

```
00:00:01      runq-sz  plist-sz   ldavg-1   ldavg-5  ldavg-15
00:05:49            0       226     13.48      7.35      3.23
00:15:17            0       226     10.45     10.03      6.54
00:26:29            0       232     24.08     20.94     13.92
00:36:41            0       231     27.27     24.08     18.65
00:46:42            0       231     26.77     23.64     20.68
00:56:55            1       231     25.19     24.91     22.71
01:07:14            0       234     25.80     24.44     23.33
01:16:38            0       231     25.66     24.08     23.55
01:27:07            0       236     26.37     24.51     23.95
01:36:42            0       236     25.20     23.61     23.54
01:46:42            0       236     25.03     24.64     24.01
01:56:17            0       237     25.66     23.82     23.69
02:06:31            0       238     26.15     25.59     24.68
02:16:51            0       235     26.17     25.45     24.97
02:26:14            0       241     26.26     26.31     25.61
02:36:16            0       240     25.50     26.50     26.13
```

As you can see, the load averages for 1, 5 and 15 minutes go straight up after midnight.

Any suggestions as to how to find out what process is going crazy and causing the system to lock up?

Thanks in advance :)

---

### Post by TheFu on 2013-09-04
/etc/cron.daily

The only time I've seen a Linux machine appear to lock up was with USB storage. Seems there is/was a queuing issue with USB. I see that with my current USB3 storage too.

When this stuff happens, check dmessage and the logs. See my signature for how.

---

### Post by matthew1001 on 2013-09-05
Thanks for the advice, I did have a look for anything obvious in cron.daily but couldn't see an obvious candidate that could be causing the problem. I also checked dmessage and the logs but again there were no stand-out entries at around that timestamp that would suggest something out of the ordinary happening.

I've set up a script to dump some output from iotop every few minutes now so next time it happens that might help me get to the bottom of it.

Cheers for the pointers.

---

### Post by TheFu on 2013-09-05
That will show the io stuff, but not the CPU. 

Just a thought.  Shoving the output from **top** into a file every minute is a poor-man's way to track which processes are using CPU. ** sleep 30 ; top -b -n 1 > outfile.txt**  This way you avoid the monitoring at an exact minute ... when other things are likely to run.

I use a monitoring tool called SysUsage to track current and historical performance. There may be other times when this happens that you just aren't noticing. Having the data is better than not having it.  On a low power system - I'm thinking ARM with a USB disk - constant monitoring might suck 50% of the system resources. Not good.  Of course, there are other monitoring tools/systems like cacti, nagios, opennms ... 

I like the iostat and sar stuff, but adding top output might make it all fit together easier?

---

### Post by matt_symes on 2013-09-05
Hi

Check updatedb from (m)locate.

This has caused my hard drive to thrash in the past and is run from cron.

```
/etc/cron.daily/mlocate
/etc/cron.daily/locate
```

Kind regards

---

