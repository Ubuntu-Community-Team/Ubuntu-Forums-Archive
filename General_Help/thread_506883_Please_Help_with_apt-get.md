---
title: "Please Help with apt-get"
date: 2007-07-22
forum: General Help
---

### Post by netvampire on 2007-07-22
Hello,
I am trying to run the command 'sudo apt-get update'. The reason I am doing this is because i tried to do 'sudo apt-get install tightvncserver' and it said to run apt-get update first. 

When I run 'sudo apt-get update' i get the following message:

```


Err http://ca.archive.ubuntu.com feisty Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/main Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA
Err http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Ign http://ca.archive.ubuntu.com feisty Release
Ign http://ca.archive.ubuntu.com feisty-updates Release
Ign http://ca.archive.ubuntu.com feisty/main Packages
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com feisty-security/universe Translation-en_CA
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/restricted Packages
Ign http://ca.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security Release
Ign http://ca.archive.ubuntu.com feisty/restricted Sources
Ign http://ca.archive.ubuntu.com feisty/universe Packages
Ign http://ca.archive.ubuntu.com feisty/universe Sources
Ign http://ca.archive.ubuntu.com feisty/multiverse Packages
Ign http://ca.archive.ubuntu.com feisty/multiverse Sources
Ign http://ca.archive.ubuntu.com feisty-updates/main Packages
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://ca.archive.ubuntu.com feisty-updates/main Sources
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Err http://ca.archive.ubuntu.com feisty/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/universe Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Err http://ca.archive.ubuntu.com feisty/multiverse Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty/multiverse Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Err http://ca.archive.ubuntu.com feisty-updates/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Err http://ca.archive.ubuntu.com feisty-updates/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Fetched 1B in 0s (1B/s)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-amd64/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (113 No route to host)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
mohit@kismet:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package update



```



What could be causing the problem. Any help is appreciated. And keep in mind I am a kubuntu newb. Thanks.

---

### Post by benx009 on 2007-07-22
um, are you sure your internet connection is up? can you browse the internet w/ konqueror?  don't forget you don't do "*sudo apt-get install update*" (like you did the second time), just "*sudo apt-get update*"

---

### Post by netvampire on 2007-07-22
Wow thanks for the fast response.
The internet is definately running as I can post to this forum.

When I tried the command you suggested 'sudo apt-get install update' all I get is this:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package update



```


Any more ideas?

---

### Post by odiseo77 on 2007-07-22
That's because there's no package named 'update'; as benx009 told you, you don't do 'apt-get install update'... you can execute:

```
apt-get update
```
(to update the list of packages available in the repos), or:

```
apt-get install <package_name>
```
(to install a certain package).

I'd suggest you to read [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/) for further information :)

---

### Post by bodhi.zazen on 2007-07-22
Are you behind a proxy ?

---

