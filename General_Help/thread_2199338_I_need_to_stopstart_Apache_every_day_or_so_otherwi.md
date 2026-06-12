---
title: "I need to stop/start Apache every day or so otherwise I can't edit MediaWiki content."
date: 2014-01-13
forum: General Help
---

### Post by tbeagley on 2014-01-13
Every couple of days I go to make an edit on a Wiki I created and I get "No Data Received/[COLOR=#444444][FONT=Helvetica]Unable to load the webpage because the server sent no data." back from Chrome.

I terminal into my server (12.04 server with almost nothing but Apache, PHP, MediaWiki and Postgres installed) and stop/start Apache and things are back to normal for another day or so.

I'm not even really sure where to start with this issue as it's the first time I've built a Wiki server and I can't find info on this specific issue anywhere.[/FONT][/COLOR]

---

### Post by bertan2 on 2014-01-14
Did you look in the Apache log?

---

### Post by tbeagley on 2014-01-15
I get two errors occurring throughout the log.

#1: ***PHP Notice:  Undefined variable: organicdesign in /etc/itwiki/extensions/JavaScript/JavaScript.php on line 48***
This one occurs every time I edit an article, regardless of whether the site's working or not.
I'm looking into this one.

#2: ***[notice] child pid ##### exit signal Segmentation fault (11)***

I ran: **ps -ef|grep httpd**

Then attached GDB to the resultant process, waited for it to crash and did a backtrace which got me:

**#0  0x00007f8d20fdc94a in waitpid () from /lib/x86_64-linux-gnu/libc.so.6**
**#1  0x0000000000441c84 in ?? ()**
**#2  0x0000000000442d0c in wait_for ()**
**#3  0x0000000000434684 in execute_command_internal ()**
**#4  0x000000000043618e in execute_command ()**
**#5  0x000000000041e3ed in reader_loop ()**
**#6  0x000000000041c906 in main ()**

With which I honestly have no idea what to do. :\

---

### Post by tbeagley on 2014-01-21
I guess no one has any ideas?

In the meantime, how can I create a cron job that stops then starts apache every night at midnight?

---

### Post by Habitual on 2014-01-21
[https://help.ubuntu.com/12.04/serverguide/httpd.html](https://help.ubuntu.com/12.04/serverguide/httpd.html) says "sudo service apache2 restart" but if you use root's cron, sudo is not necessary.

Either way, the cron would be as root:
```
crontab -e 
``` and add
```
0 0 * * * /path/to/service apache2 restart
``` may be all you need.

terminal > 
```
whereis service
``` will show you the /path/to/service

for future reference:
[cron sandbox]("http://www.dataphyx.com/cronsandbox/cronsandboxgui.php")

---

