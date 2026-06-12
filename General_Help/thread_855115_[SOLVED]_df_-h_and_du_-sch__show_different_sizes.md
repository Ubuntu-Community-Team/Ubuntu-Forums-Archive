---
title: "[SOLVED] df -h and du -sch * show different sizes"
date: 2008-07-10
forum: General Help
---

### Post by Marty02 on 2008-07-10
Hi everybody,

I am running a FreeBSD system but this here is the most active forum that I found and I assume that my question has nothing todo with OS specific circumstances.

So, the var-folder of my root-partition is full:

> df -h

/dev/mirror/gm0s1a    248M    101M    127M    44%    /
/dev/mirror/gm0s1e    248M     29M    199M    13%    /tmp
/dev/mirror/gm0s1f    2.9G    2.3G    368M    87%    /usr
/dev/mirror/gm0s1d    248M    219M    8.8M    96%    /var <--- FULL

but when I use du -sch * in the var-folder I receive the followin information

2,0K    account
6,0K    at
 18K    backups
6,0K    cron
 45M    db
2,0K    empty
2,0K    games
2,0K    heimdal
4,0K    lib
1,6M    log
346K    mail
4,0K    msgs
 40K    named
2,0K    preserve
 48K    run
2,0K    rwho
 24K    spool
294K    tmp
2,8M    www
 50M    total

it shows me that I only use 50 MB. How can that be? how can I detect what on my partition uses so much space?

---

### Post by ahzadjali on 2008-07-10
huuuuuuuuuum, i too faced /VAR full............poor me had to resize with live cd and messed up things. now my /usr is getting 35% how can i resize /VAR which is 14GB and allocate space to /USR...
thanks

---

### Post by Gunman1982 on 2008-07-10
Here is an article about that issue: [http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html]("http://www.cyberciti.biz/tips/freebsd-why-command-df-and-du-reports-different-output.html")

In short: If you have a file in a *nix system which is still used by a process and you delete it its not gone until the process ends. However du doesn't see it and doesn't summarize it, df however only looks at the free space and since the file is not marked as free space yet (because the process still uses it) it shows more used space the du.

---

### Post by Marty02 on 2008-07-10
thanks a lot for this article. that was exactly what I was looking for. 

problem solved! your guys are great!

---

