---
title: "iotop columns' meaning"
date: 2012-10-29
forum: General Help
---

### Post by robbofolle on 2012-10-29
Hi,
I've searched over internet but I am not able to find the answer to my question:

What is the detailed meaning of the columns SWAPIN and IO of the application **iotop**

They are expressed in percentage and I am not able to precisely figure what, for example 10% of SWAPIN means.

Thank you.

---

### Post by kanikilu on 2012-10-29
From the man page: > iotop displays columns for the I/O bandwidth read and written by each process/thread during the sampling period. **It also displays the per&#8208;centage of time the thread/process spent while swapping  in and while waiting on I/O**. For each process, its I/O priority (class/level) is shown. In addition, the total I/O bandwidth read and written during the sampling period is displayed at the top of the interface.

---

### Post by robbofolle on 2012-11-14
Thank you...I feel an idiot!!!
Anyway there still something I don't understand.

If I execute iotop when the system is thrashing, I see several processed with 99% IO, but 0% SWAPIN.

How is this behaviour possible?

---

