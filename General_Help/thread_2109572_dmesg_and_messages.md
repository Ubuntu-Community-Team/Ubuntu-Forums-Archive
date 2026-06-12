---
title: "dmesg and messages"
date: 2013-01-27
forum: General Help
---

### Post by borgward on 2013-01-27
Ubuntu 10.04
I am looking in /var/log dmesg and messages for reports of I/O errors. What do I look for? Will see words like "I/O error"?

I looked as far back as messages.4 which dates to about Dec 12 2012. I began having messages about I/O errors Dec 2 when I md5sum on something I downloaded.

(I was advised the HDD was failing and replaced it with new that recently failed. I am now running the old HDD until the replacement arrives)

? How far back are messages in /var/log kept? 
? Anyway to keep messages for a longer period?

---

### Post by papibe on 2013-01-28
Hi borgward.

Search for the keywords: error, sata or sda1 (where sda1 is the partition you are interested own). This log is also useful: /var/log/syslog

For instance:
```
grep -i error /var/log/syslog
```
Let us know how it goes.
Regards.

---

