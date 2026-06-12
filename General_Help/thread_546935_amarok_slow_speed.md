---
title: "amarok slow speed"
date: 2007-09-09
forum: General Help
---

### Post by mpgarate on 2007-09-09
amarok runs really slow on my machine.. I have about 4000 songs to deal with, but rhythmbox and exaile handle it fine. Amarok is reeeaaallly slow for every little thing, like searching a playlist. I am wondering if that is because it is a kde app, and it is loading kde icons etc in addition to the application, where the gtk based apps load less, because I am using gnome. Is that correct? and suggestions to improve my speed?

amd64 x2
2gb ram
gutsy (same effects in feisty) i686

---

### Post by atlfalcons866 on 2007-09-09
is ubuntu taking advantage of your dual core processor?

---

### Post by FuturePilot on 2007-09-09
Are you using the default database? You might want to consider using MySQL instead of SQlite
It takes a little to set up but there's plenty of guides on how to do this.

---

### Post by mpgarate on 2007-09-09
okay ill try that... and im pretty sure im using both cores - in system monitor it shows 2 cpus

---

### Post by mpgarate on 2007-09-09
could you point me toward one of those how-to's?

---

### Post by bobbo85 on 2008-03-08
I think I have the solution for you:-)  It's using mysql instead of sqllite
I just got Amarok yesterday, and I'm a newbie to Linux too - hopefully these steps will be easy and correct... they worked for me!

My collection is a few thousand songs, and Amarok was slow to launch and often took several seconds to change songs.  After switching to mysql, things immediately sped up to normal.

So here is my newbie rundown...
First, install the mysql stuff you need.
Second, make a database for Amarok
Third, make a user like "amarok" for the program to use
Finally, tell Amarok to start using mysql


1)  Install mysql stuff.  I used synaptic to install "mysql-server" "mysql-client" and "mysql-common"
- you could also use the terminal to do this:
example:  
type this into the terminal, hit enter:  
```
sudo apt-get install mysql-server
```

I think it comes up with a window asking for a root password, just make one up.
Note:  If it doesn't ask you for a root password, type this command:
```
mysqladmin -u root password myPassword
```

2)  To make a user, you need to login to the mysql server we just made.  There is a program you can download to use a GUI called mysqladmin, but I didn't use it, I just ran these commands I got from another site.
Open up the terminal, we're going to login:
```
mysql -p -u root
```
Ok put in your password, now you're at a prompt for mysql.  Note that all commands here end in a semicolon.  Just know help; and quit; for now...  

3)  Now to setup the database and user:
```
CREATE DATABASE amarok;
USE amarok;
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
FLUSH PRIVILEGES;
```

Obviously you put in your own password there again - keep the quotes.

4)  Now I think you're pretty much done.  You might have to restart the mysql server, which I think I did by going to "System -> administration ->services" then unchecking and rechecking the sql stuff.  I'm sure there's some easy command for that too, but I don't know it yet.

Anyhow, open up Amarok, go to configure amarok, and under "collection" change the database to "mysql" - leave localhost, set the database to amarok, the username to amarok, and whatever your password was.

Enjoy much faster performance!  Hope this helped, it's my first attempt to answer a question on the forums.

By the way, I snagged some of those commands from this site:
[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by RichardNixon on 2008-04-13
> 4) Now I think you're pretty much done. You might have to restart the mysql server, which I think I did by going to "System -> administration ->services" then unchecking and rechecking the sql stuff. I'm sure there's some easy command for that too, but I don't know it yet.

The following does the trick from the command line:
```
sudo /etc/init.d/mysql restart
```

---

