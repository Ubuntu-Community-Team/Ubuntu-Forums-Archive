---
title: "Broadcast Webcame over HTTP"
date: 2007-01-12
forum: General Help
---

### Post by CameronCalver on 2007-01-12
Hello i have a server under my house and i would like to host a live stream of the farm for some people i already have a apache server setup but what do i add to index.html to make it broadcast the webcam

---

### Post by netadptr0719 on 2007-01-12
I don't know about configuring apache to do it because I don't know enough about your cam to tell you what to do or how you have it set up or anything.

[http://linux.softpedia.com/get/Communications/Conferencing/webcam-underscore-server-234.shtml](http://linux.softpedia.com/get/Communications/Conferencing/webcam-underscore-server-234.shtml)

Go to that link and try that special server. If that one doesn't work just look for a separate webcam server rather than trying to do apache. I think that it may be easier in the long run.

---

### Post by CameronCalver on 2007-01-12
yeh much easyer

---

### Post by CameronCalver on 2007-01-12
i extracted it and did ```
./configure 
``` and i got
```
server@ubuntu:~/webcam_server-0.50$ ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
server@ubuntu:~/webcam_server-0.50$ 

```

---

