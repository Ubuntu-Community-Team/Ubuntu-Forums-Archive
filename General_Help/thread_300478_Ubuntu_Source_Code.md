---
title: "Ubuntu Source Code ?"
date: 2006-11-15
forum: General Help
---

### Post by jessewryan on 2006-11-15
I was just wondering if the Ubuntu version 6.06 LTS for pc CD has the source code for ubuntu on it or if it has to be downloaded. And if it does have to be downloaded where might it be located. GREAT DISTRO BY THE WAY ! LOVIN IT.

Thanks.

---

### Post by DaveBorealis on 2006-11-15
6.06's source is right here:
[http://archive.ubuntu.com/ubuntu/dists/dapper/]("http://archive.ubuntu.com/ubuntu/dists/dapper/")

It does have to be downloaded.

Dave

---

### Post by jessewryan on 2006-11-15
Thank you for the reply you pointed me in the right direction. Im still unsure on which exact file to download, the sizes have thrown me off i thought the source code would be at least 100MB so if you could let me know a little more it would be greatly appreciated. Sorry for any inconvience but im on DIALUP so I must choose my downloads wisely because they are bound to take hours haha. Thanks.

---

### Post by hearnden on 2006-11-15
Have a look in the man page for apt-get about obtaining source packages.

```

$ man apt-get

```

If you want the source-code for a particular package (e.g. wget) you can just type
```

$ sudo apt-get --download-only source wget

```

---

### Post by DaveBorealis on 2006-11-15
> **jessewryan said:**
> i thought the source code would be at least 100MB

I didn't notice the file sizes.  The 'Contents-i386.gz' file of 9.7 MB is a text file listing of all files in all packages.  Here's the first couple lines of it:
> This file maps each file available in the Ubuntu Linux system to
the package from which it originates.  It includes packages from the
DIST distribution for the ARCH architecture.


I though Ubuntu had a repository of all source code, and I thought I knew where it was.  Sorry.

So anyone reading this know if Ubuntu really does keep such a repository?

Dave

---

### Post by towsonu2003 on 2006-11-15
> **DaveBorealis said:**
> 
So anyone reading this know if Ubuntu really does keep such a repository?

seems like you got a little bad link ;) you can search for the packages here and download their sources, as well as the patches ubuntu applies to them: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  After choosing "dapper" from the drop down menu and finding the package, see where it says "More Information on" section at he end of the package's web page.

additional link (no need to see, posting as reference to DaveBorealis' link): [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

---

### Post by jessewryan on 2006-11-16
Thanks again to everyone for the replies. This forum is great and you all are appreciated. Thanks again and keep up the good work.

---

