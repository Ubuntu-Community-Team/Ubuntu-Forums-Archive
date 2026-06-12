---
title: "Error installing R: Unable to locate package R"
date: 2014-07-29
forum: General Help
---

### Post by dadrivr on 2014-07-29
[COLOR=#000000]To preface, I am fairly new to Linux.  I'm trying to install R [/COLOR][COLOR=#000000]on a Linux Server (Ubuntu 12.10, Quantal Quetzal).  When I try to install R ([/COLOR][FONT=courier new]su -c 'apt-get install R R-core R-core-devel R-devel'[/FONT][COLOR=#000000]), I receive the following error:
[/COLOR]
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package R
E: Unable to locate package R-core
E: Unable to locate package R-core-devel
E: Unable to locate package R-devel

```

[COLOR=#000000][FONT=Arial]I've tried running [/FONT][/COLOR][FONT=courier new]apt-get update[/FONT] [COLOR=#000000][FONT=Arial]but that didn't allow me to install R either.  [/FONT][/COLOR]Here's my sources.list file:


```
deb http://archive.ubuntu.com/ubuntu quantal main
deb http://archive.ubuntu.com/ubuntu quantal-updates main
deb http://security.ubuntu.com/ubuntu quantal-security main
deb http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe


deb http://cran.rstudio.com/bin/linux/ubuntu quantal/
deb-src http://cran.rstudio.com/bin/linux/ubuntu quantal/
deb http://cran.rstudio.com/bin/linux/ubuntu raring/
deb-src http://cran.rstudio.com/bin/linux/ubuntu raring/

```

Thanks in advance!

---

### Post by mooreted on 2014-07-29
I have never tried su -c for this. Did you try sudo apt-get install <packagename>?

Also, have you tried different mirrors? Maybe that one has issues.

---

### Post by steeldriver on 2014-07-29
2 things:

First, package names are case sensitive - afaik the Ubuntu packages are all lower case i.e. r-base, r-base-dev and so on

Second, Ubuntu 12.10 is now beyond EOL and it looks like the Quantal packages have already been removed from the cran repositories:  [http://cran.rstudio.com/](http://cran.rstudio.com/)

---

### Post by dadrivr on 2014-07-29
Tried [COLOR=#000000]sudo apt-get install r [/COLOR](lower case r) but same error.  Is there any way to install the latest version of R without upgrading Ubuntu?  Or is upgrading my only/best option?

---

### Post by ian-weisser on 2014-07-30
> **dadrivr said:**
> Tried [COLOR=#000000]sudo apt-get install r [/COLOR](lower case r) but same error.
Of course. Changing the command will not cause the files withdrawn from the server to magically reappear.


> **dadrivr said:**
> Is there any way to install the latest version of R without upgrading Ubuntu?  Or is upgrading my only/best option?

Using a past-end-of-life version of Ubuntu is unwise. You do not receive any security updates. Your system may now be vulnerable to published exploits. You do not receive application updates. And, of course, you will not receive much real support in this forum.

I would say that backing up your data and installing 14.04 is your best option if you wish to receive updated applications (like R). You can no longer use the upgrade path from 12.10 - the subsequent versions of Ubuntu (13.04 and 13.10) have also already closed.

---

