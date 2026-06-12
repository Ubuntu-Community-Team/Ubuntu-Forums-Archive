---
title: "Lamp-server will not install"
date: 2013-08-14
forum: General Help
---

### Post by adrian89 on 2013-08-14
I am trying to install lamp-server on a ubuntu 13.04 machine but when it should start installing it stops with error:aptitude failed(100).
I've searched on the internet and there were several fixes but none worked.
Tried:
-reinstalling aptitude
-sudo apt-get update and then try to install lamp
-using sudo tasksel and then manually select lamp-server from the list
-```
[COLOR=#000000][FONT=Consolas]sudo apt-get update --fix-missing and then reinstalling[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]
-[/FONT][/COLOR]```
debconf-apt-progress -- apt-get -q -y install lamp-server
```

I already have lamp-server installed for a while now on another machine(laptop),but the cooler's ventilator died and until I fix it I need to use lamp on another machine but cannot figure a solution for this.

---

### Post by Lars Noodén on 2013-08-14
You can install it with apt-get instead.

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Mind the caret (^)

If you have no reason to use the database, you can just install Apache2 by itself.  Perl is built into Ubuntu and all other Linux or BSD distros, so it is possible to get started without adding much.

---

### Post by adrian89 on 2013-08-14
I receive the following issue which apt-get -f install cannot resolve.

Unfortunately I need Apache2-PHP-MySql.
Some packages cannot be installed.This means you have an imposible request or you are using and instable distribution in which some packages were not created yet or moved from Incoming.


The following packages have unresolved dependencies:
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.32-0ubuntu0.13.04.1) but 5.5.32-0ubuntu0.13.04.2 it is about to be installed.
E: Could not correct the issue, you held broken packages.


Update:Solved the issue after removing mysql-server-core-5.5(sudo tasksel instal lamp-server started installing)

---

