---
title: "using wget to download a cgi file"
date: 2008-03-28
forum: General Help
---

### Post by I.You on 2008-03-28
Hi

I wrote a cgi file, HTTPD_ROOT/cgi-bin/lock.cgi, in target PC
in order to run some command on the target PC :

> #!/bin/sh

sem=`cat /var/lock/semaphore`
sem=$(($sem+1))
echo -n $sem > /var/lock/semaphore

/bin/pidof rsyncmon > /dev/null
if [ $? -eq 0 ]; then
        echo "Already running: rsyncmon"
        return 0
fi
/usr/local/bin/rsyncmon &

return 0

and I ran wget on my PC :

> wget [http://TARGET_IP/cgi-bin/lock.cgi](http://TARGET_IP/cgi-bin/lock.cgi)

then I could get the output - /var/lock/semaphore - on target PC
but it failed to download the cgi file, lock.cgi : 

> ~# wget [http://x.x.x.x/cgi-bin/lock.cgi](http://x.x.x.x/cgi-bin/lock.cgi)
--14:31:11--  [http://x.x.x.x/cgi-bin/lock.cgi](http://x.x.x.x/cgi-bin/lock.cgi)
           => `lock.cgi'
Connecting to x.x.x.x:80... connected.
HTTP request sent, awaiting response... 

NO response infinitely...

Any advice to download successfully?
Thanks in advance.

---

### Post by asdfoo on 2008-03-28
read a tutorial on CGI programming or look at an existing CGI script - if you think all is correct, check your webserver error log.

---

