---
title: "oracle 11 version...beginner question..."
date: 2007-09-18
forum: General Help
---

### Post by AlexenderReez on 2007-09-18
i just install oracle 11 version using [link]("https://help.ubuntu.com/community/HowToBuildToraWithOracle") .....
but i don't how to launch it....try to configure......but failed....any clue....i'm just beginner....

---

### Post by bettlebrox on 2007-09-19
It  might be a bit complicated! :)

First, is there a startup script for it in /etc/init.d/ ? If there is run it using sudo using the  argument startup.

If not, log in as the Oracle user (Did you create one?).  

Set the environmental variable ORACLE_SID to the name of the database you created during the installation process.

For example, if you create an database instance named mydb do the following:
[INDENT]export ORACLE_SID=mydb[/INDENT]

Start sqlplus and issue the following commands:
[INDENT]sqlplus /nolog
connect sys as sysdba
startup[/INDENT]

Then, if you want to connect to the database remotely (say from a application running on a webserver) you need to start the listener:
[INDENT]lsnrctl start[/INDENT]

This is all from memory, I'll check my notes when I get to work tomorrow and see if this is correct.

Luck!

---

### Post by AlexenderReez on 2007-09-19
> **bettlebrox said:**
> It  might be a bit complicated! :)

First, is there a startup script for it in /etc/init.d/ ? If there is run it using sudo using the  argument startup.

If not, log in as the Oracle user (Did you create one?).  

Set the environmental variable ORACLE_SID to the name of the database you created during the installation process.

For example, if you create an database instance named mydb do the following:
[INDENT]export ORACLE_SID=mydb[/INDENT]

Start sqlplus and issue the following commands:
[INDENT]sqlplus /nolog
connect sys as sysdba
startup[/INDENT]

Then, if you want to connect to the database remotely (say from a application running on a webserver) you need to start the listener:
[INDENT]lsnrctl start[/INDENT]

This is all from memory, I'll check my notes when I get to work tomorrow and see if this is correct.

Luck!

seriously...i don't really understand......but when i enter
[INDENT]sqlplus /nolog
connect sys as sysdba
startup[/INDENT]

