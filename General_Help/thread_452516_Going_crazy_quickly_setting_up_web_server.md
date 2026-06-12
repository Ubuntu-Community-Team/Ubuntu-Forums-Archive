---
title: "Going crazy quickly setting up web server"
date: 2007-05-23
forum: General Help
---

### Post by SteveHillier on 2007-05-23
I am gently going off my rocker.  I have been trying for some months when time allows to set up a Ubuntu server to allow me to test websites as if in the real world from other computers on my network.
I have a WIn 2003 domain based network with Win XP workstations.  I want to set up a web server on the network running apache, PHP and MySQL.
Six massive books later I thought I was making progress but my machine dies overnight.  The latest book I have describes how to do things in Breezy, but reinstalling fro the supplied Cd has put Edgy on my machine so the book is not entirely helpful.
I had made progress so that I could access some sites as of last night but today zilch.
I don't need Linux to be my domain server - Win 2003 does that.  I don't need domain logons - Win 2003 does that.  I so want samba to share files.  I don't need this machine as DNS server because my network is set up at present behind a router running DHCP and everything automatically assigned.
My apache2 server complains that it cannot find a FQDN for this server.  My old set up did not complain but I don't know what I did on the old set up that kept it happy.
I really need an idiots guide.  In order to set the server up first set up xxxxxx in this fashion, then set up yyyyyyy to do this and then set zzzzzzz to behave like this.  None of the books I have tell me how to do this.  They say how you can set up Samba, or configure Virtual Hosts of how to set up CUPS and all the other good gear, but nothing anywhere says what I NEED to do to achieve what I want.
Any help out there would be appreciated.
Thanks to all the good guys and gals in Ubuntu land.
Steve the Pig

---

### Post by artesvida on 2007-05-23
I'm not clear what's going on, but I've found it pretty easy to get started with Apache on Ubuntu.  If you install from CD (Ubuntu server), there's even the option to install a "LAMP" server, which installs everything you need automatically.  There are a number of how-to's (some GUI, some not) out there for additional guidance:
[http://www.howtoforge.com/node/1388](http://www.howtoforge.com/node/1388)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
[http://ubuntuforums.org/archive/index.php/t-17875.html](http://ubuntuforums.org/archive/index.php/t-17875.html)
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

Some of these refer to Dapper (6.06), but I don't see how Edgy (6.10) or Fiesty (7.04) would be that different.  One of the above is all about Apache 1.3 (instead of Apache 2), so that might be helpful, depending on your needs.

Good luck!

---

### Post by upbeat.linux on 2007-05-23
artesvida pointed out some very good resources.

as for your FQDN problem it could be one of the following:

1. you did not configure your hosts file properly on install. open /etc/hosts and check for two similar lines at the top of the file:

127.0.0.1 localhost mytestbox.mydomain.com
192.168.1.80 mytestbox.mydomain.com

2. you do not have the appropriate DNS entries on your server 2003. you'll have to add these so that other computers on your network can hit this address.

you will have to restart apache service after you have made the appropriate changes.

---

### Post by SteveHillier on 2007-05-23
Thanks upbeat.linux.
I have upgraded my hosts and at least can access things on this machine.
I will tackle Win 2003 tomorrow!!!!!!!!!!!!!!!!!!!!
Steve

---

### Post by SteveHillier on 2007-05-23
Thank artesvida.
I have installed Desktop Edgy.  I have in the passed used the CD to load a LAMP server and shuddered when I got a command line prompt and no idea what to do next.
I am afraid to say that I gave up using command line around 1991 when I got Windows 3.1 and ditched MS-DOS.
I am not confident enough to know which commands in the much larger dictionary of Linux would be useful.  My excursions into the world of 'MAN' and so on leave me either with to much information (ie how to program the whole universe should I need) or such a paucity that I have no help at all.
Maybe when I am brave enough to know exactly what is required I shall go for the smaller, slicker and efficient server option.  Until then I am afraid I shall stay with the GUI using such commands as I need in the terminal.
I have however bookmarked the links you sent through and will peruse in due course.  Many thanks
Steve

---

