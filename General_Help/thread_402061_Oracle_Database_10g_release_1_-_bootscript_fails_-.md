---
title: "Oracle Database 10g release 1 - bootscript fails - insufficient privliges"
date: 2007-04-05
forum: General Help
---

### Post by secutus on 2007-04-05
Hello,

I have a small problem with a dbora bootscript I created for the Oracle Database 10g release 1. 
A small extract of the code is shown below:

#!/bin/bash
#
# /etc/init.d/dbora
#
# Startup script for Oracle databases

export ORACLE_HOME=/u01/app/oracle/product/10.1.0/db_1
export ORACLE_SID=test
export PATH=$PATH:$ORACLE_HOME/bin
ORA_OWNR="oracle"

# if the executables do not exist -- display an error

if [ ! -f $ORACLE_HOME/bin/dbstart -o ! -d $ORACLE_HOME ]
then
	echo "Oracle startup: cannot start (ORACLE_HOME not set or dbstart missing)"
	exit 1
fi
#depending on parameter -- startup, shutdown, restart of the instance, the listener or show usage

case "$1" in
start)
	echo -n "Starting Oracle Databases: "
        echo "----------------------------------------------------" >> /var/log/oracle
        date +"! %T %a %D : Starting Oracle Databases as part of system up." >> /var/log/oracle
        echo "----------------------------------------------------" >> /var/log/oracle
        su - $ORA_OWNER -c  $ORACLE_HOME/bin/dbstart >> /var/log/oracle
        echo "Done."

The script is located in /etc/init.d and was created by root and was added to the necessary run-levels.

In the logging I notice the following error:
SQL> ERROR:
ORA-01031: insufficient privileges

When I run the script dbstart logged in as oracle-user I don't get this error-message.

Has anybody an idea what is causing this behaviour?

Any help would be appreciated.

Kind regards
secutus

---

