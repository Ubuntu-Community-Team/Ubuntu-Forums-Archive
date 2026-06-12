---
title: "Failed to fetch http://ca.archive.ubuntu.com"
date: 2008-06-08
forum: General Help
---

### Post by spliffeh on 2008-06-08
I'm a noob trying to learn how to compile stuff

I'm typing:
> 
sudo apt-get install build-essential


I'm getting:
>  -snip-

Install these packages without verification [y/N]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main m4 1.4.10-0ubuntu2
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main autoconf 2.61-4
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main autotools-dev 20070306.1
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main automake 1:1.10+nogfdl-1
  404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.10-0ubuntu2_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/m/m4/m4_1.4.10-0ubuntu2_amd64.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/autoconf/autoconf_2.61-4_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/autoconf/autoconf_2.61-4_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/autotools-dev/autotools-dev_20070306.1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/autotools-dev/autotools-dev_20070306.1_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/a/automake1.10/automake_1.10+nogfdl-1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/a/automake1.10/automake_1.10+nogfdl-1_all.deb) 404 Not Found
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
root@linuxbox:/home/dennis# man apt-get


I assume the "CA" server is down. How do I make apt-get use another server?

---

### Post by spliffeh on 2008-06-08
_Nevermind_ I changed it in the "Synaptic Package Manager"

---

### Post by drs305 on 2008-06-08
> **spliffeh said:**
> 
I assume the "CA" server is down. How do I make apt-get use another server?

In synaptic, try Settings > Repositories, Download from: > Other, Select Best Server. Choose Server, Close. After doing this try running your commands again.

---

