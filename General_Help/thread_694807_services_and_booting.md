---
title: "services and booting"
date: 2008-02-12
forum: General Help
---

### Post by arell12 on 2008-02-12
I have a couple questions about Ubuntu hopefully I can get some answers.

First off, I am a little more used to Red Hat and I am able to check on services that are running by using the command service *smb* status but when I try that in Ubuntu it says that the service command is not enabled.  

Another thing, if i do a sudo apt-get install openssh-server, (just as an example) does that service start when I restart Ubuntu?  How do you define what services start or dont start?

Thanks, I am sure I will have more questions but that is it for now.

---

### Post by PeterJS on 2008-02-12
For seeing what services are being started up when the system boots, the services manager is in the menu at System > Administration > Services. For checking what services are running I usually use the init script in /etc/init.d/*servicename* with a paramater of status, some scripts support that, some don't. For the ones that don't a combination of ps and grep usually gets the job done.

---

### Post by ptn107 on 2008-02-12
"The default runlevel on Ubuntu is runlevel 2, in which all the services that have to be
started are referred to. Before entering runlevel 2, Ubuntu passes through runlevel S. In
this runlevel, all the essential services that are always required are started. The
configuration of both works in more or less the same way.

To understand the working of a runlevel, you need to understand two components: the
service scripts and the scripts that execute these service scripts. All of the service scripts are
found in the /etc/init.d directory, and they are used to start fundamental services such as
the mounting of file systems as well as network services like your Apache server. To specify
which of these scripts have to be executed when starting your server, two runlevel-related
directories are used. The first of these directories is /etc/rcS.d, and, on a system that follows
a default installation, the second of them is /etc/rc2.d. In the /etc/rcS.d directory, services
are started that are always needed, whereas, in the /etc/rc2.d directory, services are started
that are specific to a given runlevel.

To make sure that a service starts automatically during system initialization, a symbolic
link is created in the /etc/rcS.d directory. The name of this link starts with an S, followed by a
two-digit number, followed by the name of the script in /etc/init.d that the link refers to. All
these links are processed when booting your server, and they are processed in alphabetical
order. So S01blah is processed before S99blah.

The same thing happens for the runlevel directories, with the difference that, when work-
ing with runlevels, there is an option to change the current runlevel. When changing a runlevel,
some scripts may have to be started as well. To do this, more symbolic links are created. The
name of these links starts with K, followed by a two-digit number.

If you want to make sure that a given service is started automatically, it follows that you
first need to make sure that it has a service script in /etc/init.d. If it does, you next need to
make a symbolic link for this service. If it is a service that has to be started when your server is
booting, you just need a start link in /etc/rcS.d. If it is a service that you want to be included
in your server’s runlevels, you need to create a start link as well as a stop link in the directory of 
the default runlevel, which would be /etc/rc2.d in most cases."

References:
Vugt, Sander van (2008).  *Beginning Ubuntu Server Administration*.
          Berkeley, CA: Apress.

---

### Post by arell12 on 2008-02-12
thanks for the run down on services.  I understand better now about the services and how they start.  Lets say I wanted to restart a service with out rebooting how could i do something like that?  Again referencing what I know in Red hat I was able to do something like *service smb restart *and it would show the service stop and start.

---

### Post by PeterJS on 2008-02-12
For ubuntu you'd use:
```

sudo /etc/init.d/smb restart

```

---

