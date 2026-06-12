---
title: "[SOLVED] dependency issues"
date: 2008-03-16
forum: General Help
---

### Post by jessika-kaos on 2008-03-16
I am trying to install anki (a spaced repetition program like mnemosyne) and I get:

```
Unpacking anki (from anki_0.9.5.4-1_all.deb) ...
dpkg: dependency problems prevent configuration of anki:
 anki depends on python-sqlalchemy (>= 0.4.1); however:
  Version of python-sqlalchemy on system is 0.3.10-1.
 anki depends on python-simplejson (>= 1.7.3); however:
  Version of python-simplejson on system is 1.7.1-2.
dpkg: error processing anki (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

I installed SQLAlchemy 0.4.1 from [here]("https://launchpad.net/ubuntu/+source/sqlalchemy/0.4.1-1"), but I think it put it in somewhere very different then the old version and thus it is not acknowledged as installed. 
Is there an easy way to reconcile these two dependencies?

---

### Post by steveneddy on 2008-03-16
You need to install

**python-sqlalchemy (>= 0.4.1)**

and

**python-simplejson (>= 1.7.3)**

the symbols [COLOR="Blue"]**>=**[/COLOR] mean "greater than or equal to".

So you need a coupla libs to get this software to install properly.

If they aren't in the repos, then search with Google and go get them.

:D

---

### Post by Antarctica on 2008-03-16
Hey, I performed a search and python-sqlalchemy is in the repos.
```
sudo aptitude show python-sqlalchemy
```Your best bet is to upgrade and install programs via the repos and programs such as apt-get, aptitude, or Synaptic Package Manager.  Try upgrading all your programs.
```
sudo aptitude full-upgrade
```If that fails, then try...
```
sudo aptitude install python-sqlalchemy
```I hope this helps.  Let me know what the results are.

---

### Post by jessika-kaos on 2008-03-16
right, i found Python-SQLAlchemy 0.4.1 and installed it, but it doesn't show up as being installed. Python setup tools creates an .egg file that is put (it looks like) in /usr/lib/python2.5, but SQLAlchemy 0.3.10is elsewhere. 

```
creating /usr/lib/python2.5/site-packages/SQLAlchemy-0.4.1-py2.5.egg
Extracting SQLAlchemy-0.4.1-py2.5.egg to /usr/lib/python2.5/site-packages
SQLAlchemy 0.4.1 is already the active version in easy-install.pth

Installed /usr/lib/python2.5/site-packages/SQLAlchemy-0.4.1-py2.5.egg
Processing dependencies for SQLAlchemy==0.4.1

```

---

### Post by Antarctica on 2008-03-16
Try...
```
sudo aptitude autoclean
sudo aptitude reinstall python-sqlalchemy
```
That might help some.  I don't know much about python or SQLAlchemy.  If it helps, here's the output of sudo aptitude show python-sqlalchemy...
```
$sudo aptitude show python-sqlalchemy
Package: python-sqlalchemy
State: not installed
Version: 0.3.10-1
Priority: optional
Section: universe/python
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 1294k
Depends: python-central (>= 0.5.8), python (>= 2.3)
Suggests: python-psycopg2, python-mysqldb (>= 1.2.1-p2-2), python-pysqlite2 (>=
          2.3.0-1) | python-pysqlite1.1 (>= 1.1.7-2) | python-sqlite (>=
          1.0.1-5), python-kinterbasdb (>= 3.1.2-0.3), python-sqlalchemy-doc,
          python-setuptools (>= 0.6b3-1)
Conflicts: python-psycopg, python2.4-sqlalchemy (< 0.2.3-0.1)
Replaces: python2.4-sqlalchemy (< 0.2.3-0.1)
Provides: python2.4-sqlalchemy, python2.5-sqlalchemy
Description: SQL toolkit and Object Relational Mapper for Python
 SQLAlchemy is an SQL database abstraction library for Python. Its strengths
 are: 
 * full power and flexibility of SQL. SQLAlchemy provides a full suite of well
   known enterprise-level persistence patterns, designed for efficient and
   high-performing database access, adapted into a simple and Pythonic domain
   language. 
 * extremely easy to use for all the basic tasks, such as: accessing pooled
   connections, constructing SQL from Python expressions, finding object
   instances, and commiting object modifications back to the database. 
 * powerful enough for complicated tasks, such as: eager load a graph of objects
   and their dependencies via joins; map recursive adjacency structures
   automatically; map objects to not just tables but to any arbitrary join or
   select statement; combine multiple tables together to load whole sets of
   otherwise unrelated objects from a single result set; commit entire graphs of
   object changes in one step. 
 * built to conform to what DBAs demand, including the ability to swap out
   generated SQL with hand-optimized statements, full usage of bind parameters
   for all literal values, fully transactionalized and consistent updates using
   Unit of Work. 
 * modular. Different parts of SQLAlchemy can be used independently of the rest,
   including the connection pool, SQL construction, and ORM. SQLAlchemy is
   constructed in an open style that allows plenty of customization, with an
   architecture that supports custom datatypes, custom SQL extensions, and ORM
   plugins which can augment or extend mapping functionality. 
   
 Homepage: http://www.sqlalchemy.org/

```

---

### Post by jessika-kaos on 2008-03-16
Yep I just want to upgrade that one package. I tried installing the new version (not in the repos) with python setuptools as explained [here]("http://peak.telecommunity.com/DevCenter/EasyInstall#installing-easy-install"). it looks like ends with "processing dependencies" without installing?

---

### Post by Antarctica on 2008-03-16
It could be a broken package or maybe you need to setup a symbolic link somewhere?

---

### Post by jessika-kaos on 2008-03-16
got it. had to download debs from[ here]("http://packages.ubuntu.com/hardy/all/"). The packages I wanted were in the hardy repos but not gutsy's, though i did have to did for a few dependencies.

---

### Post by Antarctica on 2008-03-16
Yay!  I'm glad you solved it!

---

