---
title: "Squid3 init.d file in saucy"
date: 2013-12-11
forum: General Help
---

### Post by dvb15 on 2013-12-11
Greetings!

I noticed, that the package squid3 (3.3.8-1ubuntu3) in saucy repo misses /etc/init.d/squid3 file, while the package squid3 (3.1.20-1ubuntu3) in raring repo has it. The result is that I can't start squid3 with

```
sudo service squid3 start
```

Is this a bug or I miss something?

---

### Post by r-senior on 2013-12-11
It looks like it's been converted to an upstart job, so there is nothing in /etc/init.d but you will find squid3.conf in /etc/init.

From 'man service':

```
       The   SCRIPT   parameter   specifies   a   System   V   init   script,  located  in
       /etc/init.d/SCRIPT, or the name of an upstart job in /etc/init. The existence of an
       upstart  job of the same name as a script in /etc/init.d will cause the upstart job
       to take precedence over the init.d script.
```

I just installed it on my desktop machine running Saucy and it starts and stops OK:

```
$ sudo service squid3 restart
squid3 stop/waiting
squid3 start/running, process 5080
```

You can use netstat to check if it is listening on the default port, which is 3128:

```
$ sudo netstat -plant | grep 3128
tcp6       0      0 :::3128                 :::*                    LISTEN      5080/squid3
```

Did you get errors when you tried to start it?

EDIT: Note that the config file for squid itself (the rules, cache size and so on) is in /etc/squid3/squid.conf. Don't get confused between this file and /etc/init/squid3.conf.

---

### Post by dvb15 on 2013-12-11
Thanks for your reply. My problem was in configuring squid. It didn't start and I started searching why. Firstly I noticed that bash doesn't suggest squid3 if typing

```
sudo service s[TAB]
```

 Then I figured out, that /etc/init.d/squid3 is missing. I missed the fact, that in raring there was just a link to /lib/init/upstart-job, but not the script itself. Eventually, I made this link and then realized I have to correct errors in squid.conf. Finally, squid started okay. Now I understand, that the command

```
sudo service squid3 start
```

works well even without /etc/init.d/squid3 - bash just doesn't suggest squid3 as a service on [TAB] keypress, as there's no such file in init.d.

---

