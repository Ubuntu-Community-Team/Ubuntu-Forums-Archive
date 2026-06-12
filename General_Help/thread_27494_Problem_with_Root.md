---
title: "Problem with Root"
date: 2005-04-16
forum: General Help
---

### Post by satty on 2005-04-16
Hello.  I have been trying to install [Nagios](http://www.nagios.org) on a spare box.  At some point in the installation I lose the ability to sudo into root.  I only saw one thread [here](http://ubuntuforums.org/showthread.php?t=19671) that talked about the same error message that I get.  "Child terminated with 1 status" when I try to launch any number of programs that require the root's password.  For example: Synaptic Package Manager, Root Terminal, etc.  The next post is a copy of everything that I have done with the box.  Please look over it and see where I goofed.  

Originally I tried this at work, but after 3 "redo's" I decided to figure it out at home.
PC: Dual Pent 3 with 2Gb RAM and 4 9Gb SCSI drive
Thanks Ben Satterfield

---

### Post by satty on 2005-04-16
Here are my installation notes.  
Thanks, Ben

Net Saint Installation Notes
(04/16/05)

Documented to figure out what I am doing wrong.
Installed Ubuntu 5.04
User: nagios
Pass: 123456

Installed the GCC package through Synaptic Package Manager

Downloaded Apache 2.0.53

In a terminal typed,
mkdir /usr/local/apache
chmod 777 /usr/local/apache
cd /home/nagios/apps/httpd-2.0.53
./configure --prefix=/usr/local/apache
make
make install
cd /usr/local/apache/bin
./apachectl start

Tested page from another computer..Apache worked.

Downloaded nagios 2.0b3
mkdir /usr/local/nagios
chown nagios.nagios /usr/local/nagios
chmod -R 777 /usr/local/apache

vi /usr/local/apache/conf/httpd.conf
--changes maded
"Listen 80" to "Listen 192.168.200.251:80"
"User nobody" to "User nagios"
"Group #-1" to "Group #1000"
Saved the httpd.conf

grep "^User" /usr/local/apache/conf/httpd.conf
the result was "User nagios" and "UserDir public_html"

/usr/sbin/groupadd nagcmd
/usr/sbin/usermod -G nagcmd nagios

cd /home/nagios/apps/nagios-2.0b3

--end of notes.  At this point I notice I have lost root.

---

### Post by matthieufecteau on 2005-05-03
I think I had the same problem because my loopback interface was not started at boot.

Read the second post of this thread to look further : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

