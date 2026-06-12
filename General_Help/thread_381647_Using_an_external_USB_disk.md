---
title: "Using an external USB disk"
date: 2007-03-11
forum: General Help
---

### Post by GeertPoels on 2007-03-11
Hello,

I plugged in my external USB drive but don't have the rights to write files to it :confused: 
The drive is mounted on /media with accessrights dr-x-----------
If I do a chmod, the console writes :

chmod a+w Backup
chmod: changing permissions of `Backup': Read-only file system

but the rights don't change... :( 

What to do ?

Geert

---

### Post by bernied on 2007-03-11
Are you sure this is not an issue with the device?
Have you tried it on another linux OS - say a live cd?

How was it mounted - was it done automatically by Ubuntu?
What is the output of -
```
mount
```

---

