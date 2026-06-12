---
title: "Deleting syslog and kern.log"
date: 2018-08-05
forum: General Help
---

### Post by kazakore on 2018-08-05
I've just been using a program (DisplayCal) which obvious has an issue with the way it's programmed and in not long usage has completely filled my system drive! on investigation I find it has repeated links in syslog and kern.log and both are now nearly 20GB in size!! Can I cleanly just delete these files? Is there some way to stop these messages being sent to these files so I can continue to use the program without clogging up my system until it is unusable in a matter of minutes (or maybe a couple of hours)???

---

### Post by kazakore on 2018-08-05
OK I'm doing:

```

rsync -a /var/log/syslog /my/data/path

```

to copy the syslog over to a partition with enough space to process with sed and keep the owner/permission attributes (my data is also ext4.)

```

sed -i '/line-string/d' /data/path/syslog
```

And then assuming a basic:

```
mv /data/path/syslog /var/log/syslog
```

This should all clean up the logs without losing anything that might be best kept? Should I work in a different way or does this seem reasonable? (Even if a little long winded....)

---

### Post by kazakore on 2018-08-05
OK that has reduced the file sizes from over 17GB each to under 1MB each, I have moved them back to the original locations (so written over the original files) but my system is still reporting there as being 0 bytes left on the partition! What is going wrong?


EDIT: Well a restart of the system brought that space back but I didn't think should really have been needed....

---

