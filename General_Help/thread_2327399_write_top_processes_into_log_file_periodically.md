---
title: "write top processes into log file periodically"
date: 2016-06-10
forum: General Help
---

### Post by marchello_lippi2 on 2016-06-10
Hi all, 

How do I write top processes into log file periodically? 
Thanks ahead.

---

### Post by Habitual on 2016-06-10
[http://www.tldp.org/LDP/abs/html/io-redirection.html](http://www.tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by SeijiSensei on 2016-06-10
You'll need to run top as "top -n 1 >> /path/to/logfile" so it will display one page then exit.

If you only want, say, the results for the first ten processes use:
```
top -n 1 | head -n 17 >> /path/to/logfile
```
The first seven lines are the header at the top of the output, followed by ten lines of processes.

You need to create an entry in cron to do this.  See [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

