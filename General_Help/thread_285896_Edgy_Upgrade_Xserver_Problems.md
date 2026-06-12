---
title: "Edgy Upgrade Xserver Problems"
date: 2006-10-27
forum: General Help
---

### Post by lastrite on 2006-10-27
After upgrading to edgy using 'apt-get dist-upgrade' xserver fails to start. When I try log in I get '-bash /dev/null Permission Denied' repeatedly. I can however login using recovery mode but when I try install xserver-xorg I get quite a few dependency errors  and it refuses to install. 

I tried apt-get -f install as it recommends after the errors, that corrected some of the problems but I get still get some relating to xserver-xorg-video and koffice  ](*,) 

Any help would be much appreciated :(

---

### Post by lastrite on 2006-10-27
Also when logging in via recovery mode it says 'Cannot set LC_ALL to default locale' and asks for a password to use for maintenance. 

I tried apt-get update then upgrade but its appears it can't even connect to anything (connected directly to internet via ethernet) as it gives me unresolved errors :(

---

### Post by johnb820 on 2006-10-27
While upgrading to edgy it told me I needed to install x11-common because I had dependency problems installing xserver-xorg.  An x11-common deb file in my archives directory refused to unpack.  I don't know if I should have but I ended up forcing it to unpack by saying

sudo dpkg -i --force-overwrite 'file path'

I don't know if that might help or not but that was the problem I ran into upgrading to edgy eft.  It gave me quite a bit of aggravation.  A good learning experience though.

---

