---
title: "SSHD will not start using service or /etc/init.d"
date: 2013-11-15
forum: General Help
---

### Post by Spuds on 2013-11-15
```
root@www:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 13.10
Release:        13.10
Codename:       saucy
```

SSHD won't run, won't start with upstart / system ssh start or init.d, but if I login and sudo to root or run sshd using sudo, sshd runs fine.

I have been having this problem on a few of our servers for over a year.  Sometimes a reboot would help, sometimes it wouldn't.  Now they don't run at all.

The problem has existed in previous versions, sometimes fixed through release upgrades, though temporarily.

I have:

apt-get remove --purge openssh-server
apt-get install openssh-server
dpkg-reconfigure ssh-server
removed the /etc/ssh directory and done both of the above
apt-get install openssh-server
scoured auth.log (NOTHING)
Tried explicitly setting port and IP in sshd_config


There is simply no sign that sshd is even trying to start and failing.  Logging is set to debug.

sshd -t doesn't output anything.

```
root@www:/# sshd -t
root@www:/#
```

And more nothing:

```
root@www:/# service ssh start
ssh stop/pre-start, process 23617
root@www:/# ps aux | grep sshd | grep -v grep
root@www:/#
```

Nothing here, either:

```
root@www:/# /etc/init.d/ssh start
root@www:/# ps aux | grep sshd | grep -v grep
root@www:/#

```

So now I'll run as root:

```
root@www:/# sshd -d
sshd re-exec requires execution with an absolute path
```

Oops!  Okay.

```
root@www:/# /usr/sbin/sshd -d
debug1: sshd version OpenSSH_6.2, OpenSSL 1.0.1e 11 Feb 2013
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
```

No problem.  Now I can log in.

I can provide any other information you need.  

-Spuds

---

### Post by brijin on 2013-11-15
after purging, installing the openssh-server package again would help?

---

### Post by Spuds on 2013-11-15
Let's assume that I *do* have the package installed.

---

### Post by steeldriver on 2013-11-15
I'm guessing here, but since it *appears* to hang in the upstart pre-start phase, would it be worth running the steps of that one at a time and seeing if anything is failing?

```

$ cat /etc/init/ssh.conf
# ssh - OpenBSD Secure Shell server
.
.
.
pre-start script
    test -x /usr/sbin/sshd || { stop; exit 0; }
    test -e /etc/ssh/sshd_not_to_be_run && { stop; exit 0; }
    test -c /dev/null || { stop; exit 0; }

    mkdir -p -m0755 /var/run/sshd
end script
.
.
.

```

i.e.

```

test -x /usr/sbin/sshd ; echo $?

test -e /etc/ssh/sshd_not_to_be_run ; echo $?

test -c /dev/null ; echo $?

```

Obviously we don't expect the first one to fail since you can start sshd manually - but the other 2 might flush something out (maybe /dev/null isn't character special for some reason?)

Does /var/run/sshd exist and have the indicated permissions?

---

### Post by Spuds on 2013-11-15
You're onto something:

```
root@www:~# test -x /usr/sbin/sshd ; echo $?
0
root@www:~# test -e /etc/ssh/sshd_not_to_be_run ; echo $?
1
root@www:~# test -c /dev/null ; echo $?
1
```

I can tell you that we've been having /dev/null permissions problems for years.  It used to be that whenever we logged in, we'd get a dozen or so:

/dev/null:  Permission Denied

errors before we got our command prompt.  I managed to suppress those, but not fix the underlying problem.  I've searched and searched with no success.

The two problems may yet be related.

/var/run/sshd exists and has the indicated permissions:

```

root@www:/run# ls -al | grep sshd
drwxr-xr-x  2 root  root    40 Nov 15 09:06 sshd

```

---

### Post by steeldriver on 2013-11-15
So what is

```
ls -l /dev/null
```

It should be

```
crw-rw-rw- 1 root root
```

---

### Post by Spuds on 2013-11-15
> **steeldriver said:**
> It should be

```
crw-rw-rw- 1 root root
```

It wasn't before-- but it is now!

---

### Post by Spuds on 2013-11-15
ALL affected servers had a bad /dev/null

How does this happen?

I have connected users so I can't see if this fixed the problems-- but what are the chances this is the cause of my SSHD issue?

---

### Post by Spuds on 2013-11-15
SOLVED

You guys, as always, are the best.

---

### Post by rein2 on 2014-02-27
How did you manage to solve the problem? I am having the same issue. I can run the sshd from /usr/sbin/ssh-d but when I try to sudo service sshd status, nothing happens. I have tried to purge and reinstall the package, no change.

---

### Post by Spuds on 2014-03-12
In case you haven't figured it out yet-- and it took me a lot of time to figure it out, /dev/null was being overwritten by a script that was installed by the VPS provider.  So look at all of your scripts to see if one of them is doing it.  I had a script that checked the status of the file every few milliseconds and wrote the result to a file.  When the device changed a few times, I just compared the timestamps to find out how often it was being changed, checked my cron jobs and found the culprit.

Let me know if I can provide any more (timely) assistance.

---

