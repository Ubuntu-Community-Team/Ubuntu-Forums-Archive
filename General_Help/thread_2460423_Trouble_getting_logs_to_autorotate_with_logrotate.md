---
title: "Trouble getting logs to autorotate with logrotate"
date: 2021-04-09
forum: General Help
---

### Post by jo-polanco on 2021-04-09
Ubuntu 20.04.2 LTS
Gnome 3.36.8
```

$ logrotate --version
logrotate 3.14.0
```


It's been impossible to get logs to rotate automatically once they reach a size of 125M. Here's the config file saved to ```
/etc/logrotate.d
```:  

```
/home/App/Logs/*.log 
{
    missingok
    size 125M
    rotate 14
    create
}
```

What's missing?

---

### Post by TheFu on 2021-04-09
Try 
```
maxsize 10M
```
Do you bounce the application so the old log file gets closed and the new file gets opened?  Files that are just moved don't change the inode, so any open file handles will follow to the new name.

Manpage for logrotate.conf says:
```
maxsize size
              Log files are rotated when they grow bigger than size bytes  even
              before  the  additionally specified time interval (daily, weekly,
              monthly, or yearly).  The related size option is  similar  except
              that it is mutually exclusive with the time interval options, and
              it causes log files to be rotated without regard for the last ro&#8208;
              tation  time.   When maxsize is used, both the size and timestamp
              of a log file are considered.
```


Also, seems odd to be rotating logs under /home/.  Logs belong in /var/log/ - [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)

Gnome has NOTHING to do with this.

---

### Post by HermanAB on 2021-04-09
Missing:
postrotate
        /usr/bin/killall -HUP yourappthatwritesthelog

See this:
[https://linux.die.net/man/8/logrotate](https://linux.die.net/man/8/logrotate)

---

### Post by jo-polanco on 2021-04-10
Turns out [this]("https://www.reddit.com/r/Ubuntu/comments/mnn5xd/trouble_getting_logs_to_autorotate_with_logrotate/gtz4xzq/?utm_source=reddit&utm_medium=web2x&context=3") solved the issue but thanks for chiming in :)

---

### Post by TheFu on 2021-04-10
> **jo-polanco said:**
> Turns out [this]("https://www.reddit.com/r/Ubuntu/comments/mnn5xd/trouble_getting_logs_to_autorotate_with_logrotate/gtz4xzq/") solved the issue but thanks for chiming in :)

There are many ways to solve most problems.  The **maxsize** option ignores time specs, as can be seen in the manpage ref above.

Please mark this thread as SOLVED  to others don't waste time.  And a summary of what you actually do would be appreciated too, beyond a link from some external site. Save other people some time, just like you wish would happen for your questions.

---

