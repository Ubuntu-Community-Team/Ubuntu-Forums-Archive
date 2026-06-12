---
title: "How can I resume interrupted ddrescue backup?"
date: 2008-03-12
forum: General Help
---

### Post by nisarg on 2008-03-12
Hi all,

I recently had my windows NTFS partition crashed? 
I setup and mounted a smbfs network share, installed ddrescue and started copying the device. After around 5-7 days the network some how reset and the copying process was interrupted. I still have around atleast 15gb of data that needs to be copied. I know ddrecue can be resumed. How can I do that?

Any help will be appreciated.
Cheers, N

---

### Post by nisarg on 2008-03-12
OK - I think I managed to resume my backup it hits a brick-wall and stops for some reason.
I used the same command pointing to the previous log:

```
 sudo ddrescue -r2 /dev/sda Backup.img Backup.log 
```

and it managed to read from where it stopped. But within mins after it starts, it terminates with this error.
Any ideas anyone?


```
 ubuntu@ubuntu:~/Backup$ sudo ddrescue /dev/sda Backup.img Backup.log 

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:    41926 MB,  errsize:    319 MB,  errors:    9203
Current status
rescued:    41926 MB,  errsize:    319 MB,  current rate:        0 B/s
rescued:    41926 MB,  errsize:    319 MB,  current rate:        0 B/s
   ipos:    42246 MB,   errors:    9203,    average rate:        0 B/s
   opos:    42246 MBr: Invalid argument

ubuntu@ubuntu:~/Backup$

```

As I mentioned above, I should have atleast got around 15gb left that still needs to be recovered from this crashed disk. Any help is more than appreciated.

---

### Post by nisarg on 2008-03-12
People, I know we have some great people who are experts on data recovery and ddrescue.
Please help me sort this out.

thanks...

---

