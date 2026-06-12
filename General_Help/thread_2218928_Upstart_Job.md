---
title: "Upstart Job"
date: 2014-04-22
forum: General Help
---

### Post by xWEkxhW on 2014-04-22
Hello,

I've written a small Upstart job intended to:
 - Copy data files into a tmpfs folder before mysql starts
 - Copy the contents of the tmpfs folder to the hard drive when mysql is stopped

The job I've written is:

```
start on starting mysql
stop on stopped mysql


task


post-stop script
   cp -r -p /mnt/ram/mysql/* /var/lib/mysql-offline
end script


pre-start script
   chown mysql:mysql /mnt/ram/mysql
   cp -r -p /var/lib/mysql-offline/* /mnt/ram/mysql/
end script

```
It's not fully working, and blocks mysql from starting. Obviously I've done something wrong. Does anybody have any hints to correct it?

Thanks!

---

### Post by xWEkxhW on 2014-04-22
Update: I removed the task line and it's working correctly now :)

---

### Post by Danger_Monkey on 2014-04-22
If you run into issues again add:
```

set -x

```
at the top of your script.  It will print out each line, and the result.  It will also show you where the script stops or hangs. It's quite useful when everything looks good.

---

### Post by mörgæs on 2014-04-22
Please mark the thread 'solved'.

---

