---
title: "sudo vs kdesudo problem"
date: 2008-03-05
forum: General Help
---

### Post by tarun2000 on 2008-03-05
Why do I get different outputs for these two commands and how do I fix it?
Thanks

```

tarun@tarun-laptop:~$ sudo /opt/lampp/lampp statusraw | grep APACHE
APACHE RUNNING
tarun@tarun-laptop:~$ kdesudo /opt/lampp/lampp statusraw | grep APACHE
VERSION 1.6.6

APACHE RUNNING

MYSQL NOTRUNNING

PROFTPD RUNNING

```

---

### Post by kuja on 2008-03-06
I don't see why you'd want to use kdesudo for a terminal app, assuming that's what it is, but placing the entire command in quotes should help.

---

### Post by tarun2000 on 2008-03-06
Its not a terminal app.

I have a Java GUI that makes a native call to that script and parses its output to determine if the process is running.

I'll try the quotes and see how that goes.

---

