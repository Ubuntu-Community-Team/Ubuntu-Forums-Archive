---
title: "How to install Oracle SQL Developer in Ubuntu?"
date: 2013-08-26
forum: General Help
---

### Post by zpierce on 2013-08-26
As the title says, I'm trying to install Oracle SQL Developer 4.0 in Ubuntu 13.04.  This is for a class I'm in, but the textbook only provides instructions for Windows, and I'm not finding any current guides when I google it.  First problem is that the download is .rpm, which, although I am a noob here, I understand Ubuntu doesn't work with.  Anyone know how I can get this installed?  I've seen several other threads of people talking about using SQL Developer in Ubuntu, so I'm fairly confident there is a way.
Any help is appreciated.

---

### Post by zpierce on 2013-08-26
Update: I used alien to convert and install the .rpm download file
Command: alien -d -i --scripts sqldeveloper-4.0.0.12.27-1.noarch.rpm
No errors, and it created /opt/sqldeveloper/
I attempted to open the sqldeveloper.exe file in this directory and got Archive Manager "An error occurred while loading the archive"

---

### Post by zpierce on 2013-08-27
Shameless bump.  I can't be the only person using Oracle on Ubuntu.

---

### Post by yamel2 on 2013-09-04
Hi there, I hope you can help me out here. Well the good part is that you are not the only one who uses Oracle SQL developer on Ubuntu. I am currently trying to install it but I have ran into a lot of problem.
Can you please tell me or show me how you go it installed and how you install JDK for SQL. When I give the path to the jdk sql says not jdk folder or file found.

---

### Post by zpierce on 2013-09-04
Hi, I actually did manage to get SQL Developer working and would be happy to help you.
First, what Oracle DB are you running?  I've got Oracle Database Enterprise Edition 11g R2 running on Ubuntu 13.04 64-bit.  I'm using OpenJDK (you can grab v7 in the Software Center, it worked fine for me).  Let me know where you're at and I'll try to help you out.

---

### Post by yamel2 on 2013-09-04
Hi!

   I am trying to install Oracle SQL developer edition, the latest one on Oracle download page on Ubuntu 12.04 64 bit With jdk 6. I downloaded it and unzipped it using archive manager, got my ./sqldeveloper.sh file to run. I go to the folder were is the file and run it, then SQL launches and is running as long as I don't close the terminal or command application.  

 

 Question: is that a successful installation?, if yes I need help with getting it to work without lunch it from the terminal every-time I want to run SQL. Do you know how can I get that fixed?
 

 When I run the .sh file from the terminal the is a message that says that the path will be saved into a directory called .sqldeveloper in home, I can see and go inside the directory but actually it does not save the path in there.


terminal message while I am running SQL:

yamel@yamel-Satellite-C855:~/Application/sqldeveloper$ ls
dataminer  jdbc        jviews       sleepycat             sqldeveloper.sh
icon.png   jdev        modules      sqldeveloper          sqlj
ide        jdev.label  rdbms        sqldeveloper.desktop  timingframework
javavm     jlib        readme.html  sqldeveloper.exe      view-source-paths.lis
yamel@yamel-Satellite-C855:~/Application/sqldeveloper$ ./sqldeveloper.sh 

Oracle SQL Developer
 Copyright (c) 1997, 2011, Oracle and/or its affiliates. All rights reserved. 

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.sqldeveloper/jdk
/usr/lib/jvm/java-6-openjdk-i386

well, thank you and I hope you can help me!

---

### Post by zpierce on 2013-09-05
Well, I have to launch SQL Developer from the command line [./sqldeveloper.sh] from within my /opt/sqldeveloper folder, and the terminal has to stay running while doing so.  I tried once to set up a shortcut on the desktop and launcher, but it didn't work and I don't mind working from the terminal, so I haven't gone back to it.
I know I had to provide my path for OpenJDK when I first launched it, but that worked fine for me and I haven't gotten that message since.  If everything else is working (the actual application is launching fine), I would suggest removing and reinstalling OpenJDK and making sure you have the path set up correctly.

---

### Post by yamel2 on 2013-09-05
Hi, thanks!

I have an error when I try to create a new connection in sql developer that says: IO error the network adapter could not connect or something like that.
I am using a local host for the connection!

do you know how to fix that problem?
thanks for everything!

---

### Post by zpierce on 2013-09-05
Hey, when I try to create a new connection, I'm getting:
Status : Failure - Test failed: LIstener refused the connection with the following error: ORA-12505, TNS: listener does not currently know of SID given in connect descriptor
Is that what you're getting?  I'm at work right now but I'll try to fix this later and post what I do and the result if this is what you're facing.  Sorry I can't help faster, but I'm completely new at this too.

---

### Post by Stefano_Baghino on 2014-02-11
I would suggest another approach (it worked for me): instead of installing the RPM package, you could download the tarball intended for other platforms (i.e.: other Unix platforms), place it wherever you want (/opt/sqldeveloper sounds fine) and manage it outside APT. You could then add this to make sure you can run it from anywhere in the filesystem:
```

# make sure that the sqldev installation ownership goes to the superuser
sudo chown -R root:root /opt/sqldeveloper

# make anybody able to run the sqldeveloper.sh script and the related executables
sudo chmod a+x /opt/sqldeveloper/sqldeveloper.sh
sudo chmod a+x /opt/sqldeveloper/sqldeveloper/bin/sdcli
sudo chmod a+x /opt/sqldeveloper/sqldeveloper/bin/sqldeveloper

# creates a one-line script that runs the sqldeveloper gui
sudo echo "/opt/sqldeveloper/sqldeveloper.sh > /dev/null 2> /dev/null &" > /usr/bin/sqldeveloper 

# make sure that anybody can run the sqldeveloper one-liner
chmod a+x /usr/bin/sqldeveloper

```
Assuming that /usr/bin is in your $PATH environment variable (it should) you could now run it from the terminal or in Unity after hitting Alt+F2.

---

