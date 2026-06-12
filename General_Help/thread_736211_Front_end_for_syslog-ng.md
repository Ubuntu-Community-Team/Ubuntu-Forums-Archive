---
title: "Front end for syslog-ng"
date: 2008-03-26
forum: General Help
---

### Post by seeker1458 on 2008-03-26
posted this in desktop group, but on second thought I figured I would get a quicker response here.

Hey guys, looking for a good syslog-ng front end. I've got my logs seperated out by $HOST, but it would be nice to have a gui for making charts and the like. Please report on your experience with the different front ends you have used. Also, is mysql installed via the:

```
apt-get install build-essential
```? 
If you could please let me know of any dependencies.

---

### Post by kellemes on 2008-03-26
Don't know about a frontend for syslog-ng.

buils-essentials includes tools for building packages.. see here...
[http://packages.ubuntu.com/gutsy/build-essential]("http://packages.ubuntu.com/gutsy/build-essential")

Mysql is installed like so..
```
sudo apt-get install mysql-server
```
mysql-server is an empty package pointing to the last mysql version in the repository, that's mysql-server-5.0
So you can just as well..
```
sudo apt-get install mysql-server-5.0
```

---

