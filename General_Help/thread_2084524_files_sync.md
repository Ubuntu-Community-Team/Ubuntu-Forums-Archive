---
title: "files sync"
date: 2012-11-15
forum: General Help
---

### Post by FemmeFatale on 2012-11-15
Hello, 

I have a case - I work for a big company where strict firewall rules are applied. For some reason, there is not data backup procedure which means I am supposed to take care for my own corporate data. Now I used to do it using external hard drives, however, it's not a solution anymore for a number of reasons.

Questions:

1) is there a way to sync my data over the internet with remote host?
2) is it possible to make it scheduled - let's say twice a day?
3) initially, i will copy all data 1:1 on my work laptop and the remote host and when I run the sync tool, to sync changes only, not all data.

So, would you help?

---

### Post by Paddy Landau on 2012-11-22
> **FemmeFatale said:**
> 1) is there a way to sync my data over the internet with remote host?
Linux has a wonderful utility called [FONT=Lucida Console]rsync[/FONT]. It works like copy ([FONT=Lucida Console]cp[/FONT]), but:

[LIST]
[*][FONT=Lucida Console]rsync[/FONT] is clever enough to copy only what has changed, rather than entire files. So, if you change only 20 bytes of a 3Gb file, [FONT=Lucida Console]rsync[/FONT] will transfer only the 20 bytes plus the changed timestamp. It can also compress the data before sending to make better use of bandwith.
[*][FONT=Lucida Console]rsync[/FONT] will also (if you request it) delete files on the target if they have been deleted on the source. That means you have an exact copy of the source. Use the [FONT=Lucida Console]--archive[/FONT] option.
[*]The "r" stands for remote: it is able to connect to an [FONT=Lucida Console]rsync[/FONT] daemon running remotely. I believe that [FONT=Lucida Console]rsync[/FONT] can perform the task from either the sending or receiving machine. (You do not have to have a remote [FONT=Lucida Console]rsync[/FONT] daemon if you can access the remote folder directly via the network.)
[/LIST]
> **FemmeFatale said:**
> 2) is it possible to make it scheduled - let's say twice a day?Yes. simply schedule it with [FONT=Lucida Console]cron[/FONT] or [FONT=Lucida Console]anacron[/FONT], whichever is more appropriate to your task.

> **FemmeFatale said:**
> 3) initially, i will copy all data 1:1 on my work laptop and the remote  host and when I run the sync tool, to sync changes only, not all data.
No problem. [FONT=Lucida Console]rsync[/FONT] will simply pick up where you left off. In fact, you can use [FONT=Lucida Console]rsync[/FONT] instead of [FONT=Lucida Console]cp[/FONT] for the initial backup; [FONT=Lucida Console]rsync[/FONT] will compress the data before sending it over the network.

Bonus tip: If you want to make backups with archives, use [FONT=Lucida Console]rdiff-backup[/FONT]. It uses [FONT=Lucida Console]rsync[/FONT] to efficiently transfer data, but it also creates incremental backups. I have used [FONT=Lucida Console]rdiff-backup[/FONT] for years and it has never failed me.

---

