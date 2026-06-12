---
title: "Boot time is slowing down, how do I remedy that?"
date: 2007-07-06
forum: General Help
---

### Post by SnowPunk98 on 2007-07-06
For some reason now my boot kinda hangs for a while while loading and I don't know what it is doing. Is there anything I can run to report what is taking so long to load?

---

### Post by PaulFr on 2007-07-06
Look at the output of **dmesg** after a boot and see if there are any gaps in the numeric value in the [ ] brackets. Or you can look at **/var/log/messages** after the boot and search for gaps. If you want a useful picture, see the **[http://www.bootchart.org/download.html](http://www.bootchart.org/download.html)** package.

---

