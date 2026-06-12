---
title: "MythTV MySQL noob help"
date: 2004-12-16
forum: General Help
---

### Post by WattoDaToydarian on 2004-12-16
Hey guys, I'v been tryin to install MythTV and i keep gettin a problem with the mythtv-database package. I get this error message...

Setting up mythtv-database (0.16-1) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.16-1); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
  :confused: 
I'v tried the "dpkg-reconfigure --force mythtv-database" command and used it to change the user and pass a few times with no luck. Can anyone help me with this that knows how to get this installed?
Thanks! 8-)

---

### Post by mr_ed on 2004-12-16
Disclaimer:  I have never done this, and have never installed MySQL, but I may be able to give you a start point.

First, the root user is disabled, but I believe you need to create a root user for your MySQL database.

---

### Post by AnGeLiX on 2005-01-22
You should do this:

$ sudo /usr/bin/mysqladmin -u root password your_db_user_password

Excellent Guide for all the newbies (including myself :) ) [http://ubuntuguide.org/#installmysqldatabaseserver](http://ubuntuguide.org/#installmysqldatabaseserver)

---

### Post by Joshua on 2005-03-17
So, let me get this straight:

1) $ sudo /usr/bin/mysqladmin -u root password your_db_user_password
2) $ sudo aptitude install mythtv
3) follow promts

and that's it?

---

### Post by WattoDaToydarian on 2005-03-17
After you install MythTV you do "sudo /usr/bin/mysqladmin -u root password your_db_user_password" where "your_db_user_password" is the password you used when you installed mysql with myth.

... At least I think thats right. If that dosn't work just search google for how to change the root password for mysql. It's probly gunna take some work. Mythtv is still beta so dont expect everything to work right (I had to learn the hard way ;-) ).

---

### Post by madjo on 2005-09-09
okay, sorry for reviving this old-ish thread, but I am having difficulties with setting mythtv up.
I followed the instructions given here...
I gave the root user of MySQL a password, entered that one in the configuration of Mythtv's database backend. but still no luck.
I keep getting this error upon the start of mythtv:
```
2005-09-09 19:53:24.552 Switching to square mode ()
2005-09-09 19:53:24.559 Unable to connect to database!
2005-09-09 19:53:24.560 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-09-09 19:53:24.560 Switching to square mode (blue)
Segmentation fault
```and if I try to create a mythtv user I get the same access denied error:
```
mysqladmin -u mythtv password SomeRandomPassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'mythtv@localhost' (Using password: NO)'
```

---

### Post by madjo on 2005-09-09
never mind, I got it to work :)

I created a new user for mysql, and made sure that it was loaded.
then started mythbackend, which tried to connect, and fails. It then asks if you wish to set the database settings... yes
then it asks a few questions, most things can be left to the default, **except** the username and password, change this to your newly created user and password. follow the rest of the 'wizard'.. and then afterwards you can use mythtv :) (at least you can start the setup now) :)

---

### Post by nzruss on 2006-02-05
i'm really stuck here too. Keep getting the same Database error. Real noob to linux here, (just 2 days). 

Really need a step-by-step of what to do to get the database working for mythTv. 

"Unable to connect to database"

please help. 

how do you create new SQL db users and get them running etc?

thanks in advance

NZruss

---

### Post by WattoDaToydarian on 2006-02-05
Hey nzruss, did you do```
mysql < /usr/share/mythtv/sql/mc.sql
```That creates the MythTV database.
You might also want to make sure MySQL is running by doing ```
/etc/init.d/mysql restart
```I also strongly recommend you take a look at [http://digitalboy.mythtvtalk.com/files/MythTvTunerGuide.pdf](http://digitalboy.mythtvtalk.com/files/MythTvTunerGuide.pdf) this has a list of known cards that work with mythtv, you might be able to get a card thats not on there to work but it's vary iffy.:-| 
Have fun!\\:D/

---

### Post by nzruss on 2006-02-06
Tried that, 

I'm missing something really simple. (plus I have no idea what any of this means, but i'm reading up on Linux tutorials etc as quick as i can!) 


Tried this:

number2@Number2:~$ mysql < /usr/share/mythtv/sql/mc.sql

Got this:

ERROR 1045: Access denied for user: 'number2@localhost' (Using password: NO)
number2@Number2:~$

Then Tried this:
/etc/init.d/mysql restart

and got this:
Stopping MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permission denied
...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'number2@localhost' (Using password: NO)'
Killing MySQL database server by signal: mysqldmysqld(7111): Operation not permitted
mysqld: no process killed
Starting MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permission denied
...already running.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'number2@localhost' (Using password: NO)'
number2@Number2:~$


anyone got simple tips for a total noob. Pls.

---

### Post by nzruss on 2006-02-06
Tried both those. I'm missing something fundamental. 

this is what i get:

number2@Number2:~$ /etc/init.d/mysql restart
Stopping MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permission denied
...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'number2@localhost' (Using password: NO)'
Killing MySQL database server by signal: mysqldmysqld(7111): Operation not permitted
mysqld: no process killed
Starting MySQL database server: mysqldcat: /var/run/mysqld/mysqld.pid: Permission denied
...already running.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'number2@localhost' (Using password: NO)'
number2@Number2:~$

---

### Post by WattoDaToydarian on 2006-02-06
oops, whenever you restart a service like mysql you need to do it as root by putting a sudo before the command. "sudo /etc/init.d/mysql restart"

---

