---
title: "How to safely clean up logs?"
date: 2006-11-14
forum: General Help
---

### Post by Peepsalot on 2006-11-14
What is the best way to clean up my log files.  I had a glitch at one point(never figured out the source) where it was adding something like 20lines/second to my log files all saying "VFS: busy inodes on changed media.".  So I have 568MB in my var/log now that I want to clean up.

Is it safe to delete these logs and the files will be recreated as needed?  Or is there some other method that should be used?

---

### Post by dcstar on 2006-11-14
> **Peepsalot said:**
> What is the best way to clean up my log files.  I had a glitch at one point(never figured out the source) where it was adding something like 20lines/second to my log files all saying "VFS: busy inodes on changed media.".  So I have 568MB in my var/log now that I want to clean up.

Is it safe to delete these logs and the files will be recreated as needed?  Or is there some other method that should be used?

logrotate

---

### Post by kerry_s on 2006-11-14
I've deleted everything but the folders without problems, new files are made on next boot/reboot. It won't make the folders if you delete them and you'll get a message there missing.

---

### Post by nikhilk on 2006-11-14
> **dcstar said:**
> logrotate
I second that.

---

