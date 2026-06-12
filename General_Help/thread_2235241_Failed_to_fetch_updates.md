---
title: "Failed to fetch updates"
date: 2014-07-19
forum: General Help
---

### Post by anon3140 on 2014-07-19
When I try to update my system, I get multiple 404 errors. I am running Lubuntu 13.04 64-bit.

```
administrator@administrator:~$ sudo apt-get update
[sudo] password for administrator: 
Ign http://extras.ubuntu.com raring Release.gpg
Hit http://ppa.launchpad.net raring Release.gpg
Ign http://archive.ubuntu.com raring Release.gpg
Ign http://extras.ubuntu.com raring Release    
Hit http://ppa.launchpad.net raring Release    
Ign http://archive.ubuntu.com raring-updates Release.gpg              
Hit http://ppa.launchpad.net raring/main amd64 Packages
Ign http://archive.ubuntu.com raring-backports Release.gpg
Hit http://ppa.launchpad.net raring/main i386 Packages
Ign http://archive.ubuntu.com raring-security Release.gpg
Ign http://archive.ubuntu.com raring Release                         
Ign http://archive.ubuntu.com raring-updates Release                 
Ign http://archive.ubuntu.com raring-backports Release
Ign http://archive.ubuntu.com raring-security Release
Ign http://ppa.launchpad.net raring/main Translation-en_GB           
Ign http://archive.ubuntu.com raring/main amd64 Packages/DiffIndex   
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://archive.ubuntu.com raring/restricted amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com raring/universe amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com raring/multiverse amd64 Packages/DiffIndex
Err http://extras.ubuntu.com raring/main Sources
  404  Not Found
Err http://extras.ubuntu.com raring/main amd64 Packages
  404  Not Found
Err http://extras.ubuntu.com raring/main i386 Packages
  404  Not Found
Ign http://extras.ubuntu.com raring/main Translation-en_GB
Ign http://extras.ubuntu.com raring/main Translation-en
Err http://archive.ubuntu.com raring/main Sources              
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/restricted Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/universe Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/multiverse Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Ign http://archive.ubuntu.com raring/main Translation-en_GB
Ign http://archive.ubuntu.com raring/main Translation-en
Ign http://archive.ubuntu.com raring/multiverse Translation-en_GB
Ign http://archive.ubuntu.com raring/multiverse Translation-en
Ign http://archive.ubuntu.com raring/restricted Translation-en_GB
Ign http://archive.ubuntu.com raring/restricted Translation-en
Ign http://archive.ubuntu.com raring/universe Translation-en_GB
Ign http://archive.ubuntu.com raring/universe Translation-en
Err http://archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Ign http://archive.ubuntu.com raring-updates/main Translation-en_GB
Ign http://archive.ubuntu.com raring-updates/main Translation-en
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_GB
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com raring-updates/universe Translation-en
Err http://archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Ign http://archive.ubuntu.com raring-backports/main Translation-en_GB
Ign http://archive.ubuntu.com raring-backports/main Translation-en
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_GB
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com raring-backports/universe Translation-en
Err http://archive.ubuntu.com raring-security/main Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/restricted Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/universe Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/multiverse Sources
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/universe i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring-security/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Ign http://archive.ubuntu.com raring-security/main Translation-en_GB
Ign http://archive.ubuntu.com raring-security/main Translation-en
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_GB
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_GB
Ign http://archive.ubuntu.com raring-security/restricted Translation-en
Ign http://archive.ubuntu.com raring-security/universe Translation-en_GB
Ign http://archive.ubuntu.com raring-security/universe Translation-en
Err http://archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/restricted amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/universe amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/multiverse amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages  404  Not Found [IP: 2001:67c:1360:8c01::18 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I also have problems installing new software. It says that I have held broken packages.

```
administrator@administrator:~$ sudo apt-get install --no-install-recommends wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

However, I only have three held packages.

```
administrator@administrator:~$ dpkg --get-selections | grep hold
gimp                        hold
gimp-data                    hold
libgimp2.0                    hold
```

As far as I know, they are not broken. Gimp works fine. Regardless, I tried unholding them to see if it resolved the issue, but it did not. Even with no held packages, I was told that I have held broken packages and therefore cannot install new packages.

I also get an authentication error for some packages. I don't know if it is related.

```
administrator@administrator:~$ sudo apt-get install --no-install-recommends dconf-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  dconf-tools
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 116 kB of archives.
After this operation, 561 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  dconf-tools
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated
```

How can I fix this? Thanks.

---

### Post by Rex Bouwense on 2014-07-19
The fact that Lubuntu 13.04 has reached its End Of Life and is no longer supported may have something to do with your problems.  Recommend that you download and install Lubuntu 14.04 which is the only Lubuntu version that is currently supported.

---

### Post by Dennis N on 2014-07-19
Rex is correct. The repositories are no longer available.

> The 404 or Not Found error message is a HTTP standard response code indicating that the client was able to communicate with a given server, but the server could not find what was requested.

The web site hosting server will typically generate a "404 Not Found" web page when a user attempts to follow a broken or dead link; hence the 404 error is one of the most recognizable errors users can find on the web. (Wikipedia)

Time to upgrade.

---

### Post by anon3140 on 2014-07-20
Alright, thanks.

---

