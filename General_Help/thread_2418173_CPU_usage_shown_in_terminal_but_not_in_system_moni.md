---
title: "CPU usage shown in terminal but not in system monitor"
date: 2019-05-02
forum: General Help
---

### Post by PABlanche on 2019-05-02
Hi,

Thunderbird 60.6.1 running on Ubuntu 19.04 is constantly using between 40 and 60% of the CPU. 
I have to close and  restart Thunderbird for the CPU usage to drop in the single digit, but after a while (hours), it get back to the 60%. I reported the problem to Mozilla.

Strangely enough, this high CPU usage does not appear in the system monitor (~6%) but only in the terminal running "top" (up to 60%). Any reason for this discrepancy?

The CPU is getting hot and the fan is kicking in.

---

### Post by TheFu on 2019-05-02
Which packaging system installed thunderbird?  APT? Snap? Flatpak? AppImage?  Was it from the Canonical Repo, some PPA or some app-store?

Can you see it in **top**?  Can you copy/paste that output here?

Is the system low on RAM and spending lots of time swapping?  What does vmstat show?

Is there a specific email that is being viewed which causes it?  It is full of javascript and images?  Lots of tracking allowed via email?
Or have you only allowed plain 8-bit ASCII to be shown?

---

### Post by PABlanche on 2019-05-07
Here is an example of what **top **is displaying:```

 PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND    
 7231 pablanc+  20   0 2708096 864700 150468 R**  91.7  ** 5.3 251:14.15 thunderbi+ 
 3605 pablanc+  20   0 3820700 829780 233964 S   3.7   5.1 114:47.92 Web Conte+ 
 2046 pablanc+  20   0 1691508 870344 742712 S   0.3   5.4 234:27.90 Xorg       
 3371 pablanc+  20   0 3117268 817604 293184 S   0.3   5.1  86:07.56 firefox-b+ 
 5566 pablanc+  20   0 1757284 329784 256264 S   0.3   2.0   0:16.67 Web Conte+ 
 6924 pablanc+  20   0 8826544 575936 403184 S   0.3   3.6   0:11.37 soffice.b+ 
 8558 pablanc+  20   0   12252   4224   3468 R   0.3   0.0   0:00.98 top        
32296 pablanc+  20   0 1257500 123568  45644 S   0.3   0.8   1:58.17 nautilus   
   
```
Thunderbird is at 91.7% CPU time when the system manager only sees 7%.

Here is the output of **vmstat**:```

procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0   3948 3116276  11308 8428800    0    0    45   278    4   57 24  7 68  0  0

```
Plenty of RAM.

I am not sure how to check for which packaging system installed thunderbird. Please advise

I have 4 accounts 2 POP3 and 2 IMAP.

Thanks for the help and sorry for the delay.

---

### Post by TheFu on 2019-05-08
Please look at your post.  All the columns have been lost, making it impossible to read.  Please use "code tags" to make it look like it does in a terminal. Edit the post above.  AdvReply (#) - 

How many cores does the system have?  91% of 1 core is what percentage of 12 cores? Hint: about 7.5%.

---

### Post by PABlanche on 2019-05-08
System has 4 cores 8 threads

---

### Post by deadflowr on 2019-05-08
In System Monitor go to Preferences > Processes  and uncheck Divide CPU usage by CPU Count to allow it to show all usage instead of usage based on the division per cpu counts. 
(In newer Ubuntu's preferences is in the 3 horizontal line icon (looks like a sandwich or hamburger)

---

### Post by PABlanche on 2019-05-08
Thanks for the tip about the system monitor. 
Any idea why Thunderbird is using so much CPU time?

---

