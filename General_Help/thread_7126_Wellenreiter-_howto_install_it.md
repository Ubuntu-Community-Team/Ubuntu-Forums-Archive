---
title: "Wellenreiter- howto install it?"
date: 2004-12-04
forum: General Help
---

### Post by Borgmeister on 2004-12-04
Hi again, i know this isnt directly related to ubuntu, but i have downloaded the Wellenreiter tar, but i cannot work out howto install it, the file came with linux.install, but ubuntu doesnt seem to know what kind of file it is, this has turned into a real stumper for me, i have googled for an answer, and the website does not have any guide to where i have gone wrong.

So far i have untarred the app, but it has not made a directory, so i cannot cd into it to 

./make
./make install.

Please help

---

### Post by WimVriend on 2004-12-04
[QUOTE=Borgmeister]Hi again, i know this isnt directly related to ubuntu, but i have downloaded the Wellenreiter tar, but i cannot work out howto install it, the file came with linux.install, but ubuntu doesnt seem to know what kind of file it is, this has turned into a real stumper for me, i have googled for an answer, and the website does not have any guide to where i have gone wrong.

So far i have untarred the app, but it has not made a directory, so i cannot cd into it to 

./make
./make install.

Please help[/QUOTE]

Is there no readme or install file

---

### Post by poofyhairguy on 2004-12-04
[QUOTE=Borgmeister]Hi again, i know this isnt directly related to ubuntu, but i have downloaded the Wellenreiter tar, but i cannot work out howto install it, the file came with linux.install, but ubuntu doesnt seem to know what kind of file it is, this has turned into a real stumper for me, i have googled for an answer, and the website does not have any guide to where i have gone wrong.

So far i have untarred the app, but it has not made a directory, so i cannot cd into it to 

./make
./make install.

Please help[/QUOTE]

Well dude, I want to help you, but I think compiling from source is the devil.

Instead I find the packages I need on google. Here is a deb package I found:

[http://www.ucc.gu.uwa.edu.au/~dagobah/~dagobah/debian/pool/wellenreiter/wellenreiter_1.6-1_i386.deb](http://www.ucc.gu.uwa.edu.au/~dagobah/~dagobah/debian/pool/wellenreiter/wellenreiter_1.6-1_i386.deb)

I found that this package has these dependancies:

perl (>= 5.6.0), libgtk-perl, libnet-pcap-perl 

all of those you can get with apt-get. 

I know its not the newest version, but I can't help you otherwise.

---

