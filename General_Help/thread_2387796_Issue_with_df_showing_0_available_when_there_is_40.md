---
title: "Issue with df showing 0 available when there is 40G left. I can write to that 40G"
date: 2018-03-23
forum: General Help
---

### Post by LeviNelson on 2018-03-23
Ran into a real peculiar problem today. I have two 1TB drives mirrored (Softraid) together in my server. The last 792G of it has been partitioned as /thrash. The drive filled up so I went and deleted a folder with 28G. Checked df after and available was still saying 0. Thinking "that's odd but maybe something else was waiting for that space" I deleted another 22G folder. And checked df. Only 11G available. Hmm well that's REALLY odd.

then noticed this df output had a huge discrepancy between AVAIL, USED, and SIZE columns:

/dev/md2        792G  741G   11G  99% /thrash

So I googled around found things about cached files etc etc so I just rebooted my machine. It came back up with the same issue. So I unmounted and forced a fsck. It came back clean.

Perplexed I just started copying files back onto the partition until rsync complained that it was full and ended up blowing way past 11G free.

df output once I filled it up: 

/dev/md2        792G  **792G     **0 100% /thrash

df output after I deleted one of the files:

/dev/md2        792G  **788G     **0 100% /thrash

another file:

/dev/md2        792G  **776G     **0 100% /thrash

You get the idea....

Once I deleted all the files I am back to

df output:

/dev/md2        792G  **741G   **11G  99% /thrash


Has anyone seen anything like this? I've rebooted my machine multiple times. mdstat looks fine. Nothing weird in syslog or dmesg. I really am at a loss for this one. First time I have ever seen this and I always df after a rm. I've tried googling around but can't find anything specific to my issue. 

Anyone have any ideas on this one? Thanks


system:

Distributor ID: Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:        16.04
Codename:       xenial

EDIT: I should also add du agrees with the USED column throughout these tests.

---

### Post by wildmanne39 on 2018-03-23
Please post your solution and please mark the thread solved.

Thanks

---

### Post by Impavidus on 2018-03-24
5% of your filesystem is reserved for root, so you can write to it if you're the root user, but it's not available for ordinary users. Some people say that 5% is way too much on large modern drives. I say that it's unlikely 5% will make a difference. Anyway, if you want to change that 5%, use **tune2fs**. From the man page:```
man tune2fs
...
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which may only be allocated
              by privileged processes.   Reserving some number  of  filesystem
              blocks for use by privileged processes is done to avoid filesys&#8208;
              tem fragmentation, and to allow system  daemons,  such  as  sys&#8208;
              logd(8),  to continue to function correctly after non-privileged
              processes are prevented from writing to  the  filesystem.   Nor&#8208;
              mally, the default percentage of reserved blocks is 5%.

```

---

