---
title: "All of my logs in /var/log are blank and not poplulating"
date: 2008-04-28
forum: General Help
---

### Post by headlice on 2008-04-28
Just what the title says.  I dont see how logging got turned off or how to even turn it back on.  Sits behind a router with a good password and intrusion detection, so I dont think anyone else was messing around....

ETA: running 8.08 server w/o desktop

---

### Post by Monicker on 2008-04-28
> **headlice said:**
> Just what the title says.  I dont see how logging got turned off or how to even turn it back on.  Sits behind a router with a good password and intrusion detection, so I dont think anyone else was messing around....

ETA: running 8.08 server w/o desktop


Are klogd and syslogd running?

```
ps aux |grep klogd
ps aux |grep syslog

```


If they are not running:

```
sudo /etc/init.d/klogd start
sudo /etc/init.d/sysklogd start
```

---

### Post by ghost_ryder35 on 2008-04-28
how  bout
```

dmesg

```
is that working?

---

### Post by headlice on 2008-04-28
> **Monicker said:**
> Are klogd and syslogd running?

```
ps aux |grep klogd
ps aux |grep syslog

```


If they are not running:

```
sudo /etc/init.d/klogd start
sudo /etc/init.d/sysklogd start
```


K well this is obviously the problem.  and starting them manually did not work....

---

### Post by Monicker on 2008-04-28
> **headlice said:**
> K well this is obviously the problem.  and starting them manually did not work....

What error message did you receive when trying to start those services?

---

### Post by headlice on 2008-04-28
The only thing that I can think of that happened was I went into my router and enabled syslogd on it, and added my server as a remote server just to see what would happen.

I turned it off and rebooted router.  Logging still not working on the server...

---

### Post by headlice on 2008-04-28
> **Monicker said:**
> What error message did you receive when trying to start those services?

no message returned.  when I look for it in the active processes it is still not there

---

### Post by Monicker on 2008-04-28
> **headlice said:**
> The only thing that I can think of that happened was I went into my router and enabled syslogd on it, and added my server as a remote server just to see what would happen.

I turned it off and rebooted router.  Logging still not working on the server...


Running syslogd on the router should not affect the workstation.  Did you alter anything in /etc/syslog.conf?


Try these commands to see if we can get any useful information about where things are going wrong:

```
sudo klogd -d
sudo syslogd -d -u syslog
```

---

### Post by headlice on 2008-04-28
omg I dont know wtf happened...

```
ps aux | grep log
```

showed 2 log processes running, niether were system and kernal.

ran ```
syslogd -d
```

came back with ```
The program 'syslogd' can be found in the following packages:

 * sysklogd

 * inetutils-syslogd

Try: apt-get install <selected package>

bash: syslogd: command not found
```

apt-get install syslogd didnt work.

```
apt-get install klogd
``` worked and now BOTH are up and running.

Thanks guys.  I still dont know what happened and how they got removed.  They WERE working before yesterday.

---

