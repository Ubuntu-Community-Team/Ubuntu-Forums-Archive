---
title: "New software can't be installed, because there is a problem with the software current"
date: 2014-11-09
forum: General Help
---

### Post by lolwtfidk on 2014-11-09
This is the details I get when the package operation fails if I click repair:

```
installArchives() failed: E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb containing libgcc1:amd64, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.

dpkg: error processing archive /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb (--unpack):
 pre-dependency problem - not installing libgcc1:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of libc6:amd64:
 libc6:amd64 depends on libgcc1; however:
  Package libgcc1 is not installed.

dpkg: error processing package libc6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of multiarch-support:
 multiarch-support depends on libc6 (>= 2.3.6-2); however:
  Package libc6:amd64 is not configured yet.

dpkg: error processing package multiarch-support (--configure):
 dependency problems - leaving unconfigured


```
I tried this: [http://ubuntuforums.org/showthread.php?t=947124&p=5962046#post5962046](http://ubuntuforums.org/showthread.php?t=947124&p=5962046#post5962046) and got this:
```
$ sudo apt-get update
[sudo] password for ______: 
Ign http://extras.ubuntu.com trusty InRelease                             
Ign http://mirror1.ku.ac.th trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://extras.ubuntu.com trusty Release
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Ign http://mirror1.ku.ac.th trusty-updates InRelease
Ign http://mirror1.ku.ac.th trusty-backports InRelease
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign http://mirror1.ku.ac.th trusty-security InRelease
Hit http://mirror1.ku.ac.th trusty Release.gpg
Hit http://mirror1.ku.ac.th trusty-updates Release.gpg
Hit http://mirror1.ku.ac.th trusty-backports Release.gpg
Hit http://mirror1.ku.ac.th trusty-security Release.gpg
Hit http://mirror1.ku.ac.th trusty Release
Hit http://mirror1.ku.ac.th trusty-updates Release                         
Hit http://mirror1.ku.ac.th trusty-backports Release                       
Hit http://mirror1.ku.ac.th trusty-security Release                        
Hit http://mirror1.ku.ac.th trusty/main Sources                            
Hit http://mirror1.ku.ac.th trusty/restricted Sources
Hit http://mirror1.ku.ac.th trusty/universe Sources 
Hit http://mirror1.ku.ac.th trusty/multiverse Sources
Hit http://mirror1.ku.ac.th trusty/main amd64 Packages
Hit http://mirror1.ku.ac.th trusty/restricted amd64 Packages
Hit http://mirror1.ku.ac.th trusty/universe amd64 Packages
Hit http://mirror1.ku.ac.th trusty/multiverse amd64 Packages
Hit http://mirror1.ku.ac.th trusty/main i386 Packages
Hit http://mirror1.ku.ac.th trusty/restricted i386 Packages
Hit http://mirror1.ku.ac.th trusty/universe i386 Packages
Hit http://mirror1.ku.ac.th trusty/multiverse i386 Packages
Hit http://mirror1.ku.ac.th trusty/main Translation-en
Hit http://mirror1.ku.ac.th trusty/multiverse Translation-en
Hit http://mirror1.ku.ac.th trusty/restricted Translation-en
Hit http://mirror1.ku.ac.th trusty/universe Translation-en
Hit http://mirror1.ku.ac.th trusty-updates/main Sources
Hit http://mirror1.ku.ac.th trusty-updates/restricted Sources
Hit http://mirror1.ku.ac.th trusty-updates/universe Sources
Hit http://mirror1.ku.ac.th trusty-updates/multiverse Sources
Hit http://mirror1.ku.ac.th trusty-updates/main amd64 Packages
Hit http://mirror1.ku.ac.th trusty-updates/restricted amd64 Packages
Hit http://mirror1.ku.ac.th trusty-updates/universe amd64 Packages
Hit http://mirror1.ku.ac.th trusty-updates/multiverse amd64 Packages
Hit http://mirror1.ku.ac.th trusty-updates/main i386 Packages
Hit http://mirror1.ku.ac.th trusty-updates/restricted i386 Packages
Hit http://mirror1.ku.ac.th trusty-updates/universe i386 Packages
Hit http://mirror1.ku.ac.th trusty-updates/multiverse i386 Packages
Hit http://mirror1.ku.ac.th trusty-updates/main Translation-en
Hit http://mirror1.ku.ac.th trusty-updates/multiverse Translation-en
Hit http://mirror1.ku.ac.th trusty-updates/restricted Translation-en
Hit http://mirror1.ku.ac.th trusty-updates/universe Translation-en
Hit http://mirror1.ku.ac.th trusty-backports/main Sources
Hit http://mirror1.ku.ac.th trusty-backports/restricted Sources
Hit http://mirror1.ku.ac.th trusty-backports/universe Sources
Hit http://mirror1.ku.ac.th trusty-backports/multiverse Sources
Hit http://mirror1.ku.ac.th trusty-backports/main amd64 Packages
Hit http://mirror1.ku.ac.th trusty-backports/restricted amd64 Packages
Hit http://mirror1.ku.ac.th trusty-backports/universe amd64 Packages
Hit http://mirror1.ku.ac.th trusty-backports/multiverse amd64 Packages
Hit http://mirror1.ku.ac.th trusty-backports/main i386 Packages
Hit http://mirror1.ku.ac.th trusty-backports/restricted i386 Packages
Hit http://mirror1.ku.ac.th trusty-backports/universe i386 Packages
Hit http://mirror1.ku.ac.th trusty-backports/multiverse i386 Packages
Hit http://mirror1.ku.ac.th trusty-backports/main Translation-en
Hit http://mirror1.ku.ac.th trusty-backports/multiverse Translation-en
Hit http://mirror1.ku.ac.th trusty-backports/restricted Translation-en
Hit http://mirror1.ku.ac.th trusty-backports/universe Translation-en
Hit http://mirror1.ku.ac.th trusty-security/main Sources
Hit http://mirror1.ku.ac.th trusty-security/restricted Sources
Hit http://mirror1.ku.ac.th trusty-security/universe Sources
Hit http://mirror1.ku.ac.th trusty-security/multiverse Sources
Hit http://mirror1.ku.ac.th trusty-security/main amd64 Packages
Hit http://mirror1.ku.ac.th trusty-security/restricted amd64 Packages
Hit http://mirror1.ku.ac.th trusty-security/universe amd64 Packages
Hit http://mirror1.ku.ac.th trusty-security/multiverse amd64 Packages
Hit http://mirror1.ku.ac.th trusty-security/main i386 Packages
Hit http://mirror1.ku.ac.th trusty-security/restricted i386 Packages
Hit http://mirror1.ku.ac.th trusty-security/universe i386 Packages
Hit http://mirror1.ku.ac.th trusty-security/multiverse i386 Packages
Hit http://mirror1.ku.ac.th trusty-security/main Translation-en
Hit http://mirror1.ku.ac.th trusty-security/multiverse Translation-en
Hit http://mirror1.ku.ac.th trusty-security/restricted Translation-en
Hit http://mirror1.ku.ac.th trusty-security/universe Translation-en
Ign http://mirror1.ku.ac.th trusty/main Translation-en_US
Ign http://mirror1.ku.ac.th trusty/multiverse Translation-en_US
Ign http://mirror1.ku.ac.th trusty/restricted Translation-en_US
Ign http://mirror1.ku.ac.th trusty/universe Translation-en_US
Reading package lists... Done
$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
$ sudo apt-get clean
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not installed
E: Unmet dependencies. Try using -f.
$ sudo dpkg --remove -force --force-remove-reinstreq libgcc1
dpkg: error: conflicting actions -f (--field) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !


```

I tried ```
sudo apt-get install -f
``` and get this:
```
sudo apt-get install -f
[sudo] password for _____: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgcc1
The following NEW packages will be installed:
  libgcc1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/39.2 kB of archives.
After this operation, 132 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: No such file or directory
dpkg: regarding .../libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb containing libgcc1:amd64, pre-dependency problem:
 libgcc1 pre-depends on multiarch-support
  multiarch-support is unpacked, but has never been configured.

dpkg: error processing archive /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb (--unpack):
 pre-dependency problem - not installing libgcc1:amd64
Errors were encountered while processing:
 /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

---

### Post by bapoumba on 2014-11-09
Please have a look here : [https://answers.launchpad.net/ubuntu/+source/apt/+question/210735](https://answers.launchpad.net/ubuntu/+source/apt/+question/210735)
and post the outputs to 
```
ls -la /var/lib/dpkg/
ls -la /var/backups/dpkg*
```
depending on the result, the fix in the previous link may or may not be relevant to you.

---

### Post by dreibh on 2014-11-26
I solved the problem on my system by forcing an installation of libgcc1:sudo dpkg -i --force all /var/cache/apt/archives/libgcc1_1%3a4.9.1-0ubuntu1_amd64.deb

---

