---
title: "Repository Update Problem"
date: 2007-02-17
forum: General Help
---

### Post by nastavirss on 2007-02-17
After i updated my ubuntu 6.06(dapper) kernel to version 2.6.15-28-386 yesterday, i am unable to update the packages in the repository.

I used both synaptic package manager as well as tried sudo apt-get update, but i am getting 

```
Err http://archive.canonical.com dapper-commercial Release.gpg
  Connection failed
Err http://medibuntu.sos-sts.com dapper Release.gpg
  Connection failed [IP: 88.191.42.241 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 195.248.90.38 80]
Ign http://archive.canonical.com dapper-commercial Release
Ign http://security.ubuntu.com dapper-security Release
Ign http://medibuntu.sos-sts.com dapper Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.38 80]
```
this is just a snap shot of the whole corpus of errors that i am getting. 
And this is how my sources.list looks

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main


```

It would be great if anyone could help me with this.

---

### Post by Spin Doctor on 2007-02-17
I belive I had this happening to me once aswell. It seems your etc/apt/sources.list has become corrupted, meaning probably it doesnot follow the formats required for Synaptic to read the list.

What I did to solve the problem was:[LIST]
[*]First backup your etc/apt/sources.list
[*]Go to System mainmeny, Select Administration submeny, and select software sources menyoption.
[*]Uncheck everything you have selected, leaving it as blank as possible.
[*]Restart Synaptic to see if it will load the sources.list[/LIST]If this does not work: open you etc/apt/sources.list.
If you see a format error, go ahead and delete just that. 
If not, delete everything there, and save, leaving it blank. Then google to find a default sources.list and paste into yours. And make extra additions based on if you are running Automatix or any other unsupported repositories.

---

### Post by nastavirss on 2007-02-17
I tried doing that. But still facing the problem.

---

### Post by Ambimom on 2007-02-17
There is definitely something amiss with the repository update....I had a similar issue and after doing a bit of research, I learned that this is not an isolated problem.  Here's how I solved my problem.  Perhaps it will work for you.

[http://www.ubuntuforums.org/showthread.php?t=363244](http://www.ubuntuforums.org/showthread.php?t=363244)


Here's a similar thread:

[http://www.ubuntuforums.org/showthread.php?t=363680](http://www.ubuntuforums.org/showthread.php?t=363680)


Change the http to ftp and see what happens.  I tried editing the source list but that didn't work for me.  I did it manually in Synaptic...worked like a charm.  It is a bug apparently and very annoying.

Good luck!

---

### Post by nastavirss on 2007-02-17
Hey

Changing it to FTP made it work. 

Thanks a lot

---

