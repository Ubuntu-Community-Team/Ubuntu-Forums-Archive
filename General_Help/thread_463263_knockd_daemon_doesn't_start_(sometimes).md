---
title: "knockd daemon doesn't start (sometimes)"
date: 2007-06-03
forum: General Help
---

### Post by Darkriser on 2007-06-03
Sometimes, when I restart my PC, log in to Ubuntu, and run 
```
sudo cat /var/log/knockd.log
```

I see following entries
```
[2007-06-03 20:53] waiting for child processes...
[2007-06-03 20:53] shutting down
```

Why knockd daemon is unable to start?

Thanx for help,
Marcel

---

### Post by rklauco on 2007-06-04
Provide a copy of the config file, otherwise there is no way how to help.

---

### Post by Darkriser on 2007-06-05
/etc/knockd.conf
```
[options]
	logfile = /var/log/knockd.log

[opencloseSSH]
	sequence    	= <port1>,<port2>,<port3>
	seq_timeout 	= 15
	start_command   = /sbin/iptables -A TRUSTED -s %IP% -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
	tcpflags	= syn
	cmd_timeout 	= 20
	stop_command    = /sbin/iptables -D TRUSTED -s %IP% -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
```

/etc/default/knockd
```
################################################
#
# knockd's default file, for generic sys config
#
################################################

# control if we start knockd at init or not
# 1 = start
# anything else = don't start
START_KNOCKD=1

# command line options
# KNOCKD_OPTS="-i eth0"
```

---

### Post by rklauco on 2007-06-06
The seq timeout **must** be bigger than the command timeout.
But that does not explain why the daemon exists.

Try to set command line options in the config to run in DEBUG mode
```

KNOCKD_OPTS="--debug --verbose"

```
(do not forget to remove the hash...).

The only option that came to my mind is wrong runlevel or problem with services startup order.

---

### Post by Beacon11 on 2008-05-02
(sorry for reopening an old thread) I don't suppose the times it didn't work was when you didn't have eth0 active? Knockd defaults to eth0, and when Ubuntu runs it on boot, it runs it with the default settings. Knockd will fail if it can't get an IP address from eth0, which is the problem I had. In fact, I'm trying to solve it right this second. I use wireless (eth1) more than I use wired (eth0) so I need this.

UPDATE: To fix the default using eth0, do the following:

```

sudo vi /etc/init.d/knockd

```

At the top of that file, you'll see something like:

```

...
...
OPTIONS=" -d"
...
...

```

All you need to do it change that to:

```

...
...
OPTIONS="-i eth1 -d"
...
...

```

That solved my problem!

---

