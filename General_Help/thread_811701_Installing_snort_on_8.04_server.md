---
title: "Installing snort on 8.04 server"
date: 2008-05-29
forum: General Help
---

### Post by ic_penguin on 2008-05-29
I've installed snort before, and haven't had too many problems, but I'm really running into a head scratcher here.

I installed ubuntu server 8.04, and went ahead and did the LAMP install.

I've got all the prerequisites for snort; libpcap, etc.

Downloaded snort 2.8.1 from snort.org, compiled it with the --with-mysql flag, installed it, and if I run snort -c /etc/snort/snort.conf, it goes fine until I get this:

> 
Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( )
database: configured to use mysql
database: 'mysql' support is not compiled into this build of snort

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..



I didn't get any errors when I configured the package with the mysql option, but it still seems to be acting like it wasn't configured right.

The only strange thing I noticed was when I went to run snort the first time, it said it couldn't find snort in /usr/sbin, so I created a symlink to /usr/local/bin/snort and it ran until I got the error message.

Any ideas?

---

### Post by bodhi.zazen on 2008-05-29
See if these links help :

[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10)

[http://www.howtoforge.com/intrusion_detection_snort_base_postgresql_ubuntu6.06](http://www.howtoforge.com/intrusion_detection_snort_base_postgresql_ubuntu6.06)

---

### Post by ic_penguin on 2008-05-29
Yeah, thats the guide that I was using as a rough guide. I've double checked, and I have done all those steps, and nothing works.

---

### Post by jkeating on 2008-09-30
This is an old post so not sure if you've figured this out already but I followed this guys post...

[http://rm-rf.co.uk/2008/07/snort-3-beta-on-ubuntu-debian-installation/](http://rm-rf.co.uk/2008/07/snort-3-beta-on-ubuntu-debian-installation/)

I used Ubuntu 8.04 jeOS with Snort-2.8.3...a base install but a good starting point.

---

### Post by joskevermeulen on 2008-10-15
Hello,

I used the same tutorial as you did, and got the same problem/error. Snort works, but the integration with the mysql db doesn't work.
I tried to recompile snort with the flag --with-mysql=/usr.
But no succes :s, still got the same error. 
Maybe with postgresql it will go better??

---

### Post by bodhi.zazen on 2008-10-15
[[all variants] Intrusion Detection - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=919472")

See if that tread helps.

---

### Post by FlapBags on 2009-12-27
Um, did you try
 
sudo apt-get install snort
 
Its pretty straight forward.

---

