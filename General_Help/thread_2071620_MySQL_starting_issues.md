---
title: "MySQL starting issues"
date: 2012-10-15
forum: General Help
---

### Post by unknown user on 2012-10-15
I have been using MySQL on my windows drive via the MySQL 5.5 Command Line Client. I have got my head around this and seem to be making some good progress with it. It is set up to store locally and when I enter the password, away I go.

I tried to install it on to my Ubuntu system and I am having issues trying to run it. When I start it in Ubuntu, it is asking me for a database and a username/password. I do not know where this is or what it is. 

I was hoping to have the same line command setup as that in Windows. Can anyone help me with this as I would really like to use in Ubuntu. I would like to point my database storage area to a local drive, open it up and get going.

---

### Post by unknown user on 2012-10-16
Yesterday, I had a look into this a bit more and found that I was able to install MySQL server from the line command (sudo apt-get install mysql-server). This once installed asked me for a root password. I then was able to access MySQL from the terminal via the following line (mysql -u root -h localhost -p) then entering my password. Away I could go, that is just like the setup I have in windows, so now I am happy with this :)

However, I still have the issue when trying to access it from the gui, being asked for a database and password (which I know). Can anyone help?

---

