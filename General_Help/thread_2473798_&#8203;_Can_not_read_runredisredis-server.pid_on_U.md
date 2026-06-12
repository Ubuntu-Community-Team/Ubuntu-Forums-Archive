---
title: "&#8203; Can not read /run/redis/redis-server.pid on Ubuntu 20.04"
date: 2022-04-14
forum: General Help
---

### Post by kahlenberg on 2022-04-14
[FONT=Arial]Hi,
I installed redis-server v5.0.7 on Ubuntu 20.04 with apt install redis-server. I am recieving always an error: **systemd[1]: redis-server.service: Can’t open PID file /run/redis/redis-server.pid (yet?) after start: Operation not permitted**
I changed the pidfile option in /etc/redis/redis.conf from /run/redis/redis-server.pid to /var/run/redis/redis-server.pid and restarted the server with sudo systemctl restart redis-server but it still gives same error.
And redis-server.service file under /etc/systemd/system look as following:[/FONT]
```

...
[Service]
Type=forking
ExecStart=/usr/bin/redis-server /etc/redis/redis.conf
PIDFile=/var/run/redis/redis-server.pid
TimeoutStopSec=0
Restart=always
User=redis
Group=redis
RuntimeDirectory=redis
RuntimeDirectoryMode=2755
....

```

[FONT=Arial]It still gives error that it can not read file /run/redis/redis-server.pid. There is no other option with /run/.. elsewhere.
Where does it come from? How can I solve the problem?[/FONT]

---

### Post by TheFu on 2022-04-16
What is the output from 
```
ls -al /run/redis/redis-server.pid
```
That would be the first thing to check.

---

### Post by kahlenberg on 2022-04-16
It is already there: -rw-rw---- 1 redis redis 5 Apr 16 19:08 /run/redis/redis-server.pid and it has a PID number.

---

### Post by TheFu on 2022-04-16
Does redis run using the redis userid? Looks like it should, but .... does the redis uid exist on the system? Check the group at the same time.
```
/var/run/redis$ ll
total 4
**dr[COLOR="#FF0000"]w[/COLOR]xr-sr-x  2 redis redis   80 Apr  6 13:10 ./**
drwxr-xr-x 35 root  root  1220 Apr 16 13:23 ../
-rw-rw----  1 redis redis    5 Apr  6 13:10 redis-server.pid
srwxrwx---  1 redis redis    0 Apr  6 13:10 redis.sock=
```

is what my redis looks like.

Not that my directory is /var/run/redis, but that is just a symlink
```
/var$ ll -d run
lrwxrwxrwx 1 root root 4 Dec 11  2016 run -> /run/
```
so it shouldn't matter.  
```
$ df -Th /run
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs   98M  1.5M   97M   2% /run
```

Is the tmpfs not full there?

---

### Post by kahlenberg on 2022-04-19
What is redis uuid?<br><br>Everything looks normal:<br><br>

```

$ ll /var/run/redis
total 4,0K
   0 drwxr-sr-x  2 redis redis   60 Apr 19 08:23 ./
   0 drwxr-xr-x 41 root  root  1,2K Apr 19 11:04 ../
4,0K -rw-rw----  1 redis redis    5 Apr 19 08:23 redis-server.pid
$ df -Th /run
Filesystem     Type   Size  Used Avail Use% Mounted on
tmpfs          tmpfs  1,6G  2,7M  1,6G   1% /run

```

---

### Post by TheFu on 2022-04-19
So it isn't the file system or file.  I don't know enough about redis to guess at any other causes.  Are there any other errors in the logs that can be googled?

I'd check over the /etc/redis/redis.conf for issues too. Alas, I don't know **anything** about it either. I don't recall altering it in any way during setup. My config file is from the setup time in 2016.  In that file, the redis log is configured as /var/log/redis/redis-server.log. Very little inside that, even with 'notify' level. Looks like just 20 entries/day.

Sorry I'm no help.

---

