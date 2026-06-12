---
title: "Repos gpg key missing"
date: 2006-12-03
forum: General Help
---

### Post by ajgreeny on 2006-12-03
I have tried to add the plf repos
[http://packages.freecontrib.org.ubuntu/plf](http://packages.freecontrib.org.ubuntu/plf) dapper
to my dapper system's sources.list for both binary and source, but when I try to update it I get the error message:-
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

I'm sure there must be a way to overcome this using wget, but all I've tried has not helped.  Can anyone tell me what I should do, or are the repos no longer available?  I'm not even sure if this means I can't download software from these repos or if the warning is just that, a warning, rather than something that stops me using the repos.

---

### Post by bapoumba on 2006-12-03
To get the gpg key :
```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add
```

To add it to your trusted keys :
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x12B83718 ;  gpg --export -a 0x12B83718 | sudo apt-key add -
```

Check that the following are in your /etc/apt/sources.list :
```

deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
```

[URL="http://packages.freecontrib.org/ubuntu/plf/"]
http://packages.freecontrib.org/ubuntu/plf/[/URL]

---

### Post by ajgreeny on 2006-12-03
Thanks bapoumba, I knew there was an easy way to do it but couldn't remember how.  Incidentally after doing the first code:-

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add

the terminal froze and I could only do the rest by opening another terminal.  It all works OK now but is that freezing usual, or is it rather strange?

Whatever the answer, many thanks for such a speedy and helpful reply.

---

### Post by bapoumba on 2006-12-03
Well, the freeze is not normal. May be it took quite a while to get the key for some obscure/magical/forever unknown reason ... Not sure though :)

So for the easy way, I just typed "plf" in a google search to get to the page I've linked ;)

---

### Post by ajgreeny on 2006-12-04
Wow!  That simple.  Many thanks.

---

### Post by wesley_of_course on 2006-12-12
Resolving packages.freecontrib.org... gpg: can't open `': No such file or directory
88.191.33.6
Connecting to packages.freecontrib.org|88.191.33.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
01:20:49 ERROR 404: Not Found.


 Same story here too !

     Is it my system ???????                  ](*,)

---

### Post by bapoumba on 2006-12-13
@ wesley_of_course : the repos have changed :
[http://ubuntuforums.org/showpost.php?p=1875573&postcount=8]("http://ubuntuforums.org/showpost.php?p=1875573&postcount=8")

I wrote a little translation here :
[http://bapoumba.free.fr/?p=13]("http://bapoumba.free.fr/?p=13")
and contacted the wiki team ;)

---

