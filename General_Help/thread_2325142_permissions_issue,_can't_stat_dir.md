---
title: "permissions issue, can't stat dir"
date: 2016-05-19
forum: General Help
---

### Post by djeyewater on 2016-05-19
I'm trying to debug a permissions issue.
When I run
```
sudo -u www-data stat /home/djeyewater/webapps
```
I get
```
stat: cannot stat '/home/djeyewater/webapps': permission denied
```
If I run
```
sudo -u www-data stat /home/djeyewater
```
It works fine, so the problem must be with the permissions on the webapps directory.
Running
```
ls -al /home/djeyewater/webapps
```
gives
```
drwxr-xr-x 3 djeyewater www-data 4096 May 19 13:55 .
```

So I'm not sure why I can't stat that directory as the www-data user?

---

### Post by steeldriver on 2016-05-19
Is /home/djeyewater/ executable by www-data (either via the group or other permissions)? if not, it will not be able to open the directory to see its contents

---

### Post by djeyewater on 2016-05-19
No it wasn't, and that was problem. Thanks very much for the help!

---

