---
title: "Problems when updated to 8.04 LTS! &amp; resolution problem!"
date: 2008-04-20
forum: General Help
---

### Post by n0kS on 2008-04-20
***EDIT: I SOLVED THE RESOLUTION PROBLEM!***
Hello people, I've just upgraded from Ubuntu 7.10 to 8.04 LTS and here's the problem
```
n0ks@phr33d0m:~$ update-manager
current dist not found in meta-release file
```
and....
```
n0ks@phr33d0m:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy
```

When I try to update my sources' database I get this one....
```
n0ks@phr33d0m:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://es.archive.ubuntu.com hardy Release.gpg
Ign http://es.archive.ubuntu.com hardy/main Translation-en_US
Ign http://es.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://es.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://es.archive.ubuntu.com hardy/multiverse Translation-en_US
............
............
```
Ign = Ignored ?! 

I got something similar 1h ago with the Update Manager... it appeared me some error with the above, that couldn't get the source list from those repositories...
Now the Update Manager's error seems to be solved, somehow.... (the error doesn't appear) but I have the same thing with the Ign in the console....

Thanks in advance!

---

### Post by trippinnik on 2008-04-20
edit your /etc/apt/source.list and take our the '#' before repos you want to enable.

---

