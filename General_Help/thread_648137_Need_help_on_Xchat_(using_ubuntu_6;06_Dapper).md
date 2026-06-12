---
title: "Need help on Xchat (using ubuntu 6;06 Dapper)"
date: 2007-12-23
forum: General Help
---

### Post by deadpunk on 2007-12-23
First of all! i have downloaded xchat 2.6.6 using synaptic! i would like to get the last version.i have download it and i got xchat 2.8.4.tar.bz2 and i would like to install it.i try using terminal but i got some errors which tell me that i need a compiler(gtk...something like this).Can any one help me!

Before i was using Xp and i was moderating a chan using mIRC and i got scripts to do somme stuff.eg: using kick with a reason behind telling why i kick him or ban him.All the coding was in a text.ini and i was doing some modification on it so that to suit my operation  as a moderator!

But now am on ubuntu 6.06 dapper and i want to insert these option in popup of my xchat!

Thanx


ps: i got ubuntu via friend and  i love it!!!! i ll stuck to it and try to master it and with the help of th forum!

---

### Post by seshomaru samma on 2007-12-23
I think you need a pcakage called build essential to install that.
run this command:
```
sudo aptitude install build-essential
```
also read[ this ]("http://monkeyblog.org/ubuntu/installing/")

EDIT - it is possible that the latest Xchat will not run on Ubuntu 6.06.  Perhaps what it asked you for was not a compiler but some dependencies. It is possible that you will need to update other componants to make the latest version run on Dapper.
 If you get the latest version of Ubuntu (7.10 Gutsy) it will naturally run the latest software , but it also more likely to be buggy...

---