### Post by nzruss on 2006-02-06
Will try that tomorrow. Thanks in advance. Am reading [http://www.linux-tutorial.info](http://www.linux-tutorial.info) to get a grasp of the concepts. I'll be up and running before you know it!

Just wish installing MythTv was as easy as installing ubuntu!!!

---

### Post by nzruss on 2006-02-07
[QUOTE=WattoDaToydarian]oops, whenever you restart a service like mysql you need to do it as root by putting a sudo before the command. "sudo /etc/init.d/mysql restart"[/QUOTE]

OK, that worked, 

i got this:
------------------------
number2@Number2:~$ sudo /etc/init.d/mysql restart
Password:
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld.
Checking for crashed MySQL tables in the background.
number2@Number2:~$ 
------------------------------

now what?

I typed "Mythtv" into the command line, got a few driver errors and then the MythTV database initialisation screen. Not sure what to enter in there, but put in my system password and user, and it goes to next screen. I get no options there, click next, then it crashes back to the command line.   

The driver error:
---------------
2006-02-07 20:31:27.324 Database not open while trying to load setting: Language
2006-02-07 20:31:27.328 Unable to connect to database!
2006-02-07 20:31:27.328 Driver error was [1/1130]:
QMYSQL3: Unable to connect
Database error was:
Host 'localhost.localdomain' is not allowed to connect to this MySQL server
----------------------

then when it crashes, i get: 

------------------------
2006-02-07 20:31:53.835 Failed to init MythContext, exiting.
number2@Number2:~$ mythcontext
bash: mythcontext: command not found
number2@Number2:~$
---------------------------

I was expecting some issues cos i'm using a Brooktree BT878 Video and FM Tuner, But was hoping to at least get the non-tv recording, like the music/internet/mail/weather/pictures features running first. (I've had the TV playing in some system manager random window early on, but cant remember how).... so i think the BT878 is working ok.. 

Can anyone help in setting up that blue data base screen.....

I'm getting there, slowly. 

Thanks so much for your patience and help so far! I really appreciate it. 

NZRuss

---

### Post by WattoDaToydarian on 2006-02-07
Does it work now?

---

### Post by nzruss on 2006-02-07
number2@Number2:~$ sudo aptitude install mythtv
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by WattoDaToydarian on 2006-02-07
you cant run any package managing programs while your doing it such as apt, aptitude, or synaptic.

---

### Post by nzruss on 2006-02-07
crap. 
 O.k. seems i need to read up on that, does that mean i need to shut down the browser?

I can restart the SQL database ok. that i can do. 

I can get to the initialisatoin screen of Mythtv database.. and not sure what it all means.

---

### Post by nzruss on 2006-02-08
OK, 

I uninstalled mythtv and all the associated dependencies, and anything related. 

Reinstalled mythtv and all the dependencies etc, and got this error after they loaded:

mythtv-database: subprocess post-installation script returned error exit status 1
E: mythtv: dependency problems - leaving unconfigured

... now of to read how to fix it...

---

### Post by nzruss on 2006-02-12
Got it up and running. - started from scratch and didnt have too many problems. I'm alot more confident in the Linux command line environment now too!

Just having problems tuning the TV. - am going to ditch the bttv (Tview bt8x8') and get the PVR 150/250.  

and i have to say thanks to WattoDaToydarian... got a heaps of help over aMsn.. cheers!!!   Give that man some beans. 

Next step is communicating with the Directv low speed port....

any tips anyone?

---

### Post by WattoDaToydarian on 2006-02-12
I have the PVR-150 and it works perfectly! but i dont know anything about talking to the DirectTV reciever, i dont think it's possible...:confused: 
Is it a serial comminuications port? If it has a baud rate and stuff listed on it mayb you can connect a null modem cable to it and open up a terminal to talk to it.

---

### Post by nzruss on 2006-04-04
OK. Got it working in the end. I started from scratch and followed Daniel Hymes instructions here: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

His instructions are really very good. I'll flick him some beer money once its integrated to the lounge.

---

### Post by nzruss on 2006-04-09
I got the PVR-150, and to my surpirse it has a blaster built in. I've been searching around and the closest i've come is here: [http://www.blushingpenguin.com/mark/blog/?p=24](http://www.blushingpenguin.com/mark/blog/?p=24)

I had some problems getting this to work though. I posted my issues here: [www.nzruss.blogspot.com](www.nzruss.blogspot.com) (i'll leave a How-to there once ive got it resolved). 

so it seems possible, but just in its infancy. 

i'll be looking until i get this resolved.

---

### Post by WattoDaToydarian on 2006-04-09
If you want a dedicated MythTV box then I highly recommend using Knoppmyth @ [http://mysettopbox.tv/](http://mysettopbox.tv/) which is a distro made for that! It has many scripts that simplify everything including IR Blaster support and many How-TOs like this one [http://mysettopbox.tv/phpBB2/viewtopic.php?t=9542](http://mysettopbox.tv/phpBB2/viewtopic.php?t=9542)
I'm currently using this for my dedicated myth box and my PVR-150 and pcHDTV-2000 worked perfectly out of the box!
However I havn't setup my IR Blaster because I havn't any need for it.
Good Luck!:)

---

### Post by nzruss on 2006-04-09
I hear what your saying, but i'm pretty happy with ubuntu in the living room and on the TV. (that is where i'm typing this from). Plus i've already put some of my DVD collection on and dont really want to mess with it. I didnt discover knoppmyth till after I got ubuntu up and running, but it might suit the next person to read this. CHeers for your help and advice though.

---

