---
title: "find point in journal where system failed"
date: 2019-10-07
forum: General Help
---

### Post by holiday on 2019-10-07
I am having random lockups. Looking back through the journal I want to see the journal at the time of the lockup. 


journalctl --list-boots gives some information but I am still struggling to locate the exact position in the journalctl output. Is there a simple search I can do to locate the exact point

---

### Post by wildmanne39 on 2019-10-07
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by TheFu on 2019-10-08
journalctl can search by time.  manpage has more, but [https://www.loggly.com/ultimate-guide/using-journalctl/](https://www.loggly.com/ultimate-guide/using-journalctl/) might be easier.

---

