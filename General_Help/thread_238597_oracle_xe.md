---
title: "oracle xe"
date: 2006-08-17
forum: General Help
---

### Post by DagonX on 2006-08-17
I installed the oracle xe database that came in a Debian package. It seemed to install ok. When I tried to access the home page I received tUnable to connect 
      
Firefox can't establish a connection to the server at 127.0.0.1.

*   The site could be temporarily unavailable or too busy. Try again in a few moments.

*   If you are unable to load any pages, check your computer's network
          connection.

*   If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.he following error:

Is this a permission problem? If it is how do I fix the permissions? I can't find where the Debian package manager stuck everything or else I would chmod everything to universal read/write/execute.

I can apparently start and stop the database. So the database appears to be running.

Charles

---

### Post by acidix on 2006-08-24
hi charles,

please be sure to enter the right url: [http://localhost:8080/apex](http://localhost:8080/apex)

thomas

---

### Post by fleenort on 2007-04-07
Sorry for posting to an older thread. I have read thru the others regarding Oracle 10g XE and I can't seem to find this problem anywhere else.

A short explanation of what I've done so far:

1) First, I installed Oracle 10g XE from the Oracle website.
2) After reading a few threads, I looked in Synaptic and realized that once I had added the repository and gotten a key, Oracle DID show up as available to install from Synaptic
3) I uninstalled (removed completely from Synaptic)
4) I re-installed using Synaptic this time
5) I ran the configure script...

I have tried many variations on [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex)
Including swapping out 127.0.0.1 for localhost, taking off the 8080 and switching http to https... ETC.

Anyone have a solution beyond making sure the address is correct? I'm clicking on "Go To Database Homepage" from the Application menu to get there.

If I just try going to the SQL command line and connect as "system", I get this:

[INDENT]/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found

SQL*Plus: Release 10.2.0.1.0 - Production on Sat Apr 7 16:43:52 2007

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

SQL> connect 
Enter user-name: system
Enter password: 
ERROR:
ORA-01034: ORACLE not available
ORA-27101: shared memory realm does not exist
Linux Error: 2: No such file or directory
[/INDENT]

Thanks for any help,
Fleenort

---

### Post by arodelo on 2007-07-25
it looks that you need to configure oracle,
so goto /etc/init.d
and run oracle-xe configure

respond the question and reboot your machine.
it should be fine now.

---

### Post by Elrie on 2007-08-09
Hello, all!

I have the similar problem.

HTTP access to my XE installation doesn't work.
I'm running it on Edubuntu 7.04
Oracle XE Universal from Oracle web site.

The oracle client acces to database works fine.
So I can connect using sqlplus or SQL Developer from localhost and from remote host.

It seems that http listener is started, as it appears in 'netstat -ano'
If use telnet to XE http port I get 'connected' and silence (but on working installation it's the same).

But using any browser I could'n see Apex home page

I tryed differnet ports: 8080, 7777, etc. Doesn't matter.

So I can't understand what happens and why it doesn't work properly.

I thought that it is porblem connected with iptables, but if I set any rules it doesn't change anything.

I have the similar installation on other box, but running simple Ubuntu 7.04 - it works excellent.

Any ideas?

---

### Post by korny on 2007-08-09
> **fleenort said:**
> 
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found


This probably is irrelevant for the rest of your problem, but the above error is because the shell script starts with "#!/bin/sh" but uses bash syntax.  I think on some unixes /bin/sh is just a link to /bin/bash, so on those systems this works.  You can edit the file above and change #!/bin/sh to #!/bin/bash and this part at least will work.

(this advice is probably wildly out of date but may help someone else who sees this thread!)

---

### Post by korny on 2007-08-09
If you can get in to sqlplus as system you can find the port that is used:
  select dbms_xdb.getHttpPort() from dual;
  select dbms_xdb.getFtpPort() from dual;
If you don't know the system password you might be able to log in as a dba as follows :
  sudo sqlplus "/ AS SYSDBA"
(This doesn't seem to work for me, but I suspect I have to set up root as a dba somehow... it has worked for me on other oracle systems in the past though, and can be a life saver!)

If you want to change the port used, you can do it from sqlplus as well:
  exec dbms_xdb.setHttpPort(9000);
  exec dbms_xdb.setFtpPort(0);

Hope this helps...

---

### Post by Elrie on 2007-08-10
All the things connected with simple clients (sqlplus, SQL Developer) are ok.
I can do any operations with DB.

The problem is only with HTTP access, and it doesn'd depend on port used, as I tryed different.

At last  I've found in log files this:

```

10-AUG-2007 11:14:25 * http * (ADDRESS=(PROTOCOL=tcp)(HOST=127.0.0.1)(PORT=33815)) * handoff * http * 12518
TNS-12518: TNS:listener could not hand off client connection
 TNS-12571: TNS:packet writer failure
  TNS-12560: TNS:protocol adapter error
   TNS-00505: Operation timed out
    Linux Error: 110: Connection timed out

```

---

### Post by Elrie on 2007-08-10
Hm...

I've found problem at last.

Default configuration seems doesn't work on the box that have 2 network interfaces.
So, I just made some adjustments to listener to be on one defined interface, and no all is ok.

---

### Post by Stettin on 2007-09-19
How exactly did you do that? I have a machine with 2 NICs here at work (I can't remove one), booting to my USB drive to run Ubuntu.

---

### Post by enavarro on 2007-12-06
> **korny said:**
> This probably is irrelevant for the rest of your problem, but the above error is because the shell script starts with "#!/bin/sh" but uses bash syntax.  I think on some unixes /bin/sh is just a link to /bin/bash, so on those systems this works.  You can edit the file above and change #!/bin/sh to #!/bin/bash and this part at least will work.

(this advice is probably wildly out of date but may help someone else who sees this thread!)

I would like to thank korny, this solved my problem, I configured oracle and everything nicely but got this and it was annoying. BTW im using Xubuntu 7.10 with Oracle 10g Express Edition.

---

### Post by remusc on 2008-03-02
Hi,

I encountered the same problem after I have installed OracleXE/Ubuntu 7.10 with the access to [http://127.0.0.1:8080/apex](http://127.0.0.1:8080/apex).

The problem was with the listener which didn't started when I started also the DB.
For starting the DB you should give to the current user, dba privileges.

For starting the listener, you should login as user 'oracle' and start the listener.
 (I have also changed previously the oracle password)
su - oracle -p
lsnrctl start

This issue was due because, I have chosen not to start automatically the DB when I configured with /etc/init.d/oracle configure.

I wonder how I can start the listener with the current account and not the oracle account.

I have 2 card (Wireless and eth) and the whole installation was done with the wlan interface activated (on some forums it is said that the wireless connection can generate problems, which was not my case).

Regards,
Remus

---

### Post by mstrello on 2008-04-19
When you set a password for the listener, the user must supply the correct password before issuing some damaging commands such as stopping the listener. Note: this behavior is different across Oracle versions. In Oracle 9i and earlier, a password, if set, applies to any user trying to manipulate the listener. In Oracle 10g and later, the Oracle software owner without a password can manipulate the listener. So, if a user other than the software owner tries to manipulate the listener, he has to supply the correct password, else he gets the following error:

TNS-01190: The user is not authorized to execute the requested listener command

Extracted from 
[http://www.dba-oracle.com/t_tns_01190_listener_password_security_authorization.htm](http://www.dba-oracle.com/t_tns_01190_listener_password_security_authorization.htm)

This was a very serious flaw for Oracle 9i and previous versions (nobody remember to set the password!).

---

