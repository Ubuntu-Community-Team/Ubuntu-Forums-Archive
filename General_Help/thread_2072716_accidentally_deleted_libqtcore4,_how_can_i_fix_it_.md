---
title: "accidentally deleted: libqtcore4, how can i fix it (detailed description provided)"
date: 2012-10-18
forum: General Help
---

### Post by denzos on 2012-10-18
Currently running a Kubuntu 11.10, while trying to fix some dependency problems i removed the mentioned pkg. 

Immediately i tried apt-get install but i was then getting this error msg: 
```

 
E: could not get lock the administrator directory var/lib/dpkg/lock -open (11: Resource temporarily unavailable) 

E: Unable to lock administration directory (var/lib/dpkg), is another process using it ? 
```
================================================== ============

Then i went with: 

sudo kill $(cat /var/lib/dpkg/lock) 

It resulted with: 
```

:~/Documents$ sudo kill $(cat /var/lib/dpkg/lock)
cat: /var/lib/dpkg/lock: No such file or directory
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.
```

================================================== ===========

Afterwards i tried: 

```

  sudo apt-get install libqtcore4
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```

After i following the requirements, a different error message appeared: 
```

 E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```
================================================== ===========

I thought to give a try to "auto-remove": 

```

  apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dcraw digikam-data fgfs-base freeglut3 fuseiso libalut0 libchm1 libcoin60 libcvaux2.1 libdap10 libepsilon0 libgdal1-1.7.0 libgeos-3.2.2 libgeos-c1 libglew1.5
  libhdf4-0-alt libhdf5-serial-1.8.4 libkface-data libkface1 liblensfun-data liblensfun0 libnetcdf6 libogdi3.2 libopenscenegraph80 libopenthreads14
  libpackagekit-glib2-14 libpackagekit-qt2-2 libplib1 libpodofo0.9.0 libpoppler-glib6 libproj0 libspatialite2 libxerces-c28 packagekit packagekit-backend-aptcc
  proj-bin proj-data projectm-data python-beautifulsoup python-cherrypy3 python-clientform python-cssutils python-cssutils-doc python-django python-django-tagging
  python-dnspython python-encutils python-lxml python-mechanize python-packagekit python-pyparsing python-routes python-webob simgear2.0.0 swh-plugins unixodbc
0 upgraded, 0 newly installed, 56 to remove and 6 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
root@deniz-3000-N100:/home/deniz/Documents# dpkg --configure -a 
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
```
================================================== ==============

Finally i tried: 
```

 
sudo dpkg --configure -a 
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
```

---

### Post by jerrrys on 2012-10-18
First off, you sure another package like software center isn't open?

[http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html](http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html)

If thats not the case:

sudo rm /var/lib/dpkg/lock

sudo apt-get update

Getting any errors?

---

