---
title: "alltray"
date: 2006-10-16
forum: General Help
---

### Post by dontgetshocked on 2006-10-16
I cant manage to get this software installed correctly so that it works
I followed the install file instructions with no success.
anyone know of a easier way or different?

---

### Post by ayoli on 2006-10-16
i used this repos to have alltray before (i dont use alltray anymore):
```
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
```
add it to your /etc/apt/sources.list
then:
```
sudo aptitude update && sudo aptitude install alltray
```

---

### Post by dontgetshocked on 2006-10-16
Thanks,

That worked
Although I changed the french to english

---

### Post by kinson on 2006-12-01
Hi,

I've followed your instructions up there (even tried changing "french" to "english", but when i perform "sudo aptitude update" I get:

```
kinson@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Ign http://asher256-repository.tuxfamily.org dapper Release.gpg
Ign http://asher256-repository.tuxfamily.org ubuntu Release.gpg
Ign http://asher256-repository.tuxfamily.org dapper Release
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://my.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://my.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://asher256-repository.tuxfamily.org ubuntu Release
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://my.archive.ubuntu.com dapper Release
Ign http://asher256-repository.tuxfamily.org dapper/main Packages
Ign http://asher256-repository.tuxfamily.org dapper/dupdate Packages
Ign http://asher256-repository.tuxfamily.org dapper/french Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://my.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Ign http://asher256-repository.tuxfamily.org ubuntu/main Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
Ign http://asher256-repository.tuxfamily.org ubuntu/french Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://my.archive.ubuntu.com dapper/main Sources
Hit http://my.archive.ubuntu.com dapper/restricted Sources
Err http://asher256-repository.tuxfamily.org dapper/main Packages
  404 Not Found
Err http://asher256-repository.tuxfamily.org dapper/dupdate Packages
  404 Not Found
Hit http://my.archive.ubuntu.com dapper-updates/main Packages
Hit http://my.archive.ubuntu.com dapper-updates/restricted Packages
Err http://asher256-repository.tuxfamily.org dapper/french Packages
  404 Not Found
Err http://asher256-repository.tuxfamily.org ubuntu/main Packages
  404 Not Found
Err http://asher256-repository.tuxfamily.org ubuntu/dupdate Packages
  404 Not Found
Hit http://my.archive.ubuntu.com dapper-updates/main Sources
Hit http://my.archive.ubuntu.com dapper-updates/restricted Sources
Err http://asher256-repository.tuxfamily.org ubuntu/french Packages
  404 Not Found
Fetched 4B in 3s (1B/s)
Reading package lists... Done
kinson@ubuntu:~$
```

What I added to sources.list:

```
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french
```

Tried "sudo apt-get update" gives the same results as above.

Any help would be appreciated, thanks :)

Kinson

---

### Post by navneeth on 2006-12-14
"update" just updates you repos (I think). You should also use the install command (duh!)

```
sudo apt-get install alltray
``` or ```
sudo aptitude install alltray
```


Look at ayoli's post.

---

### Post by Sukarn on 2006-12-22
> **navneeth said:**
> "update" just updates you repos (I think). You should also use the install command (duh!)

```
sudo apt-get install alltray
``` or ```
sudo aptitude install alltray
```


Look at ayoli's post.

He's not able to fetch the package list. How do you think he can install the package if his package manager does not know it exists?

---

