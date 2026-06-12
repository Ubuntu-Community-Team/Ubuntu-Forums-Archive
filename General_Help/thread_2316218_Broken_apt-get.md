---
title: "Broken apt-get"
date: 2016-03-06
forum: General Help
---

### Post by attila4 on 2016-03-06
Hi!

I tried to install gfortran, but it needed the libglib2.0 so I tried to install this too. But that didn't work and now I got 'Error: BrokenCount >0'. I looked after how to solve this, I found this:
```

sudo apt-get clean 
sudo apt-get update[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]sudo dpkg --configure -a[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
```

When I ran those lines I got this:

```
dpkg: dependency problems prevent configuration of libglib2.0-dev: libglib2.0-dev depends on libglib2.0-0 (= 2.46.1-1); however:
  Version of libglib2.0-0:amd64 on system is 2.46.2-1ubuntu1.
 libglib2.0-dev depends on libglib2.0-bin (= 2.46.1-1); however:
  Version of libglib2.0-bin on system is 2.46.2-1ubuntu1.


dpkg: error processing package libglib2.0-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglib2.0-dev



```

If I try ```
sudo apt-get install -f
``` this  happens:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-dev
Suggested packages:
  libglib2.0-doc
The following packages will be upgraded:
  libglib2.0-dev
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 1.368 kB of archives.
After this operation, 4.096 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://hu.archive.ubuntu.com/ubuntu/ wily-updates/main libglib2.0-dev amd64 2.46.2-1ubuntu1 [1.368 kB]
Fetched 1.368 kB in 0s (4.357 kB/s)  
(Reading database ... 643827 files and directories currently installed.)
Preparing to unpack .../libglib2.0-dev_2.46.2-1ubuntu1_amd64.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/libglib2.0-dev_2.46.2-1ubuntu1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libglib2.0-dev_2.46.2-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I dont't want gfortran anymore, I just want my atp-get work again. How can I solve this problem?

---

### Post by pissedoffdude on 2016-03-06
Hi,

Try this first:
```
sudo apt-get install python3-dev
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```

If you're still running into issues at this point, doing a ```
sudo apt-get remove libglib2.0-dev
```

Was the package you were trying to install originally in a non standard repository?  If it wasn't, you should be fine upgrading all your packages prior to installing it.

---

### Post by vasa1 on 2016-03-06
Look at```
sudo dpkg -C
```
From *man dpkg*,```
        -C, --audit
              Searches  for  packages  that have been installed only partially on
              your system. [B]dpkg will suggest what to do with  them  to  get  them
              working[/B].


```

---

### Post by attila4 on 2016-03-06
Hi,

I can't run ```
apt-get install python3-dev
``` because I get this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.46.1-1) but 2.46.2-1ubuntu1 is to be installed
                  Depends: libglib2.0-bin (= 2.46.1-1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And ```
 apt-get remove 
``` also doesn't work.

I think I use only standard repos., this is my source.list:
```

# deb cdrom:[Ubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://hu.archive.ubuntu.com/ubuntu/ wily main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://hu.archive.ubuntu.com/ubuntu/ wily-updates main restricted
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://hu.archive.ubuntu.com/ubuntu/ wily universe
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily universe
deb http://hu.archive.ubuntu.com/ubuntu/ wily-updates universe
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://hu.archive.ubuntu.com/ubuntu/ wily multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily multiverse
deb http://hu.archive.ubuntu.com/ubuntu/ wily-updates multiverse
deb-src http://hu.archive.ubuntu.com/ubuntu/ wily-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://security.ubuntu.com/ubuntu wily-security main restricted
deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
deb http://security.ubuntu.com/ubuntu wily-security universe
deb-src http://security.ubuntu.com/ubuntu wily-security universe
deb http://security.ubuntu.com/ubuntu wily-security multiverse
deb-src http://security.ubuntu.com/ubuntu wily-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu utopic partner
# deb-src http://archive.canonical.com/ubuntu utopic partner

```

---

### Post by attila4 on 2016-03-06
If I run 
```

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libglib2.0-dev       Development files for the GLib library

```
I got this:

```

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 libglib2.0-dev       Development files for the GLib library

```

But the problem comes form that the installation of libglib2.0-dev doesn't work, and if I try to reinstall the same happens.

What? Shortened urls? It depends on where I see that url.

---

### Post by pissedoffdude on 2016-03-06
Are you able to execute ```
dpkg -r libglib2.0-dev

```

---

### Post by attila4 on 2016-03-06
Nope,
```
dpkg - r libglib2.0-dev
```

gives 
```
dpkg: error processing package libglib2.0-dev (--remove): package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 libglib2.0-dev

```

And reinstalling doesn't work. Is there a possible way to solve this?

---

### Post by pissedoffdude on 2016-03-07
Eww, I'm not liking that you didn't have any unofficial repos either.  Give ```
sudo dpkg --remove --force-remove-reinstreq libglib2.0-dev

```

A shot.  If it still fails, let us know if this page helps: [http://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error](http://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error)

---

### Post by attila4 on 2016-03-07
Well when I need something I add unofficial repos, but after I didn't use the program I remove the program and the repo too. And I use some other program which I compiled from source. 

I got this for that:
```

dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 643327 files and directories currently installed.)
Removing libglib2.0-dev (2.46.1-1) ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing package libglib2.0-dev (--remove):
 subprocess installed pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libglib2.0-dev



```

That page doesn't help, I can't run ```
[COLOR=#111111][FONT=Consolas]sudo apt-get install libglib2.0-dev[/FONT][/COLOR]
```, because I get error for this.

---

### Post by matt_symes on 2016-03-07
Hi

You want to start off by removing the utopic repo in your sources file.

Which unofficial repo did you use ? The above one ?

Kind regards

---

