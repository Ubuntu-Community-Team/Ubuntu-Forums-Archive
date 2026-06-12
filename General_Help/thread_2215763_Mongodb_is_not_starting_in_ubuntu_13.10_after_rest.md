---
title: "Mongodb is not starting in ubuntu 13.10 after restart"
date: 2014-04-08
forum: General Help
---

### Post by maciej-bak-85 on 2014-04-08
[COLOR=#000000][FONT=Arial]I've installed on ubuntu 13.10 mongodb in standard way[/FONT][/COLOR]
> sudo apt-get install mongodb-10gen
[COLOR=#000000][FONT=Arial]but after system restart I have:[/FONT][/COLOR]
> mongo
MongoDB shell version: 2.4.10
connecting to: test
Tue Apr  8 13:27:01.049 Error: couldn't connect to server 127.0.0.1:27017 at src/mongo/shell/mongo.js:145
exception: connect failed
[COLOR=#000000][FONT=Arial]even after:[/FONT][/COLOR]
> sudo service mongodb start
[sudo] password for baku: 
mongodb start/running, process 2589
[COLOR=#000000][FONT=Arial]To run mongo I have to do:[/FONT][/COLOR]
 > sudo mongod -f /etc/mongodb.conf &
[COLOR=#000000][FONT=Arial]How to make this working on system start ? Thanks![/FONT][/COLOR]

---

