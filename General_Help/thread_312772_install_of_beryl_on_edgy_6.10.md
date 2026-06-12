---
title: "install of beryl on edgy 6.10"
date: 2006-12-04
forum: General Help
---

### Post by STREETURCHINE on 2006-12-04
installing beryl according to this guide

Beryl & Nvidia with XGL on GNOME

run into some trouble here

rex@rex-desktop:~$ wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
--11:58:15--  [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc)
           => `-'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.113.152.130
Connecting to www.beerorkid.com|208.113.152.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,692 (1.7K) [text/plain]

100%[====================================>] 1,692          7.91K/s             

11:58:33 (7.90 KB/s) - `-' saved [1692/1692]

OK
rex@rex-desktop:~$ sudo apt-get update
E: Type 'd' is not known on line 2 in source list /etc/apt/sources.list
rex@rex-desktop:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
rex@rex-desktop:~$ 


so now can some one please guide me through this ,thanks](*,)

---

### Post by STREETURCHINE on 2006-12-05
ok fixed that one but now i have a blank screen after i log in ,can anyone help with this one ,thanks

---

### Post by STREETURCHINE on 2006-12-05
ok got that one sorted out, but now beryl wont start have no idea how to fix this one '.
when i type beryl in terminal everything freezes ,any one out there have a solution to this ,thanks

 com'on people it is boring talking to myself.lol:-D

---

### Post by RAOF on 2006-12-05
Hm, that howto appears both old, and for Dapper.  Maybe you should try one of the howto's from the "Edgy" section of the sticky thread at the top of the forums?

---

### Post by STREETURCHINE on 2006-12-05
it is old and it has a section for edgy as well so i tried it out but no go yet.

---

### Post by RAOF on 2006-12-05
Ok, we're obviously looking at different howtos.  Please post a link to the one you've followed!

Oh, and at least one solution will probably be to use beryl-manager rather than just trying to start beryl manually.  But I use Compiz, so I'm not sure of the arcanae required.

---

### Post by STREETURCHINE on 2006-12-05
hi i have the beryl manager but it does nothing,the how to i used is from same how to just clicked on the wrong link sorry.this is what i was doing 
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

just dont know what to do now ,i got it working first time around on dapper, but running into trouble here .

---

