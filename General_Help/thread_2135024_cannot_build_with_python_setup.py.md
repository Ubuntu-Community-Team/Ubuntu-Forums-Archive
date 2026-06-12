---
title: "cannot build with python setup.py"
date: 2013-04-12
forum: General Help
---

### Post by gamblor01 on 2013-04-12
Hi folks,

I'm trying to build this lockbox application so I can evaluate it (storing important documents like tax returns and such):
[https://launchpad.net/lockbox](https://launchpad.net/lockbox)


Unfortunately I don't see any binary files for it so I have to build from source and I am completely clueless how to do so.  There is a setup.py file in there which I ran, and it initially complained:

```

$ ./setup.py 
To build lockbox you need https://launchpad.net/python-distutils-extra

```


No problem, a quick "sudo apt-get install python-distutils-extra" fixed that problem.  Now when I run the setup.py file I get this:

```

$ ./setup.py 
ERROR: Python module gpgme not found
ERROR: Python module MessageBox not found
ERROR: Python module diskctl not found
ERROR: Python module MessageBox not found
ERROR: Python module gpgme not found
ERROR: Python module diskctl not found
ERROR: Python module MessageBox not found
ERROR: Python module diskctl not found
ERROR: Python module MessageBox not found

```


I have tried searching those messages on google without any luck.  I eventually found something called easy_install and set that up but whenever I try something like "sudo easy_install gpgme" it fails to find anything.  Any idea how I get this gpgme, MessageBox, and diskctl stuff installed?

---

### Post by gnuyoga on 2013-04-13
apt-get install python-distutils-extra

and then try python ./setup.py

---

### Post by 3rdalbum on 2013-04-13
Lockbox PPA: [https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa](https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa)

---

### Post by gamblor01 on 2013-04-13
> **gnuyoga said:**
> apt-get install python-distutils-extra

and then try python ./setup.py

Thanks but please see my original post.  I already did this.


> **3rdalbum said:**
> Lockbox PPA: [https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa](https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa)

This was actually how I initially attempted to install but it doesn't work because the packages are only built for precise and not quantal.  Adding the PPA works fine but when I try to run sudo apt-get update I get this:

```

Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Fetched 1,112 kB in 16s (67.6 kB/s)
W: Failed to fetch http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/fabio-massaioli/lockbox-ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```




Thus, I decided to try and build this from source.  So I still need to figure out how to get these python packages installed.  Honestly it's not just for this project -- it's probably a useful thing to know in general how to get software to build with python...

---

### Post by gamblor01 on 2013-04-13
Ok so was able to get this installed.  I wound up downloading the .deb file directly:

[https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa/+packages](https://launchpad.net/~fabio-massaioli/+archive/lockbox-ppa/+packages)


I tried to install it with dpkg -i and it failed stating that it depends on python-gpgme which is not installed.  So I ran "sudo apt-get install python-gpgme" and then lockbox automatically configured itself as well and is working.

I guess I'll mark this as solved but with more and more things built with python, knowing how to satisfy build dependencies will come in handy.  So far the following is all I know from this case:

```

sudo apt-get install python-distutils-extra python-gpgme

```

---

