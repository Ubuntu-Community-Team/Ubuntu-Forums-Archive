---
title: "Help installing ivtv for hauppauge pvr 150"
date: 2007-01-09
forum: General Help
---

### Post by Atrio05 on 2007-01-09
well i have been trying to install ivtv for Edgy 6.10 but i keep getting an error.
i've been following the tutorial at this site [site]("https://help.ubuntu.com/community/Install_IVTV_Edgy#head-4dab30da47e2645aa5f1c6d6956f6e1e41b816bd") but i get to this command *sudo apt-get install ivtv-source devscripts ivtv-utils module-assistant* and i get this error *E: Couldn't find package ivtv-source*. could anyone help me with getting ivtv to work or my hauppauge card?

---

### Post by Atrio05 on 2007-01-09
i'm trying to get myth tv installed by some directions found on some wiki(i will post the site when i find it again, i'm on a different comp. now) and i am stuck at this point until i get ivtv installed. so any info on this problem would be great because as of now i'm at a stand still. 

 thanks for your time!

---

### Post by superm1 on 2007-01-09
> **Atrio05 said:**
> well i have been trying to install ivtv for Edgy 6.10 but i keep getting an error.
i've been following the tutorial at this site [site]("https://help.ubuntu.com/community/Install_IVTV_Edgy#head-4dab30da47e2645aa5f1c6d6956f6e1e41b816bd") but i get to this command *sudo apt-get install ivtv-source devscripts ivtv-utils module-assistant* and i get this error *E: Couldn't find package ivtv-source*. could anyone help me with getting ivtv to work or my hauppauge card?
This most likely means that you don't have universe or multiverse enabled.

If this is a desktop machine, click your System Menu, Choose Administration.  Choose Software Sources.  Place check marks in the two boxes for universe and multiverse.  It will ask you to update your software lists.  Go ahead.  Try again after this.

