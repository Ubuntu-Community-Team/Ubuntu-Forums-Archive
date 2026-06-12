---
title: "Connect to a MS SQL database"
date: 2013-08-02
forum: General Help
---

### Post by Remilegentil on 2013-08-02
Hi everybody,

First, I'm not sure where to post this. I didn't see any "database" section. Feel free to move this thread to the correct place.  

I need to administer a MS SQL server, and I was wondering what SQL clients are available. I'm not new with databases, but it is the first time I attempt to work with MS SQL server. I need a graphical interface to send my SQL requests, view the database, just like phpMyAdmin would do. 

There must be something I didn't understand, because I can't get anything to work. Should I install a driver ? (I saw there was an ODBC driver for RedHat that won't work on my LinuxMint). What about JDBC -is this necessary ? Why does the client "Squirrel" (a client that should be exactly what I need) always tell me that I lack some libs ? 

Any hint would be nice.

---

### Post by Remilegentil on 2013-08-02
I'm slowly making progress here. I finally made my connection work by using squirrel and JDBC or JDTS. But with both, I get errors when I attempt to make SELECTs. Since I lost a lot of time, I'll post an explanation when everything is clearer.

---

### Post by oldfred on 2013-08-02
There is ODBC drivers, but with Linux they are not particularly easy to configure. But as I remember with Windows (years ago) it was not all that easy to configure in Windows.

I have this in my notes:
Dabo is designed to create database-centric apps
[http://dabodev.com/](http://dabodev.com/)

---

