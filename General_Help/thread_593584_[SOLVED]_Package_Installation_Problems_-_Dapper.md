---
title: "[SOLVED] Package Installation Problems - Dapper"
date: 2007-10-27
forum: General Help
---

### Post by Awayne on 2007-10-27
I'm running Ubuntu Dapper as a server and I am trying to install a package, but it fails to install it, I know the package is in the repos, but it fails to find it. Everything works just the usual sudo apt-get install package, refuses to work. Any help would be greatly appreciated, thanks.

OUTPUT:
> Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release [38.4kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [75.7kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages [20.6kB]
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages [51.4kB]
Get: 10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages [12.2kB]
Get: 11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources [5780B]     
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources [14B] 
Get: 13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources [13.2kB]
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources [2713B]
Get: 15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [9813B]    
Fetched 230kB in 1s (168kB/s)                     
Reading package lists... Done


INSTALL:
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package streamripper


---

### Post by lH)4~mK0e on 2007-10-27
You need to enable the standard "universe" repository in the sources.list file.  Should look like this in the file:

```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

Then:
```
sudo apt-get update
```

You should be all set to install after that.

---

### Post by Awayne on 2007-10-27
That worked wonders, missed 2 commented lines, thank you very much.

---

