---
title: "how to do some experiment with mysql server 5.6 on ubuntu 14.04&#65311;"
date: 2015-07-22
forum: General Help
---

### Post by andy140 on 2015-07-22
Hi,I am a newcomer to mysql although I have learned it in school.
I want to use mysql to do some experiment about Netflix Prize in 2006&#65292;
So I have many data to deal with(about 100 million rating).On my ubuntu
Server,I have installed Mysql server 5.6 with the command:
```
sudo apt-get install mysql-server-5.6
```
Do I need to install a client on my Mac? and I want to know how to input my
data(about 2G) into database?And is there some useful tutorial could help me?
Thank you  in advance.

---

### Post by Lars Noodén on 2015-07-23
You will need a client on whichever machine you connect from.  

About loading the data in bulk, one way to do that is to use [load data infile](http://dev.mysql.com/doc/refman/5.6/en/load-data.html) to read from a file.  But the file will have to be structured correctly.  If you do it that way, it will probably be faster to upload to the Ubuntu machine then use the client there to do the import so that you don't have to wait for 2+ GB to flow across the network.

---

### Post by andy140 on 2015-07-23
> **Lars Noodén said:**
> You will need a client on whichever machine you connect from.  

About loading the data in bulk, one way to do that is to use [load data infile]("http://dev.mysql.com/doc/refman/5.6/en/load-data.html") to read from a file.  But the file will have to be structured correctly.  If you do it that way, it will probably be faster to upload to the Ubuntu machine then use the client there to do the import so that you don't have to wait for 2+ GB to flow across the network.
OK,Thank you friend.

---

