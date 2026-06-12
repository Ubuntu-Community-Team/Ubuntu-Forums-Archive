---
title: "Need Help ON AIGLX"
date: 2006-12-23
forum: General Help
---

### Post by timmy87 on 2006-12-23
I need Help on instaling AIGLX ,i have read the help file on ubuntu help site....which is "CompositeManager/AIGLXonDApper" ...so the problem start like this :

1) Add additional repositories

Add the following to the bottom of /etc/apt/sources.list:

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main aiglx
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main aiglx

NOTE: You have to be root to edit this file, for example:

gksudo gedit /etc/apt/sources.list
( On this point everything is ok)

You should add the GPG keys for these repositories so you don't get nasty errors:

wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -

(but ,until here it says that i should get the GPG keys for the two repositories...)

  The first repositories ive managed to get the key, but the second one "ubuntu.compiz.net"   
  I cant get the GPG key...It say like this on the terminal :-k 

 >Resolving ubuntu.compiz.net... failed: Temporary failure in name resolution.
gpg: no valid OpenPGP data found.  :-k 

can someone help me...???? im an Ubuntu 6.06 LTS user

---

### Post by hanzomon4 on 2006-12-24
Dude those howto's are so dated... Check this out for updated howto's [ One thread to rule them all v2: Beryl & Official Compiz]("http://www.ubuntuforums.org/showthread.php?t=272104")

---

### Post by timmy87 on 2006-12-24
OMG...Thanks ,i didnt know about it..haha..thanks again ...:D

---

### Post by colonel_panic414 on 2007-01-04
I already have Beryl installed, but I'm having the same Repository issue with ubuntu.compiz.net. The new guide doesn't offer a new repo, since (last I heard) ubuntu.compiz.net was down...

---

