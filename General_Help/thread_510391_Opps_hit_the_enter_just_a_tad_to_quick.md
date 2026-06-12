---
title: "Opps hit the enter just a tad to quick"
date: 2007-07-26
forum: General Help
---

### Post by jphillip on 2007-07-26
Howdy,

O.K. played with sudo and should not have.

Here was my problem. Did not have writes access to edit and add web pages in /var/www/

SO I did this thinking this would help...

sudo chown -R jon:jon /var/www/ 

But I actually  did this :

chown -R jon:jon /var

Now since I rebooted it appears I have messed up some items and can not for example get the network up.
ETH0 and ETH1 do not have the correct permissions to run. Nor Mysql  etc..etc..etc...

Any suggestions????

Jp

---

### Post by louieb on 2007-07-26
wild as guess of the day change the owner:group back to root. Just looked at mine some of the directories belong to a different group but both are empty.  
.```

lou@blackboxu:~$ cd /var
lou@blackboxu:/var$ ls -l
total 40
drwxr-xr-x  2 root root  4096 2007-07-26 07:37 backups
drwxr-xr-x 13 root root  4096 2007-03-11 19:57 cache
drwxr-xr-x  2 root root  4096 2006-05-30 20:02 games
drwxr-xr-x 45 root root  4096 2007-07-25 07:45 lib
drwxrwsr-x  2 root staff 4096 2006-05-22 09:00 local
drwxrwxrwt  3 root root    80 2007-07-22 07:34 lock
drwxr-xr-x  7 root root  4096 2007-07-26 07:40 log
drwxrwsr-x  2 root mail  4096 2006-05-30 19:49 mail
drwxr-xr-x  2 root root  4096 2006-05-30 19:49 opt
drwxr-xr-x 12 root root   580 2007-07-25 07:42 run
drwxr-xr-x  6 root root  4096 2006-05-30 19:53 spool
drwxrwxrwt  6 root root  4096 2007-06-08 07:35 tmp
lou@blackboxu:/var$


```

This is my desktop. If that doesn't fix it I'll check my LAMP server  later and see who owns what there.

---

