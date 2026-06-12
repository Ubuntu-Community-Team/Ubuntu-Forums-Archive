---
title: "Ubuntu won't start always??"
date: 2014-02-02
forum: General Help
---

### Post by AlliumPorrum on 2014-02-02
Is there any good tool which could used for solving the problems with starting the Ubuntu 13.10 with Xubuntu desktop?

When I restart my Ubuntu, about 50% of times it just won't start; all I get is a blank black screen with non-blinking cursor on the upper left corner. Then if I reboot it, it might start just fine to Xubuntu desktop, or maybe not... 

I noob with Linux, so I have no idea how could I solve this problem. Any hints..?

---

### Post by TheFu on 2014-02-02
Review the log files. They are fairly comprehensive.  Most programs support turning up the amount of logging as well.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) should work regardless of Linux used - desktop/server doesn't matter.

---

### Post by AlliumPorrum on 2014-02-03
Did not work: 

~/Downloads$ sudo egrep -i &#8216;error|warning&#8217; /var/log/*log
warning&#8217;: command not found

[2]+  Stopped                 sudo egrep -i &#8216;error | warning&#8217; /var/log/*log


Was there some tool that tries to solve your configuration and solve potential problems with packages etc...?

---

### Post by TheFu on 2014-02-03
It looks like the command got munged in some way.  Please check that the "'" are both the same singe-quote.  From here, it seems a locale issue changes one or both into a right or left tick. That breaks the command.

```
sudo egrep -i 'error|warning' /var/log/*log
```

Hopefully that doesn't get munged.

The only command that I know that might fix APT is **aptitude**.

---

### Post by AlliumPorrum on 2014-02-03
Ok thanks! :=)

 There were quite a lot of lines, but I'm not sure they have anything to do with this problem. How can I clear all the logs, so that after next failed restart it would be easier to see what happened..?

---

### Post by TheFu on 2014-02-03
Startup errors are wiped at every reboot (dmesg).
Log files get rotated, so only "current" ones have the .log extension.
Most log file records have a date/time stamp ... you can add a grep filter to the same line looking for specific times.

If there are too many warnings/errors - either redirect the **egrep** output to a file or pipe it through **more** to see it a page at a time. This is common stuff on UNIX-like OSes.  If you are new to this stuff - [http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](http://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) might help explain the idea, if not the exact commands to be used.

---

