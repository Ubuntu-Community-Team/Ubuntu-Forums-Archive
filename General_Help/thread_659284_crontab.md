---
title: "crontab"
date: 2008-01-05
forum: General Help
---

### Post by kool_kat_os on 2008-01-05
I just saved a file to my desktop called "cron.txt" and I when to terminal and typed
"sudo crontab -u myusername /home/mysuername/Desktop/cron.txt"

This is what the file says:
[HTML]

* 6 * * * sudo sync -rtlzv --delete rsync.apache.org::apache-dist /var/www/[/HTML]

Now what? Also how do I check to see if it has ran? Thanks

---

### Post by ~LoKe on 2008-01-05
How many threads do you need for one thing?

[Thread](http://ubuntuforums.org/showthread.php?t=659198)
[Thread](http://ubuntuforums.org/showthread.php?t=658735)

---

### Post by kool_kat_os on 2008-01-05
when I have a new question no one answers

---

### Post by ~LoKe on 2008-01-05
> **kool_kat_os said:**
> when I have a new question no one answers

Answers were given to you [here](http://ubuntuforums.org/showpost.php?p=4078648&postcount=4).

---

### Post by kool_kat_os on 2008-01-05
how do I check if it ran?

---

### Post by ~LoKe on 2008-01-05
Err...I'm not sure, but you could have it make a log....Not familiar with rsync or even crontabs for that matter.
```
0 0 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/ && echo "Complete 0 0" >> /var/www/cronlog
0 6 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/ && echo "Complete 0 6" >> /var/www/cronlog
0 12 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/ && echo "Complete 0 12" >> /var/www/cronlog
0 18 * * * rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www/ && echo "Complete 0 18" >> /var/www/cronlog
```

There's probably a proper way to do that...

---

### Post by arvevans on 2008-01-05
Go to a Terminal page and do:
[INDENT]man crontab

and

man cron[/INDENT]

This tells you where cron logs it's stuff, how to control the log level, how to make cron run in foreground, etc.

Arv
_._

---

