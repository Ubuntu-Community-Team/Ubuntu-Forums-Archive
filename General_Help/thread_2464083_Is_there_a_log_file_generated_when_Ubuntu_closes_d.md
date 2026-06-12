---
title: "Is there a log file generated when Ubuntu closes down?"
date: 2021-06-24
forum: General Help
---

### Post by robert48 on 2021-06-24
I'm using 21.04 Ubuntu Desktop AMD 64

When I close down I get a flash of text on the screen that is too quick for me to read. Some of the text is in red. 

Is there a log file generated when I close Ubuntu down and if so, how do I access it please?

---

### Post by ActionParsnip on 2021-06-24
Maybe in /var/log/kern.log

---

### Post by TheFu on 2021-06-24
> **robert48 said:**
> Is there a log file generated when I close Ubuntu down and if so, how do I access it please?

Logs are constantly being written from the initial boot until full shutdown and halt.  These are in /var/log/.
If it were me, I'd boot from some alternate media, like into a "Try Ubuntu" environment from any desktop install ISO on flash storage, then mount the partition were /var/ is normally located and look around using tools like egrep and looking at the file timestamps to chose which were written most recently.  On Unix file systems, files have an attribute called "mtime" - that's the last time a file was modified.  There are a few other attributes like ctime, and atime, but mtime is the most useful, IMHO.

---

