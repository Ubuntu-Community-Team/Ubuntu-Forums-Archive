---
title: "Where do I find the shutdown log messages?"
date: 2008-03-26
forum: General Help
---

### Post by MountainX on 2008-03-26
Is there a log file containing the shutdown messages? My system hangs on shutdown or restart for several minutes and I want to review the messages I see on the screen.

---

### Post by MountainX on 2008-03-27
Maybe I should ask this in the newbie section.

I have looked in /var/log and I cannot tell which log file has the shutdown messages. Thanks.

---

### Post by justleen on 2008-03-27
your almost there then..
/var/log  contains anything that logs... but what if the logging deamon doesnt run you say?
there is a command for that: dmesg
```
dmesg | more
```
or to get the last 100 lines
```
dmesg |tail -100 
```

---

### Post by MountainX on 2008-03-27
Thank you but using dmesg doesn't show the errors I'm seeing on screen at shutdown. Maybe they get replaced by new messages once I reboot... I'm not sure what the buffer size is.

What are my other options for finding these shutdown messages? Thanks.

---

### Post by justleen on 2008-03-28
syslog or syslog.0
do a grep on part of the error in /var/log
```
 grep -Hi <error> /var/log/* 
```
-H to display file name
-i for case insensetive

---

