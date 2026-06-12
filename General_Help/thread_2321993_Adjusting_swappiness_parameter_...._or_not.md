---
title: "Adjusting swappiness parameter .... or not"
date: 2016-04-25
forum: General Help
---

### Post by pfeiffep on 2016-04-25
Ever since I first installed Ubuntu I've added a  line [vm.swappiness=10] in /etc/sysctl.conf to adjust the frequency the  system MIGHT look to use swap. 
  Thus far in UM 16 fresh install I haven't inserted this line. I've  noticed the UM 16 seems more responsive than Ubuntu 14 {using gnome  flash back] on the same hardware. 

So my question: Is there a **log** that contains information about swap or memory usage over time? I know I can generate my own with vmstat na 5 >> path/some.log

  My thought is to apply this *tweak* after I've examined appropriate data.

---

### Post by pfeiffep on 2016-04-28
bump

---

### Post by QDR06VV9 on 2016-04-28
I think [B]" /proc/meminfo "
[/B]Contains memory usage information for both physical memory and swap[B].
[/B]

---

### Post by nerdtron on 2016-04-28
If you installed the sysstat package you should have the sar utility that reports the system statistics (CPU, ram, swap, disk, etc.) to a log file in /var/log/sa

The reports are updated (by default) every 10 minutes and are rotated ever midnight.
Showing the swap report for today (on my test server)
```

[root@goddard httpd]# sar -S
Linux 3.10.0-327.13.1.el7.x86_64 (goddard)    04/29/2016      _x86_64_        (1 CPU)

12:00:01 AM kbswpfree kbswpused  %swpused  kbswpcad   %swpcad
12:05:01 AM   1992948     55048      2.69      5016      9.11
12:10:01 AM   1992948     55048      2.69      5016      9.11
12:15:01 AM   1992948     55048      2.69      5016      9.11
12:20:01 AM   1992948     55048      2.69      5016      9.11
12:25:01 AM   1992948     55048      2.69      5016      9.11
12:30:01 AM   1992948     55048      2.69      5016      9.11
12:35:01 AM   1992948     55048      2.69      5016      9.11
12:40:01 AM   1992948     55048      2.69      5016      9.11
12:45:01 AM   1992948     55048      2.69      5016      9.11
12:50:01 AM   1992948     55048      2.69      5016      9.11
12:55:01 AM   1992948     55048      2.69      5016      9.11
01:00:01 AM   1992948     55048      2.69      5016      9.11
01:05:01 AM   1992928     55068      2.69      4412      8.01
01:10:01 AM   1992928     55068      2.69      4412      8.01
01:15:01 AM   1992928     55068      2.69      4412      8.01
01:20:01 AM   1992928     55068      2.69      4412      8.01
01:25:01 AM   1992928     55068      2.69      4412      8.01
01:30:01 AM   1992928     55068      2.69      4412      8.01
Average:      1992941     55055      2.69      4814      8.74

```

If you want to read the report file from a previous day, just specify the file name:
```
 sar -S -f /var/log/sa/sa29 
```

---

