---
title: "Recovering data with DDRescue"
date: 2024-09-05
forum: General Help
---

### Post by tommy2k10 on 2024-09-05
I am recovering a friend's data, on an 1TB external drive that is diagnosed as in poor health by Western Digital using DDRescue, by cloning the disk ona blank 2TB Seagate drive, but after Pass 1 has finished, it seems to have stopped. The output is:
IPOS: 870814MB
OPOS: 870814MB
Non-tried: 428761MB
Rescued: 571377MB
Percent rescued: 57.2%
Non-trimmed: 31180kB
Non-scraped: 0B
Bad-sector: 0B
Bad areas: 0
Read errors: 632
Current rate: 0B/s
Average rate: 5259kB/s
Error rate: 167kB/s
Run time: 1d 6h 16m
Remaining time: n/a
Time since last remaining read: 5h 18m 2s
Copying non-tried blocks... Pass 2 (Backwards)

What do I do now and how do I access the recovered files?

---

### Post by 1fallen on 2024-09-05
If you are trying to recover data from a corrupted disk, you may want to append the -r option after the first try above. This will instruct ddrescue to retry bad sectors in an effort to recover as much data as possible. You can specify the number of retries after the option. In this example, we will use 3 retries.

```
sudo ddrescue -d -r3 /dev/sdxx backup.img backup.logfile
```

Of course change "/dev/sdxx"  to your Drive used.

---

