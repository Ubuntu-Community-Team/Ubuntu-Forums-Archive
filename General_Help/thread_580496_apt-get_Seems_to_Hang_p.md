---
title: "apt-get Seems to Hang p"
date: 2007-10-18
forum: General Help
---

### Post by TheMatt on 2007-10-18
Hi,

For some odd reason when I went to install some debs today, apt get hung up. At first hung up at the archive.ubuntu.com repos, and then hung up at retrieving headers. I commented out the archive.ubuntu.com repos but it still hangs up at retrieving headers.

This is with the archive.ubuntu.com repos enabled.
```
mattmodica@Dothan:~$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:2 http://packages.medibuntu.org dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://packages.medibuntu.org dapper Release
Ign http://packages.medibuntu.org dapper/free Packages
Ign http://packages.medibuntu.org dapper/non-free Packages
Hit http://packages.medibuntu.org dapper/free Packages
Hit http://packages.medibuntu.org dapper/non-free Packages
Get:4 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:6 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Fetched 6B in 4m3s (0B/s)
Reading package lists... Done
mattmodica@Dothan:~$     
```

Is there some other log I should look at and post?

Thanks. :)

---

### Post by mrvertigo on 2007-10-18
this could very well be related to repo server load and not your system at all, just my two cents

---

### Post by m0eman on 2007-10-18
> **mrvertigo said:**
> this could very well be related to repo server load and not your system at all, just my two cents

Agreed, this morning, I couldn't even reach the update server. Mad rush to get gutsy this morning.

---

### Post by mrvertigo on 2007-10-18
yah, i just checked and my dl speeds even stalled downloading blender...... there swamped!

---

### Post by m0eman on 2007-10-18
I just read somewhere, try this: (it worked for me)
system->administration->software sources
ubuntu software tab->download from-> other->select best server

---

