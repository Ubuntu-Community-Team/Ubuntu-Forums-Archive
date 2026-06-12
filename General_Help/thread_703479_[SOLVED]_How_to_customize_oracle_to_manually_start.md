---
title: "[SOLVED] How to customize oracle to manually startup/shutdown ?"
date: 2008-02-21
forum: General Help
---

### Post by sourabhsharma149 on 2008-02-21
Hello Friends,

I am having Oracle 10g XE installed on Gutsy..It is working fine..
I want to make it custom startup and shutdown..(As of now it is starting up when gutsy boots) as it is not required  Oracle to run each time...Please suggest the way to do it.

Thanks in Advance

---

### Post by Beefeater on 2008-02-22
Hi,

edit
/etc/default/oracle-xe
and change ORACLE_DBENABLED to false

Then to start Oracle I run
/etc/init.d/oracle-xe restart
as start and stop doesn't work.
Hmm, might look into that now.

---

### Post by sourabhsharma149 on 2008-03-03
Cheers Man !!

You suggestion did the trick......

I am able to configure oracle startup by changing the parameter.

From started OS I use sqlplus:


Enter user-name: sys/password as sysdba
Connected to an idle instance.

SQL> startup
ORACLE instance started.

Total System Global Area  289406976 bytes
Fixed Size                  1258488 bytes
Variable Size              96472072 bytes
Database Buffers          188743680 bytes
Redo Buffers                2932736 bytes
Database mounted.
Database opened.
SQL> shutdown
Database closed.
Database dismounted.
ORACLE instance shut down.
SQL>

---

