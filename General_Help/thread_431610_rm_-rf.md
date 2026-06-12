---
title: "rm -rf"
date: 2007-05-03
forum: General Help
---

### Post by darfel on 2007-05-03
Hi.

I've done a rm -rf inside /var... so i'm having some problems running certain applications, like apt-get, adept, etc.

I've already tried to install them from sources, but i'm having some errors and no success.

Is there any "easy" to do a repair to ubuntu without having to install everything? Like running the release update or any other thing?

PS: I'm using ubuntu 7.04 and already tried the «gksu "sh /cdrom/cdromupgrade"» command, but it just gives an error too...

---

### Post by visik7 on 2007-05-03
no way man
/var contains status of installed and available packages and other things vital for your distro 
it's better to run rm -rf inside /usr than inside var 
I suggest you to do a clean install

---

### Post by darfel on 2007-05-03
really?? 

and can i install without formatting? keeping my actual personal files?

---

### Post by zvacet on 2007-05-03
You can leep your personal files if you have separate home partition.If you don´t have it just make one.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

And for the future, if you want to clean var/cache/apt/archieves do it with this command

```
sudo apt-get autoclean
```

This will delete older versions of programs and leave you just with latest.That way you can get some free space without losing anything.

---

