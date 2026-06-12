---
title: "Can't clear huge syslog"
date: 2013-12-01
forum: General Help
---

### Post by AndrewWalker on 2013-12-01
I'm having trouble clearing my /var/log/syslog file which has got enormous. It's got so big I can't actually open it so see what the problem is! 

```
-rw-r----- 1 syslog            adm      3070672281 Dec  1 12:44 syslog

```

Various sites have suggested 

```
> /var/log/syslog

```

should clear it but even using sudo gives the permission denied error. I've stopped the syslogd daemon first but nothing helps.
What do I do to clear it down? I've run logrotate but it's still the same size.

Any ideas ?

---

### Post by josgeluk on 2013-12-01
Try this:
List the inode number:
```
ls -il /var/log/syslog
```
Then remove the file by its inode:
```
sudo find /var/log -inum [inode-number] -exec rm -i {} \;
```

---

### Post by AndrewWalker on 2013-12-01
Well a partial success! I wanted to clear the log file, not delete it completely though! Will the file get recreated automatically or do I need to create an empty syslog file again?

---

### Post by josgeluk on 2013-12-01
I would guess that a new /var/log/syslog file will magically appear, but it wouldn't hurt to "sudo touch" one.

---

### Post by Habitual on 2013-12-01
```
truncate -s 0 /var/log/syslog
```?

---

