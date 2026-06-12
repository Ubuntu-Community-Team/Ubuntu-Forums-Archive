---
title: "Process eating CPU"
date: 2012-12-26
forum: General Help
---

### Post by matimont on 2012-12-26
Hi,

I have a process eating my CPU at times, and I'm not sure where to start..

The process is a user under my /home directory, and at times, it starts running at 90+% it's a web site under /home..

Thanks!

---

### Post by Frogs Hair on 2012-12-26
Run the following command when it starts happening to display the top processes in the terminal. ```
top
```

---

### Post by MishaX2 on 2012-12-26
You can then use:
```
kill <pid here>
```To terminate the application.

Ofcourse what would be graphically easier, would be to use the System Monitor.
See [http://www.addictivetips.com/ubuntu-linux-tips/how-to-monitor-your-system-performance-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-monitor-your-system-performance-in-ubuntu-linux/) on how to use the system monitor.

---

