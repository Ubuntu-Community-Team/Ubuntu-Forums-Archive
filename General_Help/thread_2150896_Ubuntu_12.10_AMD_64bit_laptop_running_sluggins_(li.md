---
title: "Ubuntu 12.10 AMD 64bit laptop running sluggins (like it's low on mem)"
date: 2013-06-02
forum: General Help
---

### Post by patagriff on 2013-06-02
I have an Acer Aspire 5515 with a dual core AMD 64 bit processor and 3 gigs of memory. I run Ubuntu 12.10 AMD 64 bit operating system that is fully updated. All I ever have running at one time is Google Chrome with a few simple tabs open (Facebook, Google, downloading a movie). 

Lately my computer has been getting more and more sluggish, as if it has a virus (I know people claim this is not possible with Linux) or as if it is out of memory. 

I have run computer janitor to clean up the system.

What steps can I take to try to isolate and eliminate the problem? I have tried different versions of Chrome (Stable, Unstable and Beta) but the problem persists. Has anyone else been having similar problems?

Thanks in advance for any suggestions you can provide.

---

### Post by Hekabe on 2013-06-02
Is it just when Chrome is open? Also, you might want to at least go to a minimum of 4G of RAM, both to utilize dual-channel support and to take advantage of the fact that you are lucky enough to own a 64-bit system that can support that much.

---

### Post by patagriff on 2013-06-02
My system never even reaches a state where swap kicks in. Don't see why I would need more memory. This problem has just arisen and I've been running Ubuntu 12.10 since the minute it came out.

---

### Post by Hekabe on 2013-06-02
Is it only when Chrome is open?

---

### Post by patagriff on 2013-06-03
No. Problems getting worse. Software updater gives error: cache input/output error. Package list or status file could not be opened or parsed. Run apt/get to see what problem is.

Sudo apt/get updates?

Said most likely unresolved tendencies.

---

### Post by r-senior on 2013-06-03
Have you looked in the log files, e.g. /var/log/syslog and /var/log/dmesg?

Any very repetitive messages occurring rapidly?

---

### Post by cbraxton on 2013-06-03
Check your hard drive for bad sectors with Disk Utility. A failing drive will definitely slow things down!

---

### Post by Mark Phelps on 2013-06-04
Sorry to say this but :

> 
I have run computer janitor to clean up the system.

Is likely to be the source of your latest problems where things don't run correctly anymore.

I made the mistake of using this a while back -- and it damaged my system so badly I had to completely reinstall.

Running these "cleaner" apps in Linux is like running "registry cleaners" in MS Windows -- it's asking for problems.

---

### Post by patagriff on 2013-06-04
I have to say, I think my hard drive might be getting ready to crash.

---

