---
title: "Problems with web servers"
date: 2005-09-06
forum: General Help
---

### Post by vhalen on 2005-09-06
Hey guys,

I'm new with ubuntu (I was Fedora user) and I want to know how to configure my machine to use apache/php/mysql/java to develop my softwares :)

I can't find apache, php and mysql services to start and use it. I was downloaded ubuntu by official mirrors and installed desktop choice.

Thanks and sorry my english :p

Ronaldo

---

### Post by xy77 on 2005-09-06
Welcome to ubuntu and welcome to this forum.

You might want to check out [www.ubuntuguide.org](www.ubuntuguide.org) to get started (make sure you read the section on additional repositories). In your particular case, you will want to install the appropriate packages (apache, modules, etc.) which you can do via synaptic or apt-get.

In order to re/start a service manually, execute
```

$ /etc/init.d/<service> start
# or
$ /etc/init.d/<service> restart

```

If you have no /etc/init.d/apache2 you have not installed apache yet.

- David (xy77)

---

### Post by bfonseca on 2005-11-30
[QUOTE=xy77]Welcome to ubuntu and welcome to this forum.

You might want to check out [www.ubuntuguide.org](www.ubuntuguide.org) to get started (make sure you read the section on additional repositories). In your particular case, you will want to install the appropriate packages (apache, modules, etc.) which you can do via synaptic or apt-get.

In order to re/start a service manually, execute
```

$ /etc/init.d/<service> start
# or
$ /etc/init.d/<service> restart

```

If you have no /etc/init.d/apache2 you have not installed apache yet.

- David (xy77)[/QUOTE]

Hi, I was hoping someone here could help me with my problem.  I have installed apache from synaptic. When I try

bfonseca@12:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server (Apache2)...                                      [ ok ]
bfonseca@12:~$ sudo /etc/init.d/apache2 start
bfonseca@12:~$ sudo /etc/init.d/apache2 restart

for some reason my start and restart are not working. Any advice on how I can fix this problem.  Any help would be greatly appreciated.
Thank
Brian

---

### Post by simgish on 2005-12-02
What does your error log say?
```
$ tail /var/log/apache2/error.log
```

---

