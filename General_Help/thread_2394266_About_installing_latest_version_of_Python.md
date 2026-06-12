---
title: "About installing latest version of Python"
date: 2018-06-14
forum: General Help
---

### Post by satimis on 2018-06-14
Hi all,

Ubuntu 16.04 gnome desktop
=======================

Python is default installed on Ubuntu 16.04

&#10219; apt policy python```

python:
  Installed: 2.7.12-1~16.04
  Candidate: 2.7.12-1~16.04
  Version table:
 *** 2.7.12-1~16.04 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.7.11-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

&#10219; python --version```

Python 2.7.12

```

I need to install Python 3.6.0. (the stable version) and found following document;

How to Install Python 3.6.1 in Ubuntu 16.04 LTS
[http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/](http://ubuntuhandbook.org/index.php/2017/07/install-python-3-6-1-in-ubuntu-16-04-lts/)

Does the steps work on Python 3.6.0?

Do I need to wipe out Python 2.7.12?  Is there any problem running Python 3.6.0. on Gnome desktop?  According to the response below the above article there was problem running 3.6.1. on Gnome desktop.

Please advise.  Thanks

Furthermore what is the difference running Anaconda Python Distribution.  I found following document;
How To Install the Anaconda Python Distribution on Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-16-04)

Regards
satimis

---

### Post by Impavidus on 2018-06-15
Both Python 2.7 and Python 3.5 should be installed by default on Ubuntu 16.04. To run the latter, use the command python3. If you really need Python 3.6 you have to jump through some hoops (probably involving a PPA) and hope it all works, or move on to Ubuntu 18.04.

Don't wipe out Python 2.7. Some vital components of Ubuntu 16.04 depend on it.

---

### Post by satimis on 2018-06-15
> **Impavidus said:**
> Both Python 2.7 and Python 3.5 should be installed by default on Ubuntu 16.04. To run the latter, use the command python3. If you really need Python 3.6 you have to jump through some hoops (probably involving a PPA) and hope it all works, or move on to Ubuntu 18.04.

Don't wipe out Python 2.7. Some vital components of Ubuntu 16.04 depend on it.
Hi,

Thanks for your advice.

&#10219; apt policy python3```

python3:
  Installed: 3.5.1-3
  Candidate: 3.5.1-3
  Version table:
 *** 3.5.1-3 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

&#10219; python3 --version```

Python 3.5.2

```

I'm prepared to learn Python programming and need to install following packages;```

python-dev python-numpy python-setuptools python-scipy libatlas-dev libatlas3-base python-matplotlib scikit-learn

```

&#10219; apt policy build-essential python-dev python-numpy \
> python-setuptools python-scipy libatlas-dev libatlas3-base \
> python-matplotlib scikit-learn```

build-essential:
  Installed: 12.1ubuntu2
  Candidate: 12.1ubuntu2
  Version table:
 *** 12.1ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
python-dev:
  Installed: 2.7.12-1~16.04
  Candidate: 2.7.12-1~16.04
  Version table:
 *** 2.7.12-1~16.04 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.7.11-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python-numpy:
  Installed: (none)
  Candidate: 1:1.11.0-1ubuntu1
  Version table:
     1:1.11.0-1ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
python-setuptools:
  Installed: 20.7.0-1
  Candidate: 20.7.0-1
  Version table:
 *** 20.7.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
python-scipy:
  Installed: (none)
  Candidate: 0.17.0-1
  Version table:
     0.17.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libatlas-dev:
  Installed: (none)
  Candidate: 3.10.2-9
  Version table:
     3.10.2-9 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libatlas3-base:
  Installed: (none)
  Candidate: 3.10.2-9
  Version table:
     3.10.2-9 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
python-matplotlib:
  Installed: (none)
  Candidate: 1.5.1-1ubuntu1
  Version table:
     1.5.1-1ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
N: Unable to locate package scikit-learn

```

I suppose I need to install scikit-learn running pip or easy_install

&#10219; apt policy python-pip```

python-pip:
  Installed: 8.1.1-2ubuntu0.4
  Candidate: 8.1.1-2ubuntu0.4
  Version table:
 *** 8.1.1-2ubuntu0.4 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     8.1.1-2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```

&#10219; pip -V```

pip 8.1.1 from /usr/lib/python2.7/dist-packages (python 2.7)

```

&#10219; which pip```

/usr/bin/pip

```

&#10219; easy_install --version```

setuptools 20.7.0 from /usr/lib/python2.7/dist-packages (Python 2.7)

```

&#10219; which easy_install```

/usr/bin/easy_install

```

I'm still curious to learn what will be the advantage using "Anaconda Python Distribution" ?

Regards
satimis

---

### Post by oldfred on 2018-06-16
If running python3, you need to be sure to install the python3 python packages.
I often installed a package and found I only had the python2 version.

I use pip3 or synaptic which shows all the python & python3 packages. Some claim pip works better but you have to know detailed package name. So I use synaptic.

But I found this in my notes:
use get-pip.py instead of sudo apt install python3-pip which is outdated

[https://packaging.python.org/guides/tool-recommendations/](https://packaging.python.org/guides/tool-recommendations/)

---

