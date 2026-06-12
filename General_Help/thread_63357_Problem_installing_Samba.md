---
title: "Problem installing Samba"
date: 2005-09-07
forum: General Help
---

### Post by jhuff on 2005-09-07
I'm trying to install Samba and I get the following error:

samba:
  Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed

Does anyone know how to resolve this dependency issue.  I thought of uninstalling samba-common, but it looks like it will uninstall both KDE and Gnome desktops.

I use KDE that has been installed on top of ubuntu.

---

### Post by mlomker on 2005-09-07
Have you run an upgrade recently?

apt-get update
apt-get upgrade

If that doesn't resolve it then perhaps there's something wrong with the /etc/apt/sources.list file?

---

### Post by jhuff on 2005-09-09
[QUOTE=mlomker]Have you run an upgrade recently?

apt-get update
apt-get upgrade

If that doesn't resolve it then perhaps there's something wrong with the /etc/apt/sources.list file?[/QUOTE]
I tried the apt-upgrade and it did not work.  Does anyone know if I uninstall samba-common if it will uninstall both KDE and Gnome desktops as well?

---

### Post by jhuff on 2005-09-20
Can anyone direct me to a good resource for fixing dependency problems.  I would really like to get samba installed.

---

### Post by Frankk on 2005-09-20
Same problem here, seems that both apt-get and synaptic see only samba 3.0.10

---

### Post by az on 2005-09-20
"samba:
Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed"

You have breezy repositories enabled.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=samba-common](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=samba-common)

3.0.10 is in Hoary, 3.0.14a is in breezy.  Remove the breezy repos, update and try again.  

If it still reports an error, post it.  If you have some breezy packages that have breezy dependancies that involve samba, you will have to take care of them.

---

### Post by Frankk on 2005-09-20
I dont have any breezy repositories enabled in sources.list
As you can see [here](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/)  samba 3.0.14 is in hoary-backports.

If I remove backports from my repos samba 3.0.10 is correctly installed.

Sorry if I misunderstood you.

---

### Post by nmarquart on 2005-09-22
Hey

[QUOTE=jhuff]I'm trying to install Samba and I get the following error:

samba:
  Depends: samba-common (=3.0.10-1ubuntu3) but 3.0.14a-3ubuntu3~5.04ubp1 is to be installed
[/QUOTE]


Beeing a total n00b in Linux im getting the same message!

I have tryed to do the things above, but whitout luck! 

Somebody please tell me what to do!

By the way im running ubuntu i danish!

/Nikolaj

---

### Post by nmarquart on 2005-09-22
I followed this at it worked!

[http://www.ubuntuforums.org/showthread.php?t=68067&highlight=%3D3.0.10-1ubuntu3](http://www.ubuntuforums.org/showthread.php?t=68067&highlight=%3D3.0.10-1ubuntu3)

/nikolaj

---

### Post by jhuff on 2005-09-24
[QUOTE=nmarquart]I followed this at it worked!

[http://www.ubuntuforums.org/showthread.php?t=68067&highlight=%3D3.0.10-1ubuntu3](http://www.ubuntuforums.org/showthread.php?t=68067&highlight=%3D3.0.10-1ubuntu3)

/nikolaj[/QUOTE]

Thanks!! for the link, it Worked.

---

