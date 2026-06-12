---
title: "I need Crontab to run a program"
date: 2007-01-17
forum: General Help
---

### Post by CameronCalver on 2007-01-17
hello our isp allows us 4gb peak and 4gb off peak so i was wondering if i could get crontab to run
```
rtorrent /home/server/Share/Share/torrents/007_casino_royal/casino_royal.torrent
``` at a certain time i understand that ```
5 14 * * * rtorrent /home/server/Share/Share/torrents/007_casino_royal/casino_royal.torrent
``` should make it run but it doesn't also how do i make it so that it runs in a terminal i can see?

---

### Post by dcstar on 2007-01-17
> **CameronCalver said:**
> hello our isp allows us 4gb peak and 4gb off peak so i was wondering if i could get crontab to run
```
rtorrent /home/server/Share/Share/torrents/007_casino_royal/casino_royal.torrent
``` at a certain time i understand that ```
5 14 * * * rtorrent /home/server/Share/Share/torrents/007_casino_royal/casino_royal.torrent
``` should make it run but it doesn't also how do i make it so that it runs in a terminal i can see?

Do a search and you will find multiple posts explaining that for cron jobs you need to put the **full path **in for any command.

---

### Post by CameronCalver on 2007-01-17
that was the full path

---

### Post by dcstar on 2007-01-17
> **CameronCalver said:**
> that was the full path

So "rtorrent" is a full path is it?, my eyes must be deceiving me.

---

### Post by CameronCalver on 2007-01-22
well thats the command i do in the terminal to make it work so what is the full path?

---

### Post by konsole on 2007-01-22
> **CameronCalver said:**
> well thats the command i do in the terminal to make it work so what is the full path?

Cameron, you're a gui guy right?

In a terminal type: ```
which rtorrent
``` The result of this command is the **full path** to the rtorrent binary on your system.

So your cron entry will start something like: /usr/local/bin/rtorrent

You need to read up on some basic Unix commands mate or you'll give Aus a bad name. ;) 

HTH.

---

### Post by CameronCalver on 2007-01-23
i do not give aus a bad name so you dont no the full command

---

