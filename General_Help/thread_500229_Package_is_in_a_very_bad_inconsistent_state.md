---
title: "Package is in a very bad inconsistent state???"
date: 2007-07-13
forum: General Help
---

### Post by dgcarter on 2007-07-13
Is this problem fixable? I have tried googleing, and everything I know and I just can't fix it.

I'm trying to fix up my Openfire XMPP Server package, this is what i get:

```

root@inter-net:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
E: The package openfire needs to be reinstalled, but I can't find an archive for it.
root@inter-net:~# dpkg --configure -a
dpkg: error processing openfire (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 openfire

```

---

### Post by Happy_Man on 2007-07-13
I would suggest clearing APT's cache of .debs..... it's in /var/cache/apt/archives. Perhaps that will do the trick....

---

### Post by omkarwagh on 2007-09-11
run the dpkg in the terminal. ive had the same error happen to me thrice and i guess this is what i did

look very closely in the error messages. all three times with me at least it said something like some particular file is missing or does not exist.
solution:- simply create a blank file of that name in the directory where the error occurs. then ask dpkg to remove the package. that worked for me at least.

---

### Post by kewldude606 on 2008-01-22
I know this thread is a bit old but I just stumbled upon it in a search and wanted to share how I fixed my problem.

I did:```
cd /tmp/
aptitude download <package>
sudo dpkg -i <package>

```

dpkg came up with an unresolved dependency, so I used aptitude to install it.  Aptitude then finished the installation of the 1st package and all was done :-).

---