If this is a command line system, you will have to do this by editing your /etc/apt/sources.list.  This is described among dozens of other posts.  This will describe how to do it:
[https://help.ubuntu.com/community/MythTV/Install/Server/Edgy/Repositories](https://help.ubuntu.com/community/MythTV/Install/Server/Edgy/Repositories)

---

### Post by Atrio05 on 2007-01-09
yes i'm doing this on a command line system and i'm pretty sure that i have all the sources uncommented that need to be, and i did sudo apt-get update and upgrade but i still get this error. i will check later to find my sources list and post it here to be sure it is correct.

thanx!

---

### Post by Atrio05 on 2007-01-10
heres my sources.list "
[I]I have 

Edgy main restricted
edgy main restricted
edgy-updates main restricted
edgy-updates main restricted
edgy-backports main restricted universe multiverse
edgy-backports main restricted universe multiverse
security main restricted 
security universe
security universe [/I]
i basicly have every thing uncommented that can be. any help?

---

### Post by nikhilk on 2007-01-10
I actually checked the multiverse repository and found a couple of ivtv-source packages there! So the error you are getting is a bit puzzling. You can try searching for it through Synaptic.

---

### Post by Atrio05 on 2007-01-10
i cant get to synaptic i only have a command line system

---

### Post by Atrio05 on 2007-01-10
is there any other way to download and install ivtv through a command line than the way i've been trying?

---

### Post by nikhilk on 2007-01-10
You can try downloading the package directly from the ubuntu archive (using wget or through ftp) and then install it using  dpkg.

---

### Post by Atrio05 on 2007-01-10
how do i go about doing that?

---

### Post by nikhilk on 2007-01-10
Try the following
```
wget archive.ubuntu.com/ubuntu/pool/multiverse/i/ivtv/ivtv-source_0.8.1-2_all.deb
```

There is another version ivtv-source_0.7.0-2_all.deb. I dont know which one you are looking for.

---

### Post by superm1 on 2007-01-10
> **Atrio05 said:**
> heres my sources.list "
[I]I have 

Edgy main restricted
edgy main restricted
edgy-updates main restricted
edgy-updates main restricted
edgy-backports main restricted universe multiverse
edgy-backports main restricted universe multiverse
security main restricted 
security universe
security universe [/I]
i basicly have every thing uncommented that can be. any help?
Exactly the issue here.
You don't have universe/multiverse on the ordinary edgy repository.  You only have it on edgy-backports and (universe) on security.

---

### Post by Atrio05 on 2007-01-10
so how do i get the universe/multiverse working?

---

### Post by superm1 on 2007-01-10
> **Atrio05 said:**
> so how do i get the universe/multiverse working?
The link i gave you earlier, just have your /etc/apt/sources.list match up with that.

---

### Post by Atrio05 on 2007-01-10
ok i got that all figured out and i'm now to this step and do not know how to do these things any pointers?

[I]#

Now, we will create a session for the automatic mythtv login. Create the file /usr/share/xsessions/mythtv.desktop. Place these contents into that file:

    *

      [Desktop Entry]
      Encoding=UTF-8
      Name=MythTV
      Comment=Use this session to run MythTV
      Exec=/usr/local/bin/mythtv.sh
      Icon=
      Type=Application

#

Create a script, /usr/local/bin/mythtv.sh that will be spawned when you login to your MythTV session. Place these contents into that file:

    *

      gnome-screensaver
      mythfrontend&
      exec openbox
[/I]

---

### Post by superm1 on 2007-01-10
> **Atrio05 said:**
> ok i got that all figured out and i'm now to this step and do not know how to do these things any pointers?

[I]#

Now, we will create a session for the automatic mythtv login. Create the file /usr/share/xsessions/mythtv.desktop. Place these contents into that file:

    *

      [Desktop Entry]
      Encoding=UTF-8
      Name=MythTV
      Comment=Use this session to run MythTV
      Exec=/usr/local/bin/mythtv.sh
      Icon=
      Type=Application

#

Create a script, /usr/local/bin/mythtv.sh that will be spawned when you login to your MythTV session. Place these contents into that file:

    *

      gnome-screensaver
      mythfrontend&
      exec openbox
[/I]
Sure:

```
sudo nano /usr/share/xsessions/mythtv.desktop
```If you are working over ssh, you can just paste that other section in.  Press ctrl-x to exit nano and save.  If your not working over ssh, then you will have to type it out.

same thing for the other file.

---

### Post by Atrio05 on 2007-01-10
ok one new and last problem i am trying to do this to fix a problem [I]Access denied for user: 'mythtv@localhost'

see instructions below with the small change of the instructon. Instead of

UPDATE user SET Password=PASSWORD('<password>') WHERE user='root';
FLUSH PRIVILEGES;

instead you can set mythtv password to the default (mythtv):

UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
FLUSH PRIVILEGES;
[/I]
 but when i type in the second one into the terminal i get this error *bash: syntax error near unexpected token `('*

can someone shed some light on this subject?

---

### Post by Atrio05 on 2007-01-10
come on this is all i need to get this to work someone please help!!!!

---

### Post by Atrio05 on 2007-01-10
does no one have any good advice as to what i do now?

---

### Post by Atrio05 on 2007-01-10
should i just not use this [tutorial]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend") and just install the edgy base system like normal and install mythtv after i have everything the way i want it? is it easier to install MythTV that way? because it seems this way all this system will be able to do is run mythtv. i kinda just wanted a way to schedule a few recordings from time to time not make a tivo. what should i do please advise me! :)

---

### Post by rattking on 2007-01-10
Hi 
UPDATE user SET Password=PASSWORD('<password>') WHERE user='root';
 FLUSH PRIVILEGES;
is a mysql command

mysql -u root mysql
to start mysql
then use that command
more  info here [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)
under Trouble Shooting
hope that helps

---

### Post by Atrio05 on 2007-01-10
well thanx for the help but i'm gonna try the other tutorial that you showed me because the other way just was not my cup of tea. i would like to be able to use it as a desktop as it's in my room. so i may be back to ask for more help with the other tut. i'm not a total n00b i just need help with some of the bash stuff!

---

### Post by edward4130 on 2007-01-12
I am in the same trouble, using a pvr-500 (same as two 150's) and They are not seen when the feed is clearly working.  I will have a chance to work on this some tomorrow, and hope that what you have posted here will help.  

My goal with using ubuntu and mythtv is to have a all-in-one, I wanted games full featured internet, as well as the PVR capabilities.  If i can't get this going I will have to go with Knoppmyth, and it is saddly lacking in other cool functions that I wanted in my Media Center.

-Edward

---

### Post by Atrio05 on 2007-01-12
yea i've had problems with knnopmyth not installing properly. it installs but it won't start up right. i donno i really want MythTV to work but i am now stuck with problems with the mysql server stuff, in the error log it keeps saying *Access denied for user: 'mythtv@localhost'* and i keep trying to do what it says in the troubleshooting section but it still won't let me start the mythfrontend. can someone help me out with this problem?

---

### Post by Atrio05 on 2007-01-13
how do i get the mythfrontend to load properly?

---

### Post by Atrio05 on 2007-01-14
can someone please help me out i really want to get myth tv running!

---

### Post by superm1 on 2007-01-14
> **Atrio05 said:**
> yea i've had problems with knnopmyth not installing properly. it installs but it won't start up right. i donno i really want MythTV to work but i am now stuck with problems with the mysql server stuff, in the error log it keeps saying *Access denied for user: 'mythtv@localhost'* and i keep trying to do what it says in the troubleshooting section but it still won't let me start the mythfrontend. can someone help me out with this problem?
Okay, so if you follow what it is asking you to do in the troubleshooting section, you are updating your password for the 'mythtv' user.  This means that whatever password you set it to, this password needs to be updated in BOTH /etc/mythtv/mysql.txt and ~/.mythtv/mysql.txt where ~ is '/home/USERNAME' and USERNAME is the username you are attempting to start mythfrontend with.  Are you updating both of these files?

---

### Post by Atrio05 on 2007-01-14
well i can't even edit the second txt because it does not exist and when ever i try to start the front end it still fails and when i run this command *more /var/log/mythtv/mythbackend.log* I get This back [I]josh@josh-ubuntu:~$ more /var/log/mythtv/mythbackend.log
2007-01-11 15:47:09.411 Using runtime prefix = /usr
2007-01-11 15:47:09.830 New DB connection, total: 1
2007-01-11 15:47:10.055 Unable to connect to database!
2007-01-11 15:47:10.057 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-01-11 15:47:10.152 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-01-11 15:47:10.209 Failed to init MythContext, exiting.
2007-01-11 16:00:57.215 Using runtime prefix = /usr
2007-01-11 16:00:57.397 New DB connection, total: 1
2007-01-11 16:00:57.409 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.439 Current Schema Version: 1160
Starting up as the master server.
2007-01-11 16:00:57.507 New DB connection, total: 2
2007-01-11 16:00:57.517 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.574 EITHelper: localtime offset -5:00:00 
2007-01-11 16:00:57.587 New DB connection, total: 3
2007-01-11 16:00:57.589 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.752 New DB scheduler connection
2007-01-11 16:00:57.754 Connected to database 'mythconverg' at host: localhost
Channel 4 is defined, but isn't attached to a cardinput.
2007-01-11 16:00:57.846 Main::Starting HttpServer
2007-01-11 16:00:57.997 Main::Registering HttpStatus Extension
2007-01-11 16:00:58.102 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-01-11 16:00:58.102 Enabled verbose msgs:  important general
2007-01-11 16:00:58.112 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-01-11 16:00:58.116 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2007-01-11 16:00:59.848 Reschedule requested for id -1.
2007-01-11 16:01:00.294 Scheduled 0 items in 0.4 = 0.31 match + 0.14 place
2007-01-11 16:01:00.407 Seem to be woken up by USER
2007-01-11 16:06:24.480 MainServer::HandleAnnounce Monitor
2007-01-11 16:06:24.496 adding: josh-ubuntu as a client (events: 0)
2007-01-11 16:06:24.498 MainServer::HandleAnnounce Monitor
2007-01-11 16:06:24.499 adding: josh-ubuntu as a client (events: 1)
2007-01-14 15:39:37.372 Using runtime prefix = /usr
2007-01-14 15:39:37.704 New DB connection, total: 1
2007-01-14 15:39:37.767 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:37.779 Current Schema Version: 1160
Starting up as the master server.
2007-01-14 15:39:37.803 New DB connection, total: 2
2007-01-14 15:39:37.805 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:37.845 EITHelper: localtime offset -5:00:00 
2007-01-14 15:39:38.071 New DB connection, total: 3
2007-01-14 15:39:38.111 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:38.242 New DB scheduler connection
2007-01-14 15:39:38.259 Connected to database 'mythconverg' at host: localhost
Channel 4 is defined, but isn't attached to a cardinput.
2007-01-14 15:39:38.270 Main::Starting HttpServer
2007-01-14 15:39:38.316 Main::Registering HttpStatus Extension
2007-01-14 15:39:38.374 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-01-14 15:39:38.471 Enabled verbose msgs:  important general
2007-01-14 15:39:38.524 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-01-14 15:39:38.541 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2007-01-14 15:39:40.365 Reschedule requested for id -1.
2007-01-14 15:39:40.413 Scheduled 0 items in 0.0 = 0.02 match + 0.03 place
2007-01-14 15:39:40.421 Seem to be woken up by USER[/I]
so can you tell what i'm doing wrong here?

---

### Post by superm1 on 2007-01-14
> **Atrio05 said:**
> well i can't even edit the second txt because it does not exist and when ever i try to start the front end it still fails and when i run this command *more /var/log/mythtv/mythbackend.log* I get This back [I]josh@josh-ubuntu:~$ more /var/log/mythtv/mythbackend.log
2007-01-11 15:47:09.411 Using runtime prefix = /usr
2007-01-11 15:47:09.830 New DB connection, total: 1
2007-01-11 15:47:10.055 Unable to connect to database!
2007-01-11 15:47:10.057 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-01-11 15:47:10.152 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-01-11 15:47:10.209 Failed to init MythContext, exiting.
2007-01-11 16:00:57.215 Using runtime prefix = /usr
2007-01-11 16:00:57.397 New DB connection, total: 1
2007-01-11 16:00:57.409 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.439 Current Schema Version: 1160
Starting up as the master server.
2007-01-11 16:00:57.507 New DB connection, total: 2
2007-01-11 16:00:57.517 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.574 EITHelper: localtime offset -5:00:00 
2007-01-11 16:00:57.587 New DB connection, total: 3
2007-01-11 16:00:57.589 Connected to database 'mythconverg' at host: localhost
2007-01-11 16:00:57.752 New DB scheduler connection
2007-01-11 16:00:57.754 Connected to database 'mythconverg' at host: localhost
Channel 4 is defined, but isn't attached to a cardinput.
2007-01-11 16:00:57.846 Main::Starting HttpServer
2007-01-11 16:00:57.997 Main::Registering HttpStatus Extension
2007-01-11 16:00:58.102 mythbackend version: 0.20.20060828-3 [www.mythtv.org]("http://www.mythtv.org")
2007-01-11 16:00:58.102 Enabled verbose msgs:  important general
2007-01-11 16:00:58.112 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-01-11 16:00:58.116 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2007-01-11 16:00:59.848 Reschedule requested for id -1.
2007-01-11 16:01:00.294 Scheduled 0 items in 0.4 = 0.31 match + 0.14 place
2007-01-11 16:01:00.407 Seem to be woken up by USER
2007-01-11 16:06:24.480 MainServer::HandleAnnounce Monitor
2007-01-11 16:06:24.496 adding: josh-ubuntu as a client (events: 0)
2007-01-11 16:06:24.498 MainServer::HandleAnnounce Monitor
2007-01-11 16:06:24.499 adding: josh-ubuntu as a client (events: 1)
2007-01-14 15:39:37.372 Using runtime prefix = /usr
2007-01-14 15:39:37.704 New DB connection, total: 1
2007-01-14 15:39:37.767 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:37.779 Current Schema Version: 1160
Starting up as the master server.
2007-01-14 15:39:37.803 New DB connection, total: 2
2007-01-14 15:39:37.805 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:37.845 EITHelper: localtime offset -5:00:00 
2007-01-14 15:39:38.071 New DB connection, total: 3
2007-01-14 15:39:38.111 Connected to database 'mythconverg' at host: localhost
2007-01-14 15:39:38.242 New DB scheduler connection
2007-01-14 15:39:38.259 Connected to database 'mythconverg' at host: localhost
Channel 4 is defined, but isn't attached to a cardinput.
2007-01-14 15:39:38.270 Main::Starting HttpServer
2007-01-14 15:39:38.316 Main::Registering HttpStatus Extension
2007-01-14 15:39:38.374 mythbackend version: 0.20.20060828-3 [www.mythtv.org]("http://www.mythtv.org")
2007-01-14 15:39:38.471 Enabled verbose msgs:  important general
2007-01-14 15:39:38.524 AutoExpire: Found 1 recorders w/max rate of 72 MiB/min
2007-01-14 15:39:38.541 AutoExpire: Required Free Space: 1.1 GB w/freq: 10 min
2007-01-14 15:39:40.365 Reschedule requested for id -1.
2007-01-14 15:39:40.413 Scheduled 0 items in 0.0 = 0.02 match + 0.03 place
2007-01-14 15:39:40.421 Seem to be woken up by USER[/I]
so can you tell what i'm doing wrong here?
Make sure mysql is indeed running, and  check /home/mythtv/.mythtv/mysql.txt.  If the password is right in /etc/mythtv/mysql.txt, but incorrect in the one in /home/mythtv/.mythtv, the one in /home/mythtv/.mythtv takes priority.

---

### Post by Atrio05 on 2007-01-14
how do i check if mysql is running and when i try to cd to the /home/mythtv/.mythtv/mysql.txt it doesn't exist

---

### Post by superm1 on 2007-01-14
> **Atrio05 said:**
> how do i check if mysql is running and when i try to cd to the /home/mythtv/.mythtv/mysql.txt it doesn't exist

```
ps ax | grep mysql
```
To check if its running

If /home/mythtv/.mythtv/mysql.txt doesn't exist, then starting the backend via
```
sudo /etc/init.d/mythtv-backend restart
```

Will only check /etc/mythtv/mysql.txt.   So as long as this file is right, there is no reason that it shouldn't be able to connect to the mysql server.

---

### Post by edward4130 on 2007-01-18
This link below helped me with the PVR-500 and it works that same as two 150's so try it.  It is the ivtv driver that you are most likely missing.

Mine is up and running good, capture is nice now working on TV out issues (nvidia)as well as
still needing to set up the server end of the system.  Having fun along the way..!!!


[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-500)

-Edward

---

