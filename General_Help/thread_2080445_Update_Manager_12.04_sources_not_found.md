---
title: "Update Manager 12.04 sources not found"
date: 2012-11-04
forum: General Help
---

### Post by david1068 on 2012-11-04
Hi all. I'm new to Ubuntu, but everything was going swell until my update manager can't seem to find upadtes. It keeps saying "Failed to download repository information: Check your internet connection."

Here's the details: \\W:Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks in advance :)

---

### Post by claracc on 2012-11-04
When I click on the first of the urls you provide, I obtain:

> Not Found

The requested URL /jonls/redshift-ppa/ubuntu/dists/precise/main/source/Sources was not found on this server.
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80

So the software package is not in this server, you can try to change the server to download updates in software sources or you can disable these ppas you want to download software from.

I have visited the redshift ppa in launchpad and there is not software package for 12.04 precise pangolin, so you cannot use them. You will have to remove them.

---

### Post by ibjsb4 on 2012-11-04
Redshift-ppa hasn't been updated in over a year, looks dead to me.

[https://launchpad.net/~jonls/+archive/redshift-ppa](https://launchpad.net/~jonls/+archive/redshift-ppa)

---

