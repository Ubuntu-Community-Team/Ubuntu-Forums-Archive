---
title: "Message file sp1&lt;lang&gt;.msb not found - Instant Client"
date: 2007-04-28
forum: General Help
---

### Post by bagadonitz on 2007-04-28
I have a full oracle install on a desktop windows box for development.

I develop on another desktop with Ubuntu 7.04.  I use most oracle tools on the windows box but our build is quite well automated with a frequently used task to refresh the database.  Part of this task, using ant, calls SQLPlus to set up various stored procs etc on the database.

I have a tnsnames.ora set up as follows:

[b]
```

ROWROW-JB =
  (DESCRIPTION =
    (ADDRESS_LIST =
      (ADDRESS = (PROTOCOL = TCP)(HOST = 192.168.369.430)(PORT = 1521))
    )
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = rowrow)
    )
  )

```
[/b]

Having this in place, the actual log in for my executing application can connect to this database no problem.  As can my unit tests.  They use the oracle jdbc driver of course.

I can not get SqlPlus to connect however.  First, if I have the environment variables set as follows, I get the result after it:

[b]
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/baga/instantclient_10_2/:/home/baga/idea-6810/bin/
ORACLE_HOME=/home/baga/instantclient_10_2/
LD_LIBRARY_PATH=/home/baga/instantclient_10_2/
ORACLE_SID=rowrow

```
[/b]
Result:
[b]
```

baga@enghlol:~$ sqlplus DEV_BAGA/rowrow@192.168.369.430
Error 6 initializing SQL*Plus
Message file sp1<lang>.msb not found
SP2-0750: You may need to set ORACLE_HOME to your Oracle software directory

```
[/b]

Being as I have the lastest available instant client with sqlplus add on package laid over it, I don't have sp1<lang>.msb in ORACLE_HOME nor anywhere else on the system.  I searched for sp1us.msb as well, not on here.

I read in a thread somewhere to drop the ORACLE_HOME variable.  So if my variables look like this:

[b]
```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/baga/instantclient_10_2/:/home/baga/idea-6810/bin/
LD_LIBRARY_PATH=/home/baga/instantclient_10_2/
ORACLE_SID=rowrow

```
[/b]

Then I get the following results:

[b]
```

baga@enghlol:~$ sqlplus DEV_BAGA/rowrow@192.168.369.430
SQL*Plus: Release 10.2.0.3.0 - Production on Fri Apr 27 20:03:06 2007
Copyright (c) 1982, 2006, Oracle.  All Rights Reserved.
ERROR:
ORA-12514: TNS:listener does not currently know of service requested in connect descriptor
Enter user-name: DEV_BAGA
Enter password: 
ERROR:
ORA-12545: Connect failed because target host or object does not exist

```
[/b]

What am I missing here?  I admit, an sqlplus expert I am not.  I'm a java developer.  However I'm building it the same way the args are passed to it via our ant scripts which work on the windows box:

[b]
```

        <exec dir="${database.dir}/packages" executable="sqlplus">
            <arg value="${oracle-user-id}/${oracle-password}@${oracle-server}"/>
            <arg value="@GitErDone.sql"/>
        </exec>

```
[/b]

Any help would be greatly appreciated.

---

### Post by bagadonitz on 2007-05-01
TTT

Anyone?

---

