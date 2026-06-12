---
title: "dpkg errors while upgrading"
date: 2015-04-20
forum: General Help
---

### Post by hypnuntu on 2015-04-20
Hello,

this may be a duplicate question, but I've tried all the solutions related to this problem with no result.

Ubuntu 14.10 x64.

When I:

```
sudo apt-get update && apt-get upgrade
```

I always get this:

```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]

```

Of course, Yes; then:

```

Setting up update-notifier-common (3.157) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 24, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 58, in <module>
    import six
ImportError: No module named six
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-installer:
 flashplugin-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.


dpkg: error processing package flashplugin-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 3.157); however:
  Package update-notifier-common is not configured yet.


dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-notifier; however:
  Package update-notifier is not configured yet.


dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                              No apport report written because the error message indicates its a followup error from a previous failure.
                           No apport report written because MaxReports is reached already
                                                                                         No apport report written because MaxReports is reached already
                                                                                                                                                       ader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.


dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 update-notifier-common
 flashplugin-installer
 update-notifier
 update-manager
 ubuntu-release-upgrader-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've tried all the suggestions found on this forum and on the web, but the problem persists.
Any tips?

Thanks

---

### Post by matt_symes on 2015-04-20
Hi

> ImportError: No module named six

Do you have the python module 'six' installed ? I think this is the required module.

From the terminal, post back the results of these commands.

```
apt-cache policy python-six
```

and 

```
dpkg -l python-six
```

**EDIT:**

Seems like it may be the required package.

```
dpkg -L python-six
/.
/usr
/usr/lib
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/six-1.5.2.egg-info
/usr/lib/python2.7/dist-packages/six.py
/usr/share
/usr/share/doc
/usr/share/doc/python-six
/usr/share/doc/python-six/copyright
/usr/share/doc/python-six/changelog.Debian.gz
```

Kind regards

---

### Post by hypnuntu on 2015-04-20
Nothing, always the same error massage;

```
apt-cache policy python-six
```

```

python-six:  Installed: 1.7.3-2
  Candidate: 1.7.3-2
  Version table:
 *** 1.7.3-2 0
        500 http://archive.ubuntu.com/ubuntu/ utopic/main amd64 Packages
        100 /var/lib/dpkg/status

```

And

```
dpkg -l python-six
```

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
ii  python-six

```

---

```

dpkg -L python-six
/.
/usr
/usr/lib
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/six.py
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/top_level.txt
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/dependency_links.txt
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/PKG-INFO
/usr/share
/usr/share/doc
/usr/share/doc/python-six
/usr/share/doc/python-six/changelog.Debian.gz
/usr/share/doc/python-six/copyright

```

The problem persists.

---

### Post by matt_symes on 2015-04-20
Hi

What do these commands return ?

```
python -c 'import sys; print sys.path'
```

and

```
while read f; do file "$f"; done < <(dpkg -L python-six);
```

Kind regards

---

### Post by hypnuntu on 2015-04-21
Hi,

```
python -c 'import sys; print sys.path'
```

returns:

```

['', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PILcompat', '/usr/lib/python2.7/dist-packages/gst-0.10', '/usr/lib/python2.7/dist-packages/gtk-2.0', '/usr/lib/pymodules/python2.7', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client']

```

and

```
while read f; do file "$f"; done < <(dpkg -L python-six);
```

returns this:

```

/.: directory
/usr: directory
/usr/lib: directory
/usr/lib/python2.7: directory
/usr/lib/python2.7/dist-packages: directory
/usr/lib/python2.7/dist-packages/six.py: cannot open `/usr/lib/python2.7/dist-packages/six.py' (No such file or directory)
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info: cannot open `/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info' (No such file or directory)
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/top_level.txt: cannot open `/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/top_level.txt' (No such file or directory)
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/dependency_links.txt: cannot open `/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/dependency_links.txt' (No such file or directory)
/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/PKG-INFO: cannot open `/usr/lib/python2.7/dist-packages/six-1.7.3.egg-info/PKG-INFO' (No such file or directory)
/usr/share: directory
/usr/share/doc: directory
/usr/share/doc/python-six: directory
/usr/share/doc/python-six/changelog.Debian.gz: gzip compressed data, max compression, from Unix
/usr/share/doc/python-six/copyright: ASCII text

```

Thanks

---

### Post by hypnuntu on 2015-04-21
Solved.

Just removed and re-installed [FONT=courier new]python-six[/FONT]. In fact:

```
while read f; do file "$f"; done < <(dpkg -L python-six);
```

showed me that its files were not present. Then, I used Synaptic to install:

[FONT=courier new]update-notifier-common
flashplugin-installer
update-notifier
update-manager
ubuntu-release-upgrader-gtk[/FONT]

and dependencies.

Thanks a lot **[COLOR=#000000]matt_symes[/COLOR]**

---

### Post by matt_symes on 2015-04-21
Hi

> /usr/lib/python2.7/dist-packages/six.py: cannot open `/usr/lib/python2.7/dist-packages/six.py' **(No such file or directory)**

That'll be the problem there :)

The package looks to be installed but the files are not there. We should try reinstalling python-six.

I assume that you can't use apt to install it directly ? (I would expect this to error)

```
sudo apt-get install --reinstall python-six
```

Is it still in your cache ? Does this return python-six ?

```
ls /var/cache/apt/archives/*six*
```

If not we will have to download it manually and reinstall it. 

So to be 100% sure of your system, can you post the output of this command

```
cat /etc/lsb-release && uname -a
```

**EDIT:**

I see you just beat me to it. Well done on fixing the problem. I'm glad it's fixed :)

Kind regards

---

### Post by hypnuntu on 2015-04-21
Thanks again for the help!

---

