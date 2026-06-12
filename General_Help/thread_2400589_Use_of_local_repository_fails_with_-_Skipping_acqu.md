---
title: "Use of local repository fails with - Skipping acquire of configured file ‘Packages’"
date: 2018-09-07
forum: General Help
---

### Post by pavibhai on 2018-09-07
Hi,


 I am new to Ubuntu and when I came across the point of trying to  install OpenJDK 7 I thought I will try the approach of a local  repository.
 From that I have done the following:
Used this as the starting point - [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)
But this was incomplete and gave me errors about Release file and signing so I went ahead with the following steps:
 
[LIST=1]
[*] Created a GPG Key 
[*] Done the following in terms of setup
```
sudo apt-get install dpkg-dev
sudo mkdir -p /usr/local/mydebs
``` 
[*] Created a program for updating my repo
```
mkdir ~/bin
echo '#! /bin/bash
cd /usr/local/mydebs
apt-ftparchive packages /usr/local/mydebs | gzip -9c > Packages.gz
apt-ftparchive release /usr/local/mydebs > /usr/local/mydebs/Release
gpg --digest-algo SHA256 --armor --output Release.gpg --detach-sign Release
gpg --digest-algo SHA256 --clearsign --output InRelease Release
’ > ~/bin/update-mydebs
``` 
[*] Ran the program to create the Packages.gz, Release, Release.gpg and  InRelease files, the listing of the directory looks like this 
[/LIST]
[INDENT] > 4096 Sep  4 16:56 ../
1710 Sep  7 06:28 InRelease
16171552 Sep  4 16:52 openjdk-7-jdk_7u161-2.6.12-1_amd64.deb
709 Sep  7 06:21 Packages.gz
828 Sep  7 06:21 Release
833 Sep  7 06:27 Release.gpg
 [/INDENT]

[LIST=1]
[*]Added the line deb file:/usr/local/mydebs ./ to the /etc/apt/sources.list 
[*]When I perform sudo apt update I get the following error: 
[/LIST]
[INDENT] W: Skipping acquire of configured file ‘Packages’ as repository ‘file:/usr/local/mydebs ./ InRelease’ does not seem to provide it (sources.list entry misspelt?)
 [/INDENT]
Please advice.

---

### Post by pavibhai on 2018-09-08
I now have it working with a change.

I put an uncompressed Packages file so the script now becomes
```
echo '#! /bin/bash
cd /usr/local/mydebs
apt-ftparchive packages /usr/local/mydebs > Packages
apt-ftparchive release /usr/local/mydebs > /usr/local/mydebs/Release
gpg --digest-algo SHA256 --armor --output Release.gpg --detach-sign Release
gpg --digest-algo SHA256 --clearsign --output InRelease Release
’ > ~/bin/update-mydebs
```

After this change it started to work. Not sure if there is a means to indicate that it should look for Packages.gz instead of Packages file.

---

