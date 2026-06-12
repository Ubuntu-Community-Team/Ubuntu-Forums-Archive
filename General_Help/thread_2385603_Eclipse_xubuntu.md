---
title: "Eclipse xubuntu"
date: 2018-02-22
forum: General Help
---

### Post by awachens on 2018-02-22
Hi good afternoon!!

I have eclipse installed in my xubuntu.
When I try to crate new class eclipse stay loading at 100%... this operation need a lot time ? 
Why stay loading and never end ?
What probes can I do ?

Thank you !!

---

### Post by TheFu on 2018-02-22
Eclipse is written in java and fairly resource intensive.
8G of RAM minimal.
top, free, iostat, memstat, netstat are the tools I'd use to narrow down the issue.
And looking through the system logs for issues is always helpful.

---

### Post by awachens on 2018-02-23
its posible .. 
Ok but what I have to search .
What info I paste here ?
What log ? Syslog?

Thank you

---

### Post by TheFu on 2018-02-23
> **TheFu said:**
> 
top, free, iostat, memstat, netstat are the tools I'd use to narrow down the issue.
And looking through the system logs for issues is always helpful.

I googled "ubuntu log files" and got this link: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
The other, already provided commands, help to determine which resources might be limited, if any.  There are many other tools, but those are the ones I use AND the relevant output can be pasted here in text.

---

