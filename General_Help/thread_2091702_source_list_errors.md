---
title: "source list errors"
date: 2012-12-05
forum: General Help
---

### Post by kend650 on 2012-12-05
I just installed 12.10 and I'm looking at Tweak's Source Editor.  It is showing multiple, but not all, *-precise.list in the left column and the correct deb *quantal main in the right column.  Is there a way to automatically update the left column to show the proper quantal name, or is this strictly a cosmetic error?

Here is a partial detailed output of backend_helper.py:

W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-amd64/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-amd64/Packages)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/binary-i386/Packages)  Unable to connect to archive.getdeb.net:http:
, W:Failed to fetch [http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en](http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/apps/i18n/Translation-en)  Unable to connect to archive.getdeb.net:http:

---

### Post by oldfred on 2012-12-05
Is this the tweak you are using?

       A easy way to remove the amount of kernels is to install Ubuntu tweak:**Phased out Oct 2012**
[http://ubuntu-tweak.com/gksud](http://ubuntu-tweak.com/gksud)

---

### Post by kend650 on 2012-12-05
The first paragraph is from Ubuntu Tweak 0.8.2 which came pre-installed with the 12.10 upgrade.  

The second part comes from a indicator app 'backend_helper.py' that gives those 'failed to fetch' errors for multiple packages.

Thanks

---

