---
title: "Boot and shutdown problem - Over ten minutes!"
date: 2013-06-23
forum: General Help
---

### Post by virgodave61 on 2013-06-23
I'm using Ubuntu version 12.04 and am not sure what caused it, maybe upgrade from terminal? Not sure. But anyway Iv'e attached a copy of my bootchart file. The system is taking like over ten minutes to boot and shutdown, no messages are displayed, just takes very long. Can anyone please help?

Ok maybe I exagerrated a little still 7.5 minutes is a long time.

Oh, sorry one more thing it wouldn't boot at all last week I had to boot from a live CD and run boot-repair to get it going again,I justed wonder if grub could still be damaged? Also I had to use a 12.10 CD and I have 12.04 innstalled.

---

### Post by nashibuntu on 2013-06-23
There is very little information here to help work out what's going wrong. You probably need to take a look at the output of the dmesg command to see what messages are being output as the system boots up. The numbers in square brackets are times in seconds since boot, so you can work out what is happening just before the system pauses. You should also look at the contents of the file /var/log/boot.log
That information might be sufficient to enable someone to help you. It could be a problem mounting a partition, or a networking delay or some such.

---

### Post by virgodave61 on 2013-06-23
Ok thank you very much for the reply I have been working on this all day for almost a week thousands of searches ex.

Attached the results of both files. This is driving me nuts.

---

### Post by rmil on 2013-06-23
Check cifs network it can cause time consuming problems in both directions on mounting the network or on shutdown.
To be sure that it is the problem unmount all cifs/samba mounts before doing shutdown.

---

### Post by virgodave61 on 2013-06-23
Can you explain why cifs network would or may be my problem?

This is solved, I ended up wipeing the OS and reinstalling everything.

---

