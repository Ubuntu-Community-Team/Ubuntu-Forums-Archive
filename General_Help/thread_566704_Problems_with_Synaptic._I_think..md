---
title: "Problems with Synaptic. I think."
date: 2007-10-03
forum: General Help
---

### Post by Ulysses on 2007-10-03
Hello,

I went to Synaptic to download some packages and experiment but it turns out that I may have made a mistake sometime before without even knowing it

Ubuntu 6.06
IBM Thinkpad Pentium III, 733
512mb RAM

And when I go to check things out, I open Synaptic and the following message appears:

E: Dynamic MMap ran out of room
E: Error occurred while processing php4-pgsql (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Whups...What did I do wrong?

Help?

RAR

---

### Post by taurus on 2007-10-03
Close synaptic if you have it open.  Then, post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by meierfra on 2007-10-03
You need to increase you apt-get cache limit:

Open the file /etc/apt/apt.conf via

```
gksudo gedit /etc/apt/apt.conf 
```

Look for the line:

> 
APT::Cache-Limit  "4194304";
(The number might be different)
Change it  to 

> APT::Cache-Limit “16777216”;

That should  solve your problem.
If it doesn't,   try increasing the Cache-Limit even more.

---

### Post by Ulysses on 2007-10-06
Hello,

Tried both suggestions. Thank you for being so patient with me. Systems works, just can't do much with it, But here are the outputs:
Ran
```
sudo apt-get update
```
Got lots of stuff. Some of it reads as errors. Not sure why.
```
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://security.ubuntu.com breezy-security Release.gpg
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:5 http://security.ubuntu.com dapper-security Release [50.9kB]
Hit http://archive.ubuntu.com dapper Release
Ign http://ca.archive.ubuntu.com breezy Release.gpg
Ign http://ca.archive.ubuntu.com breezy-backports Release.gpg
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Ign http://ca.archive.ubuntu.com breezy Release
Ign http://ca.archive.ubuntu.com breezy-backports Release
Ign http://ca.archive.ubuntu.com breezy/main Packages
Ign http://ca.archive.ubuntu.com breezy/restricted Packages
Ign http://ca.archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com dapper/main Packages
Ign http://ca.archive.ubuntu.com breezy/multiverse Packages
Ign http://ca.archive.ubuntu.com breezy/main Sources
Ign http://ca.archive.ubuntu.com breezy/restricted Sources
Ign http://ca.archive.ubuntu.com breezy/universe Sources
Ign http://ca.archive.ubuntu.com breezy/multiverse Sources
Ign http://ca.archive.ubuntu.com breezy-backports/main Packages
Ign http://ca.archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Ign http://ca.archive.ubuntu.com breezy-backports/universe Packages
Ign http://ca.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com breezy-backports/main Sources
Ign http://ca.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://ca.archive.ubuntu.com breezy-backports/universe Sources
Ign http://ca.archive.ubuntu.com breezy-backports/multiverse Sources
Ign http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com dapper/multiverse Packages
Err http://ca.archive.ubuntu.com breezy/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Hit http://ca.archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com breezy-security/main Packages
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://ca.archive.ubuntu.com dapper/multiverse Sources
Err http://ca.archive.ubuntu.com breezy/multiverse Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/main Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/restricted Sources
  404 Not Found [IP: 91.189.89.6 80]
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Err http://ca.archive.ubuntu.com breezy/universe Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/multiverse Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Get:6 http://security.ubuntu.com dapper-security/main Packages [124kB]
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/universe Packages
Hit http://ca.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-updates/universe Sources
Hit http://ca.archive.ubuntu.com dapper-updates/multiverse Sources
Err http://ca.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found [IP: 91.189.89.6 80]
Get:7 http://security.ubuntu.com dapper-security/restricted Packages [7830B]
Get:8 http://security.ubuntu.com dapper-security/universe Packages [74.3kB]
Get:9 http://security.ubuntu.com dapper-security/multiverse Packages [4070B]
Get:10 http://security.ubuntu.com dapper-security/main Sources [24.8kB]
Get:11 http://security.ubuntu.com dapper-security/restricted Sources [979B]
Get:12 http://security.ubuntu.com dapper-security/universe Sources [9690B]
Get:13 http://security.ubuntu.com dapper-security/multiverse Sources [778B]
Err http://security.ubuntu.com breezy-security/main Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/restricted Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/multiverse Packages
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/main Sources
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/restricted Sources
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/universe Sources
  404 Not Found [IP: 91.189.88.37 80]
Err http://security.ubuntu.com breezy-security/multiverse Sources
  404 Not Found [IP: 91.189.88.37 80]
Fetched 298kB in 3s (97.7kB/s)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i38 6/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/restricted/bina ry-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary -i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/bina ry-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sou rces.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/restricted/sour ce/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/universe/source /Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/sour ce/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/ binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr icted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive rse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi verse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/ source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr icted/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive rse/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi verse/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin ary-i386/Packages.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe /binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiver se/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou rce/Sources.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/source/Sources.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe /source/Sources.gz 404 Not Found [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiver se/source/Sources.gz 404 Not Found [IP: 91.189.88.37 80]
```
Then it comes back to me with the error that I mentioned before:
```
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing php4-mysql (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_br eezy-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

Then I followed the second suggestions

Ran 
```
gksudo gedit /etc/apt/apt.conf
```
Terminal read like this before going to the edit screen.
```
(gedit:5145): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```
Got this as an output in the edit screen, which doesn't even touch what it was I was supposed to see:
```
ACQUIRE {http::proxy "http://192.168.1.110:8080/"}
```

Arghhh.... Help. Please?

RAR

---

### Post by meierfra on 2007-10-06
Add  this line to "apt.conf":


> APT::Cache-Limit “16777216”;

---

### Post by Ulysses on 2007-10-06
Hey

Did it.
Saved it.
Tried to run update in terminal

Still getting the following message ; which tells me, I think, that I have the same problem

```
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com breezy Release.gpg
Ign http://ca.archive.ubuntu.com breezy-backports Release.gpg
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://security.ubuntu.com breezy-security Release.gpg
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Ign http://ca.archive.ubuntu.com breezy Release
Ign http://security.ubuntu.com breezy-security Release
Ign http://ca.archive.ubuntu.com breezy-backports Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://ca.archive.ubuntu.com breezy/main Packages
Ign http://ca.archive.ubuntu.com breezy/restricted Packages
Ign http://ca.archive.ubuntu.com breezy/universe Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://ca.archive.ubuntu.com breezy/multiverse Packages
Ign http://ca.archive.ubuntu.com breezy/main Sources
Ign http://ca.archive.ubuntu.com breezy/restricted Sources
Ign http://ca.archive.ubuntu.com breezy/universe Sources
Ign http://ca.archive.ubuntu.com breezy/multiverse Sources
Ign http://ca.archive.ubuntu.com breezy-backports/main Packages
Ign http://ca.archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Ign http://ca.archive.ubuntu.com breezy-backports/universe Packages
Ign http://ca.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com breezy-backports/main Sources
Err http://security.ubuntu.com breezy-security/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Ign http://ca.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://ca.archive.ubuntu.com breezy-backports/universe Sources
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Ign http://ca.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://ca.archive.ubuntu.com breezy/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Err http://ca.archive.ubuntu.com breezy/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Err http://security.ubuntu.com breezy-security/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Hit http://ca.archive.ubuntu.com dapper/universe Sources
Hit http://ca.archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com breezy-security/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com breezy-security/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err http://ca.archive.ubuntu.com breezy/multiverse Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/main Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/restricted Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://security.ubuntu.com breezy-security/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com breezy-security/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com breezy-security/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err http://ca.archive.ubuntu.com breezy/universe Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy/multiverse Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://security.ubuntu.com breezy-security/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/universe Packages
Hit http://ca.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-updates/universe Sources
Hit http://ca.archive.ubuntu.com dapper-updates/multiverse Sources
Err http://ca.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found [IP: 91.189.89.6 80]
Err http://ca.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found [IP: 91.189.89.6 80]
Fetched 4B in 1s (2B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz 404 Not Found [IP: 91.189.89.6 80]
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing php4-mysql (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

Argghhh...Again....Help?

---

### Post by meierfra on 2007-10-06
Well, you could try increasing the  cache limit some more, say


APT::Cache-Limit &#8220;33554432";

---

### Post by rsambuca on 2007-10-06
Your sources list is all mixed up.  You have breezy and dapper repositories in there.

Please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by PmDematagoda on 2007-10-06
Hey, what on earth are Breezy repositories doing in your sources file? 

I assume you have upgraded to dapper? If so then:-

```
sudo gedit /etc/apt/sources.list

```

Deactivate all the repository addresses with a "Breezy" in them by typing # in front of them or just remove all the Breezy addresses and save it and then try again.

One thing that would be causing the problem is that Breezy repos have be taken off since Ubuntu has withdrawn support for it a long time ago.

---

### Post by Ulysses on 2007-10-07
Hello

Uh...Not sure why there are mixed repositories. It could have something to do with me doing something and not keeping notes on it
I seem to recall experimenting with Automatix and then giving up because I couldn't figure it out

I never wanted to upgrade to 7.04. I just played.

BUT....What I did do this morning was backup my laptop completely and start all over again and decide to install 7.04 ; so in a manner of speaking, my problem is solved - but I did it the lazy way.

Now, all I need to do is get the wireless working and I am on my way.

You should completely expect another exasperated post of me not being able to get the wireles to work.

Ubunutu seriously rocks. Windoze is far too boring for me. I would never have this much fun with anything else. Well, except for that other thing ; but both of them I am capable of doing without any clothes on.

Thanks,
RAR

---

