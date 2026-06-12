---
title: "The following packages have unmet dependencies..."
date: 2013-10-09
forum: General Help
---

### Post by hennessy87 on 2013-10-09
Hello all,

I'm unable to open the Software Center or use apt-get. Instead I get this error:

```

The following packages have unmet dependencies:
 aptdaemon : Depends: python-aptdaemon (= 0.43+bzr805-0ubuntu9) but 0.43+bzr805-0ubuntu7 is to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I've tried running:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Nothing seems to work. Anyone have any ideas?

Thanks!

---

### Post by philinux on 2013-10-09
You don't say if you've done

```
sudo apt-get install -f
```

---

### Post by hennessy87 on 2013-10-09
> **philinux said:**
> You don't say if you've done

```
sudo apt-get install -f
```

Sorry. Here's the result of that

```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
The following packages will be upgraded:
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
3 upgraded, 0 newly installed, 0 to remove and 346 not upgraded.
3 not fully installed or removed.
Need to get 0 B/126 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 178160 files and directories currently installed.)
Preparing to replace python-aptdaemon.pkcompat 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb) ...
Unpacking replacement python-aptdaemon.pkcompat ...
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/aptdaemon', which is also in package python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu7
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb) ...
Unpacking replacement python-aptdaemon.gtk3widgets ...
dpkg: error processing /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/aptdaemon', which is also in package python-aptdaemon 0.43+bzr805-0ubuntu7
Preparing to replace python-aptdaemon 0.43+bzr805-0ubuntu7 (using .../python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb) ...
Unpacking replacement python-aptdaemon ...
dpkg: error processing /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/aptdaemon', which is also in package python-aptdaemon.gtk3widgets 0.43+bzr805-0ubuntu7
Errors were encountered while processing:
 /var/cache/apt/archives/python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb
 /var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb
 /var/cache/apt/archives/python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by slickymaster on 2013-10-09
Try to boot in recovery mode, enable the network, then select "dpkg" to try fix the system, and finally select "resume" to continue normal booting.

---

### Post by hennessy87 on 2013-10-09
> **slickymaster said:**
> Try to boot in recovery mode, enable the network, then select "dpkg" to try fix the system, and finally select "resume" to continue normal booting.

I get this error when i run dpkg

```

sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python-aptdaemon (= 0.43+bzr805-0ubuntu9); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu7.
dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
Setting up update-notifier-common (0.119ubuntu8.6) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 35, in <module>
    import chardet
ImportError: No module named chardet
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
ImportError: No module named apport.fileutils

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 35, in <module>
    import chardet
ImportError: No module named chardet
dpkg: error processing update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ttf-mscorefonts-installer:
 ttf-mscorefonts-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.
dpkg: error processing ttf-mscorefonts-installer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 aptdaemon
 update-notifier-common
 ttf-mscorefonts-installer


```

---

### Post by slickymaster on 2013-10-10
> **hennessy87 said:**
> I get this error when i run dpkg

```

sudo dpkg --configure -a
[COLOR=#ff0000]dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python-aptdaemon (= 0.43+bzr805-0ubuntu9); however:
  Version of python-aptdaemon on system is 0.43+bzr805-0ubuntu7.[/COLOR]
dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
Setting up update-notifier-common (0.119ubuntu8.6) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 35, in <module>
    import chardet
ImportError: No module named chardet
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
ImportError: No module named apport.fileutils

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debian.deb822
  File "/usr/lib/python2.7/dist-packages/debian/deb822.py", line 35, in <module>
    import chardet
ImportError: No module named chardet
dpkg: error processing update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 1
[COLOR=#ff0000]dpkg: dependency problems prevent configuration of ttf-mscorefonts-installer:
 ttf-mscorefonts-installer depends on update-notifier-common (>= 0.119ubuntu2); however:
  Package update-notifier-common is not configured yet.[/COLOR]
dpkg: error processing ttf-mscorefonts-installer (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 aptdaemon
 update-notifier-common
 ttf-mscorefonts-installer


```

it seems that you're dealing with two distinct issues.

Regarding the problem with **aptdaemon** there is a reported bug - [Bug #1223278]("https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/1223278") - that address it and my advise to you would be to mark it as affecting you, using the [This bug affects 1 person. Does this bug affect you?]("https://bugs.launchpad.net/ubuntu/+source/aptdaemon/+bug/1223278/+affectsmetoo") for the effect.

As for the the problem with **update-notifier-common** and **ttf-mscorefonts-installer** what you can do is to try to reinstall the package which contains deb822.py to see if it solves the issue with your update-notifier package and thus solving also the one with ttf-mscorefonts-installer. Run the following:```
sudo apt-get --reinstall install python-debian
```

---

