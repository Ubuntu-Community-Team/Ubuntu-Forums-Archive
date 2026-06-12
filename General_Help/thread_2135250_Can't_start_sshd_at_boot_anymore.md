---
title: "Can't start sshd at boot anymore"
date: 2013-04-13
forum: General Help
---

### Post by karnalta on 2013-04-13
Hi all,

Since yesterday my ubuntu server 12.04 does not start sshd deamon at boot anymore. I have searched a lot on internet for a solution but nothing seem to work for me and it's driving me crazy.

After having removed and reinstalled openssh-server to reset all, it's still doesn't work.

When I look into /var/log/dmesg, here is the end on my file :

```

[   14.013088] init: ssh main process (1266) terminated with status 1
[   14.013163] init: ssh main process ended, respawning
[   14.048528] init: ssh main process (1277) terminated with status 1
[   14.048600] init: ssh main process ended, respawning
[   14.092116] init: ssh main process (1293) terminated with status 1
[   14.092188] init: ssh main process ended, respawning
```

When I try to start it manually in different way, I get only one working method :

NOT WORKING :
```

start ssh
ssh start/running, process xxxx
status ssh
ssh stop/waiting
```

NOT WORKING :
```

/etc/init.d/ssh start
Blablabla method deprecated...
ssh start/running, process xxxx
/etc/init.d/ssh status
Blablabla method deprecated...
ssh start/running, process xxxx
ssh stop/waiting
```

WORKING :
```

/usr/sbin/sshd
```

Anyone have a idea about my problem ? I can't reboot the server remotely anymore if SSH doesn't start at boot anymore, it's really boring.

Thank you for your help.

---

### Post by rnerwein on 2013-04-13
hi
try: service ssh restart
ciao

---

### Post by karnalta on 2013-04-14
> **rnerwein said:**
> hi
try: service ssh restart
ciao

Thank but it doesn't work.

Anyway I can start it manually, but I'd like it to run on startup like before.

Where should I look to get a bit more info about my spawning error ?

---

### Post by karnalta on 2013-04-14
Ok I solved my issue.

So if it can help someone ..

I first changed the line "console none" to "console log" in the ssh upstart job script (/etc/init/ssh), so I could now look into /var/log/upstart/ssh.log after the server boot to see the error.

Here was the error I got into it :

```
140273233532560:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:618:line 4
```

A quick google search pointed me out that this error was caused by environment variable that could not be resolved in the config file.

After a lot of search I found that I had to comment these 3 lines in my /etc/ssl/openssl.cnf :

```
#RANDFILE       = $ENV::HOME/.rnd
#oid_file       = $ENV::HOME/.oid
#oid_section                    = new_oids

```

Now my sshd startup normaly again on server boot.

What I don't really get, is why an error in the SSL configuration file was affecting the SSH execution.. I had a lot a luck to find it out because I was sure the error was concerning /etc/ssh/sshd_config.

---

