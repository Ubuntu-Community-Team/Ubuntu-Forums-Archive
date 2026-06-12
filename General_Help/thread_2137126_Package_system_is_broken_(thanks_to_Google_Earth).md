---
title: "Package system is broken (thanks to Google Earth)"
date: 2013-04-19
forum: General Help
---

### Post by scottbomb on 2013-04-19
I tried to install the latest version of google-earth-stable_current_amd64.deb and it ended with the error "New software can't be installed because there is a problem with the software currently installed. Do you want to repair this problem now?"

I click the blue "Repair" button and I get this

Package operation failed. The installation or removal of a software package failed.

The details are:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%sudo apt-get -f install
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 412182 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.23-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/etc/sane.d/kodakaio.conf', which is different from other instances of package libsane:i386
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:
 ia32-libs-multiarch depends on libsane; however:
  Package libsane:i386 is not installed.

dpkg: error processing ia32-libs-multiarch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not configured yet.

dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
```
So.... I google this and find article [http://ubuntuforums.org/showthread.php?t=2061446](http://ubuntuforums.org/showthread.php?t=2061446) which suggests trying:
```
sudo dpkg --configure -a
sudo apt-get install -f
```
Problem still exists. So I continue with:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Which tells me to run 
```
sudo apt-get -f install
```
And I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  akonadi-backend-mysql akonadi-server fonts-lyx gnome-mahjongg
  libakonadiprotocolinternals1 libllvm3.1 libmjpegtools-1.9 libwebp2
  session-migration
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsane:i386
Suggested packages:
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
The following NEW packages will be installed:
  libsane:i386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/3,734 kB of archives.
After this operation, 8,970 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 412182 files and directories currently installed.)
Unpacking libsane:i386 (from .../libsane_1.0.23-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/etc/sane.d/kodakaio.conf', which is different from other instances of package libsane:i386
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.23-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This continues in an endless cycle and I cannot get it fixed. I can't seem to update anything now. Update-manager is also crashing every time I try to use it.

---

### Post by scottbomb on 2013-04-19
Well! I guess I fixed my own problem. I opened Synaptic and searched for "libsane". I marked libsane-common for reinstallation and let it run. The issue now seems to be resolved.

And thanks for the edits, papibe. I was lazy and for that I apologize.

---

### Post by claracc on 2013-04-20
> **scottbomb said:**
> Well! I guess I fixed my own problem. I opened Synaptic and searched for "libsane". I marked libsane-common for reinstallation and let it run. The issue now seems to be resolved.

And thanks for the edits, papibe. I was lazy and for that I apologize.

As you got fix your problem, please mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by scottbomb on 2013-04-24
Thanks for the link claracc. I hope Canonical revisits the way we mark threads as solved as that is by no means intuitive.

---

