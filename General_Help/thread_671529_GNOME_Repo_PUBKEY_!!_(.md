---
title: "GNOME Repo PUBKEY ?!?! :("
date: 2008-01-18
forum: General Help
---

### Post by Cygoku on 2008-01-18
Here : 

[http://www.nanolx.org/index.php?option=com_content&task=view&id=47&Itemid=30](http://www.nanolx.org/index.php?option=com_content&task=view&id=47&Itemid=30)

... they talk about a repo and it's pubkey ... but where do I find that **** pubkey?  

Cygoku

---

### Post by Cygoku on 2008-01-18
bump

---

### Post by ThrobbingBrain66 on 2008-01-18
The repo maintainer seems to keep the key in the nanolx-key package.  Seems kind of odd that you have to download a package to get the key though.  Most maintainers display the key on their webpage.

---

### Post by ~LoKe on 2008-01-18
Try...
```
wget http://www.nanolx.org/nlx.asc
apt-key add nlx.asc
```

---

### Post by Cygoku on 2008-01-19
This is the error message that I get : 

cygoku@paralyzeuz:~$ wget [http://www.nanolx.org/nlx.asc](http://www.nanolx.org/nlx.asc)
--08:06:15--  [http://www.nanolx.org/nlx.asc](http://www.nanolx.org/nlx.asc)
           => `nlx.asc'
Resolving [www.nanolx.org](www.nanolx.org)... 212.78.206.150
Connecting to www.nanolx.org|212.78.206.150|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
08:06:15 ERROR 403: Forbidden.

cygoku@paralyzeuz:~$ apt-key add nlx.asc
gpg: can't open `nlx.asc': No such file or directory
cygoku@paralyzeuz:~$ 

Cygoku

---

### Post by Cygoku on 2008-01-19
This : 

[http://download.tuxfamily.org/gnome4sid/dists/voyager/Release.gpg](http://download.tuxfamily.org/gnome4sid/dists/voyager/Release.gpg)

... didn't worked either! :(

Cygoku

---

### Post by Cygoku on 2008-01-19
bump

---

### Post by Cygoku on 2008-01-19
bump

---

### Post by Cygoku on 2008-01-20
bump

---

### Post by SovereignLX on 2008-02-12
oh ... the permissions of my key where wrong ... try again:

wget [http://www.nanolx.org/nlx.asc](http://www.nanolx.org/nlx.asc)
apt-key add nlx.asc

Furthermore: Don't use that packages unless you know what you're doing, this are _unstable_ Gnome Packages.

---

