---
title: "Make terminal commands run automatically"
date: 2008-01-05
forum: General Help
---

### Post by kool_kat_os on 2008-01-05
I need to make this command run every six hours automatically in terminal, how do i do that?
[HTML]rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www[/HTML]

---

### Post by kool_kat_os on 2008-01-05
I need to make this command run every six hours automatically in terminal, how do i do that?
[HTML]rsync -rtlzv --delete rsync.apache.org::apache-dist /var/www[/HTML]

---

### Post by ~LoKe on 2008-01-05
[Crontab](http://ubuntuforums.org/showthread.php?t=102626).

---

### Post by HermanAB on 2008-01-05
Google for "crontab howto".

Use the FULL path when you call a program in a cron script, else it won't work.

Cheers,

Herman

---

### Post by Sef on 2008-01-05
Moved to General Help.

---

### Post by bodhi.zazen on 2008-01-05
Threads merged.



please do not make duplicate threads. It makes it more difficult to help you.

---

