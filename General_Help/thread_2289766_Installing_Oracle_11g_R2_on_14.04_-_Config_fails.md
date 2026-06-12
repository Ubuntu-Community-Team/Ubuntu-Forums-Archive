---
title: "Installing Oracle 11g R2 on 14.04 - Config fails"
date: 2015-08-06
forum: General Help
---

### Post by jcllings on 2015-08-06
Pursuant to this thread: 
[http://ubuntuforums.org/showthread.php?t=2229006](http://ubuntuforums.org/showthread.php?t=2229006)
Which refers to this HOWTO:
[http://goo.gl/xlY8xn](http://goo.gl/xlY8xn)

I'm seeing: 

```

user@host:~$ sudo /etc/init.d/oracle-xe configure

Oracle Database 11g Express Edition Configuration
-------------------------------------------------
This will configure on-boot properties of Oracle Database 11g Express 
Edition.  The following questions will determine whether the database should 
be starting upon system boot, the ports it will use, and the passwords that 
will be used for database accounts.  Press <Enter> to accept the defaults. 
Ctrl-C will abort.

Specify the HTTP port that will be used for Oracle Application Express [****]:

Specify a port that will be used for the database listener [****]:

Specify a password to be used for database accounts.  Note that the same
password will be used for SYS and SYSTEM.  Oracle recommends the use of 
different passwords for each database account.  This can be done after 
initial configuration:
Confirm the password:

Do you want Oracle Database 11g Express Edition to be started on boot (y/n) [y]:y

Starting Oracle Net Listener...Done
Configuring database...
Database Configuration failed.  Look into /u01/app/oracle/product/11.2.0/xe/config/log for details

```

Looking there, I see:

```

user@host:/u01/app/oracle/product/11.2.0/xe/config/log$ grep ORA * | uniq -u
cloneDBCreation.log:ORA-01034: ORACLE not available
cloneDBCreation.log:ORA-27101: shared memory realm does not exist
cloneDBCreation.log:ORA-00845: MEMORY_TARGET not supported on this system
CloneRmanRestore.log:ORA-00845: MEMORY_TARGET not supported on this system
postDBCreation.log:ORA-01034: ORACLE not available 
postDBCreation.log:ORA-01034: ORACLE not available
postDBCreation.log:ORA-27101: shared memory realm does not exist
postDBCreation.log:ORA-00845: MEMORY_TARGET not supported on this system
postScripts.log:DROP DIRECTORY ORACLE_OCM_CONFIG_DIR

```

**Current assumptions:** 
I forgot or set incorrectly a memory parameter somewhere.

I see :
```

user@host:~$ sudo cat /etc/sysctl.d/60-oracle.conf
[sudo] password for user: 
# Oracle 11g XE kernel parameters
fs.file-max=6815744
net.ipv4.ip_local_port_range=9000 65000
kernel.sem=250 32000 100 128
kernel.shmmax=536870912
```

kernel.shmmax is 512 Mb but I think my machine has 16Gb.

user@host:~$ cat /proc/meminfo | grep MemTotal
MemTotal:       16326920 kB

512 *1024 *1024 == 536870912 (checked with calculator just in case)

16326920k == ( 16326920 *1024 ), i.e. the value in bytes.

If this is the problem, I'm failing to understand why it matters. With 16Gb, there should be plenty of space.

OK, still making progress. I figured out that you can get this value by making sure you move /etc/sysctl.d/60-oracle.conf to ~/ and then restart and look at the value:
```

user@host:~$ grep -n ".*" /proc/sys/kernel/shmm* 
/proc/sys/kernel/shmmax:1:33554432
/proc/sys/kernel/shmmni:1:4096

```
So, I've updated the value in 60-oracle.conf and moved it back to /etc/sysctl.d/. 
[FONT=arial][SIZE=2]
Followed that by:
[COLOR=#000000]
sudo service procps start
and then
[/COLOR][/SIZE][/FONT]sudo /etc/init.d/oracle-xe configure

[FONT=arial][SIZE=2][COLOR=#000000]Doing so got me:
[/COLOR][/SIZE][/FONT]
```

...all the stuff we saw before followed by...

Starting Oracle Net Listener...Done
Configuring database...Done
Starting Oracle Database 11g Express Edition instance...Done
Installation completed successfully.

```

Woohoo!! :-)

---

### Post by QIII on 2015-08-06
Hello!

Hopefully someone here will be able to help.  :)

If not, you might try the Oracle Community forum [here]("https://community.oracle.com/community/database/developer-tools/oracle_database_express_edition_xe").  That's for the Express Edition, so I imagine they can help.

---

