---
title: "nginx running, but ... not installed"
date: 2014-01-28
forum: General Help
---

### Post by sanderj on 2014-01-28
Hi,

nginx is running and listen to port 80:

```
sander@flappie:~$ ps -ef | grep nginx
root      1347     1  0 20:29 ?        00:00:00 nginx: master process /usr/sbin/nginx
www-data  1348  1347  0 20:29 ?        00:00:00 nginx: worker process
www-data  1349  1347  0 20:29 ?        00:00:00 nginx: worker process
www-data  1351  1347  0 20:29 ?        00:00:00 nginx: worker process
www-data  1352  1347  0 20:29 ?        00:00:00 nginx: worker process
sander    2911  2729  0 20:29 pts/3    00:00:00 grep --color=auto nginx
sander@flappie:~$ 
```


However, I can't remove it as Ubuntu says it's not installed. :confused:

How can I solve this? I wan't to get rid of nginx as I want to use apache.

Thanks,


```
sander@flappie:~$ sudo apt-get remove nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nginx' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sander@flappie:~$ sudo apt-get purge nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nginx' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sander@flappie:~$ 
```

```
sander@flappie:~$ sudo service nginx stop
 * Stopping nginx nginx                                                                                                                  [ OK ] 
sander@flappie:~$ sudo service nginx stop
 * Stopping nginx nginx                                                                                                                  [ OK ] 
sander@flappie:~$ 
sander@flappie:~$ sudo service nginx stop
 * Stopping nginx nginx                                                                                                                  [ OK ] 
sander@flappie:~$ sudo service nginx stop^C
sander@flappie:~$ !ps
ps -ef | grep nginx
sander    3345  2729  0 20:32 pts/3    00:00:00 grep --color=auto nginx
sander@flappie:~$ sudo apt-get purge nginx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'nginx' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sander@flappie:~$ 
```

---

### Post by Erik1984 on 2014-01-28
That's weird, how dit you install it? 

You could try to remove the service so at least it will not start up on the next boot:
```
sudo update-rc.d -f nginx remove
```

---

### Post by sanderj on 2014-01-28
I can't remember how I installed it. 

I did:
sudo update-rc.d -f nginx remove
sudo rm /etc/init.d/nginx

and after a reboot, everything is fine.

Thank you.

---

