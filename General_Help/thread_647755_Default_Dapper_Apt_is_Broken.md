---
title: "Default Dapper Apt is Broken"
date: 2007-12-22
forum: General Help
---

### Post by maddog39 on 2007-12-22
Hello all,

Recently I need to reinstall Ubuntu because I was having a bunch of problems with things not working. Well the only way for me to install Ubuntu (or any other distro for that matter) is the use the newest version availible which doesnt use SMP by default (dapper in my case). Then from there I do a manual upgrade to edgy and then use the update manager to upgrade from edgy to feisty and feisty to gutsy, really really irritating but nothing I can do.

Well this time after I install a fresh copy of dapper I start to run the updates but every single package fails to be pulled from the server. So I try and run an update on it:
```

maddog39@desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed [IP: 91.189.88.37 80]
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.88.46 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 91.189.88.46 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://us.archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://us.archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed [IP: 91.189.88.37 80]
Ign http://us.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://us.archive.ubuntu.com dapper-updates/universe Packages
Ign http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Err http://us.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper-updates/universe Packages
  Connection failed [IP: 91.189.88.46 80]
Err http://us.archive.ubuntu.com dapper-updates/multiverse Packages
  Connection failed [IP: 91.189.88.46 80]
Reading package lists... Done

```
Then I try switching mirrors (tried uk, de, and primary mirrors) and they ALL also failed to get anything from the server. I open firefox and I can browse the web just fine, went to a couple websites, google, so forth, they all worked fine. I tried browsing around the ubuntu archive mirrors from FF and that worked fine as well. I then took the IP address that apt reported as having issues and put them into firefox, and I was again able to browse the repo from firefox.

I have searched for like an hour and a half now and found aboslutely nothing on the issue. I have also reinstalled dapper about 5 or 6 times, to try different things, and its failed every single time so far. What the heck is going on? :/

Thanks!
-Alec Hussey

---

