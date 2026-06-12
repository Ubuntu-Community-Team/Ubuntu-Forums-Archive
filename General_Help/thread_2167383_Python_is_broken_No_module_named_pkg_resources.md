---
title: "Python is broken: No module named pkg_resources"
date: 2013-08-13
forum: General Help
---

### Post by nergar2 on 2013-08-13
Hello!

It has been a while since I used this forum for support but I am stuck.

My setup:

```
daniel@nergar:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

```

I woke up today and felt a need to upgrade my seedbox, all went fine so I went ahead and updated my flexget installation with the command:

```
sudo pip install --upgrade flexget
```

The command completed successfully, but immediately after pip stopped working:

```
daniel@nergar:~$ pip
Traceback (most recent call last):
  File "/usr/bin/pip", line 5, in <module>
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources

```

Now flexget is also broken and this is the error message I'm getting:

```
daniel@nergar:~$ flexget
Traceback (most recent call last):
  File "/usr/local/bin/flexget", line 7, in <module>
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources

```

I have checked and I have python-pkg-resources installed:

```
daniel@nergar:~$ sudo find / -name 'pkg_resources.*'
/usr/share/doc/python-pkg-resources/pkg_resources.txt.gz
/usr/lib/python2.7/dist-packages/pkg_resources.py

```

But for some reason python can't find it, I tried setting the PYTHONHOME and PYTHONPATH variables without any luck, also I tried modifying the flexget script:

[PHP]#!/usr/bin/python
# EASY-INSTALL-ENTRY-SCRIPT: 'FlexGet==1.1','console_scripts','flexget'
__requires__ = 'FlexGet==1.1'
import sys
sys.path.append("/usr/lib/python2.7/dist-packages/")

from pkg_resources import load_entry_point

if __name__ == '__main__':
    sys.exit(
        load_entry_point('FlexGet==1.1', 'console_scripts', 'flexget')()
    )

[/PHP]

I don't understand why python can't find anything. I also installed python-setuptools but easy_install is not working

```
daniel@nergar:~$ sudo aptitude install python-setuptools
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

daniel@nergar:~$ easy_install
-bash: easy_install: command not found

```

Does anyone knows how to fix python in my system? I don't want to reinstall the OS because it will cost me money with my provider.

---

### Post by Nergar on 2013-08-18
Anyone?? Please!!

---

### Post by y-rebattu on 2013-08-23
hello, i just ran into the same error, here is what i've done to fix it:

apt-get remove --purge python-pkg-resources

apt-get install ubuntu-desktop


i think you don't run ubuntu desktop so just reinstall the bunch of packages that where uninstalled by the removal of python-pkg-resources.

PS: you can try dpkg-reconfigure python-pkg-resources but it didn't worked for me.

---

### Post by Nergar on 2013-08-23
That did the trick!!! thanks a lot!

---

### Post by alexander-g-moore1 on 2013-10-28
> **y-rebattu said:**
> hello, i just ran into the same error, here is what i've done to fix it:

apt-get remove --purge python-pkg-resources

apt-get install ubuntu-desktop


i think you don't run ubuntu desktop so just reinstall the bunch of packages that where uninstalled by the removal of python-pkg-resources.

PS: you can try dpkg-reconfigure python-pkg-resources but it didn't worked for me.

The issue with this is usually that there is something mis-configured or a package missing. I have had the same type of issue and the first step is to make sure that the python tools are working correctly. 

To fix the issue, run the setup script for setuptools:
```
curl https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py | sudo python
```

---

### Post by David_Pecot on 2013-10-28
Thanks ... helps a lot. DP

---

### Post by hopem on 2014-03-06
This should work just fine (it did for me):

sudo apt-get install --reinstall python-pkg-resources

---

### Post by brianfinley on 2014-06-07
> **hopem said:**
> This should work just fine (it did for me):

sudo apt-get install --reinstall python-pkg-resources

Thanks for the thread, guys.  That got me half-way there.  Here's the full command that got it all working again for me:

```
sudo apt-get install python-pkg-resources python-setuptools --reinstall
```

---

