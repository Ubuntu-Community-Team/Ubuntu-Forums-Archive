---
title: "Ground works monitoring"
date: 2014-02-25
forum: General Help
---

### Post by aaron27 on 2014-02-25
Hello, 

We have installed Groundworks Server  Monitor onto our Ubuntu 13.10 install, however when trying to start the  services to access the portal we are faced with the following error:

FATAL: deployment of foundation-webapp.war timed out

Does anyone know the fix for this or has anyone come across a similar issue regarding this? We have followed all setup and install instructions to the book but cannot find a way of fixing this. 
any advice would be greatly received.

KR 
Aaron

---

### Post by tgalati4 on 2014-02-25
As I suspected, many enterprise services (including monitoring) expect a Long Term Support enterprise distro to work properly:

[https://kb.groundworkopensource.com/display/SUPPORT/Installing+or+Upgrading+to+GroundWork+Monitor+7.0.1#InstallingorUpgradingtoGroundWorkMonitor7.0.1-SystemRequirements](https://kb.groundworkopensource.com/display/SUPPORT/Installing+or+Upgrading+to+GroundWork+Monitor+7.0.1#InstallingorUpgradingtoGroundWorkMonitor7.0.1-SystemRequirements)

    Red Hat Enterprise Linux 5 Server and 6 Server, 64-bit.
    CentOS 5 and 6, 64-bit.
    Novell SuSE Linux Enterprise Server 10 and 11, 64-bit.
    Ubuntu Server 8.04 LTS, 9.10, 10.04, 12.04, 64-bit. Releases before Ubuntu 12.04 are not recommended, because starting and stopping ntop on the earlier releases is broken.

So spin up a virtual machine and put 12.04 on it and see if it works.  The monitor requires a pretty hefty machine, so don't put it on a laptop.

---

### Post by aaron27 on 2014-02-26
That doesnt really answer my question as we are running 64bit Ubuntu server 13.10

---

### Post by tgalati4 on 2014-02-26
It is not supported on 13.10.  Try putting on a 12.04 machine.

---

### Post by aaron27 on 2014-02-28
Ok reinstalled with 12.04 however now I get the following:

**HTTP Status 404 -**

[HR][/HR]**type** Status report
**message** 
**description** _The requested resource () is not available._
[HR][/HR]**JBoss Web/7.0.17..Final-redhat-2**


any advice? (all services have been started)

---

### Post by tgalati4 on 2014-02-28
That is a strange error.  I presume that you installed an Ubuntu edition of GroundWorks and not a RedHat version.  Now would be a time to post a support request on the GroundWorks forums.

---

### Post by aaron27 on 2014-02-28
I have indeed made sure that I have the Ubuntu version not redhat, I have signed up to to their own forum however their administrator hasn't activated my account yet so cannot post there yet. I was hoping someone here would have some idea of whats happening.

---

### Post by tgalati4 on 2014-02-28
I've only played with it last year and it worked out-of-the-box.  I don't use it on a day-to-day basis, so unless someone else has the same error, you will have to ping their forums.  Do you have the jboss server running?

```
ps -ef | grep jboss
```

It could be a conflict in the jboss versions running.

---

### Post by aaron27 on 2014-03-03
Ok I will boot it up this morning and see if the jboss is running, how can i resolve a conflict of jboss' ? Uninstall / reinstall? (if so how please :D )

---

### Post by aaron27 on 2014-03-03
I ran that command, jboss is running, however i noticed the services werent up and running correctly so i have now resolved that and double checked that all the services are up and running correctly. BUT i still have the same issue as before.

---

### Post by aaron27 on 2014-03-03
Ok I have the route of the issue, there is a problem with the postgresql service. when i run the command to start the portal it says broken and all services expcet sql are running. When i try and start the service on its own i get this:

administrator@server33:~$ sudo service groundwork start postgresql
waiting for server to start........ stopped waiting
pg_ctl.bin: could not start server
Examine the log output.
/usr/local/groundwork/postgresql/scripts/ctl.sh : postgresql  could not be started

Any help??????

---

### Post by tgalati4 on 2014-03-03
That would be a problem.  There should be /var/log/postresql log files that you can look through.  Postgres requires some setup.  It's possible that one of the configuration steps failed so the service will not start correctly.  There should be some database troubleshooting tutorials on the groundworks website.

---

### Post by aaron27 on 2014-03-05
Aaaah there is the issue, on the install for groundwork's it doesn't mention that it needs any setup so it is literally just installed on the machine. Ive looked through their website but not found anything of use yet

---

### Post by aaron27 on 2014-03-12
seriously. 600+ views and no one replies? no wonder people stick with windows!
](*,)](*,)](*,)](*,):x:x:confused:

---

### Post by tgalati4 on 2014-03-12
#601.  You are requesting help on a general Ubuntu help forum for a server and service-specific problem.  Your questions are more properly directed to the GroundWorks forum.  In regards to Postgres, have you gone through the documentation?  If you need dedicated support, I suggest you purchase it from GroundWorks or Canonical directly.  In the meantime, keep reading.

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

---

### Post by Iowan on 2014-03-12
> **aaron27 said:**
> seriously. 600+ views and [COLOR="#FF0000"]no one[/COLOR] replies? no wonder people stick with windows!

If I were **tgalati4**, I'd be a bit offended...

---

### Post by aaron27 on 2014-03-13
> **Iowan said:**
> If I were **tgalati4**, I'd be a bit offended...

It wasnt aimed at him, more the fact that everyone else views it and doesnt bother trying to help.

---

### Post by aaron27 on 2014-03-13
> **tgalati4 said:**
> #601.  You are requesting help on a general Ubuntu help forum for a server and service-specific problem.  Your questions are more properly directed to the GroundWorks forum.  In regards to Postgres, have you gone through the documentation?  If you need dedicated support, I suggest you purchase it from GroundWorks or Canonical directly.  In the meantime, keep reading.

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

Ok thanks, as i said i have signed upto their forum but i cannot post anything. I have contacted the admin but im beginning to give up hope and look for alternatives.

---

### Post by tgalati4 on 2014-03-14
I run *mysql* on my servers, so I can't really provide any advice on how to set up postgresql.  I can't help what I don't have experience with.  Running servers and setting up databases assumes that you have a certain level of linux knowledge.  Most of these monitoring services (and there are several) have a setup script that sets up the basic database accounts, tables, and fields that are needed by the service.  Then there is a control script that starts and stops the database server and the monitoring server.  If you can't get help from GroundWork, then try another monitoring package.  There are several.

I currently have datadog running and it has a lot of neat features. [http://datadoghq.com](http://datadoghq.com)

I can understand the OP's frustration at lack of help, but I can't handhold someone when I don't have direct experience with his problem.  I this case, I can only point in the general direction and let the OP try to figure it out.  If the OP needs to monitor machines in an IT capacity, then he will have to figure it out anyway.

---

### Post by Habitual on 2014-03-14
> **aaron27 said:**
> seriously. 600+ views and no one replies? no wonder people stick with windows!

Don't take it personally, I for one, viewed this topic several times a day and that counts. Even though I couldn't offer a solution, I still monitor 
the progress of the post.

Peace.

---

