---
title: "can't download repository index"
date: 2008-02-12
forum: General Help
---

### Post by rainpaw on 2008-02-12
Hi, thanks in advance for looking at my query: 

I have downloaded xubuntu 6.06 and I'm using Telus high speed enhanced as network provider but when I try to reload changes in repositories this always appears: could not download all repository index  

 [http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
[http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out
[http://packages.medibuntu.org/dists/dapper/Release:](http://packages.medibuntu.org/dists/dapper/Release:) Unable to find expected entry  drake/binary-i386/Packages in Meta-index file (malformed Release file?)

Sometimes, I repeat the process and items with connection timed out disappears but the last one (malformed release file) doesn't
 thanks again, rain

---

### Post by erginemr on 2008-02-12
Hi there,

Are you able to connect to internet via Firefox? If so, you can try connecting to other repository servers via Synaptic settings. please check out the last post in:

[http://ubuntuforums.org/showthread.php?t=618985](http://ubuntuforums.org/showthread.php?t=618985)

---

### Post by zvacet on 2008-02-12
System>administration>software sources>change server to main.

---

