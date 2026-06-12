---
title: "How to grep and only show exact match?"
date: 2019-10-10
forum: General Help
---

### Post by suaro on 2019-10-10
Hi Everyone,

This is killing me and I'm sure there's a super easy answer.  
I'm running the following command and grepping the output with 'com.microsoft.sqlserver.jdbc.SQLServerConnection':

Example:

jcmd `cat /var/run/hive/hive.pid` GC.class_histogram | grep 'com.microsoft.sqlserver.jdbc.SQLServerConnection'
 211:            21           3528  com.microsoft.sqlserver.jdbc.SQLServerConnection
 406:            18           1008  com.microsoft.sqlserver.jdbc.SQLServerConnection$LogonCommand
 570:            21            504  com.microsoft.sqlserver.jdbc.SQLServerConnectionSecurityManager
 867:             3            168  com.microsoft.sqlserver.jdbc.SQLServerConnection$1ConnectionCommand
1040:             4             96  com.microsoft.sqlserver.jdbc.SQLServerConnection$State
1629:             1             32  [Lcom.microsoft.sqlserver.jdbc.SQLServerConnection$State;

The first line is what I'm looking for, but I don't want the others (i.e. com.microsoft.sqlserver.jdbc.SQLServerConnection$LogonCommand   and com.microsoft.sqlserver.jdbc.SQLServerConnectionSecurityManager, etc...)
I understand grep is returning what I'm asking but how can I grep for just 'com.microsoft.sqlserver.jdbc.SQLServerConnection'  with nothing else added to the end?

Thanks so much for any input

---

### Post by Holger_Gehrke on 2019-10-10
How about putting a "$" - which signifies the end of a line in Regular expressions -  at the end of your search term ?

Holger

---

### Post by suaro on 2019-10-10
ahhh....yes.   That did it.  Thank you so much.  This has been driving me nuts!

---