it comes out....where it save this file when i choose save(remember i'm really absolute beginner in this....)


can you give me link to tutorial...reserved words and any key to save...to edit...or what ever...my  first and the only program right now is

> drop table DEPARTMENT cascade constraints;
drop table LECTURER cascade constraints;
drop table PROJECT cascade constraints;
drop table STUDENT cascade constraints;
drop table STUDENTPROJECT cascade constraints;

create table DEPARTMENT
(  DeptNo number(5),
   DeptName  varchar2(15),
   Location  varchar2(15),
  CONSTRAINTS dp_no_pk PRIMARY KEY (DeptNo) );

create table LECTURER
(  LectNo number(5),
   LectName varchar2(30),
   Research varchar2(30),
   DeptNo number(5),
  CONSTRAINTS le_no_pk PRIMARY KEY (LectNo),
  CONSTRAINTS dp_no_fk FOREIGN KEY (DeptNo) REFERENCES DEPARTMENT (DeptNo) );
 

create table PROJECT
(  ProjNo number(5),
   ProjTitle varchar2(30),
   StartDate date,
   EndDate date,
   Budget varchar2(8),
   LectNo  number(5),
  CONSTRAINTS pr_no_pk PRIMARY KEY (ProjNO),
  CONSTRAINTS lc_no_fk FOREIGN KEY (LectNo) REFERENCES LECTURER (LectNo) );

create table STUDENT
(  StudentID number(5),
   StName varchar2(30),
   StAge number(2),
   StDegree varchar2(15),
   DeptNo  number(5),
  CONSTRAINTS st_no_pk PRIMARY KEY (StudentID),
  CONSTRAINTS dp_no_fk1 FOREIGN KEY (DeptNo) REFERENCES DEPARTMENT (DeptNo) );

create table STUDENTPROJECT
(  ProjNo number(5),
   StudentID number(5),
  CONSTRAINTS stud_proj_pk PRIMARY KEY (StudentID,ProjNo),
  CONSTRAINTS stud_proj_fk1 FOREIGN KEY (ProjNo) REFERENCES PROJECT (ProjNo),
  CONSTRAINTS stud_proj_fk2 FOREIGN KEY (StudentID) REFERENCES STUDENT (StudentID) );

alter table project
add ( Sponsor varchar2(30) );

alter table student
modify ( StAge number(5) );

alter table department
add ( Lect_No number(5) );

alter table department
add (constraints lec_no_fk FOREIGN KEY (Lect_No) REFERENCES LECTURER (LectNo) );

describe department

describe lecturer

describe project

describe student

describe studentproject 

EDIT = there is no startup script for oracle in my /etc/init.d/  ...is that mean it installed in other place?

---

### Post by thatswhatshesaid on 2007-09-19
Any particular reason that you need the full 11g (vs Oracle XE)?

I have to work with oracle a lot at work and, although i haven't read about 11g yet (got my copy of Oracle mag though), there normally a lot of hoops to jump through to get 10g installed on even *certified* linux platforms (SLES, RHEL, Asianux, and Oracle Linux).

I'm not saying it can't be done (I've heard about 10g Enterprise running on Ubuntu) but it might not be worth it.  When you say "beginner question" are you referring to ubuntu, linux, or oracle (just curious)?

---

### Post by AlexenderReez on 2007-09-19
hm...i i'm average linux user...but really new to oracle.....hm....actually i just realized that howto(first link) ....i know there is a guide over there to add repo and configure it....but when i see i need to download about 255mb ++ for oracle 10 g(even in deb package),it quite dispointed .....but if i refer ot that first link...it guide me to download only about 50 mb(for all files)...

[COLOR="SeaGreen"]but[/COLOR] i did try to install oracle 10g and it failed to installed without giving any error ...whether dependency or anything else....even i did tried few times...

but install 11 version is really easy...got no problem....and i manage to run with help from [COLOR="Blue"]**bettlebrox**[/COLOR] ....

[PHP]reez@aLexEnDeRReEz:~$ sqlplus /nolog && connect sys as sysdba && startup

SQL*Plus: Release 11.1.0.6.0 - Production on Wed Sep 19 16:11:53 2007

Copyright (c) 1982, 2007, Oracle.  All rights reserved.

SQL> 


[/PHP]


so any help would be appreciate.....

---

### Post by bettlebrox on 2007-09-19
I agree with thatswhatshesaid that Oracle XE is probably going to be easier to for someone new to Oracle to use.

---

### Post by bettlebrox on 2007-09-19
Look here for documentation:
[http://www.oracle.com/pls/db111/homepage](http://www.oracle.com/pls/db111/homepage)
[http://searchoracle.techtarget.com/originalContent/0,289142,sid41_gci950947,00.html](http://searchoracle.techtarget.com/originalContent/0,289142,sid41_gci950947,00.html)
[http://www.smart-soft.co.uk/tutorial.htm](http://www.smart-soft.co.uk/tutorial.htm)

---

### Post by AlexenderReez on 2007-09-20
i got error...please help...after reboot...i can't open it anymore....

> reez@aLexEnDeRReEz:~$ sqlplus /nolog && connect sys as sysdba && startup
sqlplus: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory

---

### Post by AlexenderReez on 2007-09-20
solved that problem....but....


why i got this error while to open sql file in my home folder...??

> reez@aLexEnDeRReEz:~$ sqlplus /nolog

SQL*Plus: Release 11.1.0.6.0 - Production on Thu Sep 20 15:42:48 2007

Copyright (c) 1982, 2007, Oracle.  All rights reserved.

SQL> describe /home/reez/testoracle.sql
SP2-0640: Not connected
SP2-0641: "DESCRIBE" requires connection to server
SQL> 


i just want to connect to my home folder....what is server that i need?:mad:


based on [https://help.ubuntu.com/community/HowToBuildToraWithOracle](https://help.ubuntu.com/community/HowToBuildToraWithOracle)

it state to use

> sqlplus  username/password@//dbhost:1521/SID

 NOTE "In the connect box make sure the connection provide says "Oracle. Then enter an Instantclient connect string in the boxes. Put "username" and "password" in the appropriate places. Then put the string //dbhost:<portno>/SID in the "Database" box."



1.is it username and password is my realy system user name?or new one?

2.portno...?i just want to connect to my home folder and do basic oracle...what kind of port is it?

---

