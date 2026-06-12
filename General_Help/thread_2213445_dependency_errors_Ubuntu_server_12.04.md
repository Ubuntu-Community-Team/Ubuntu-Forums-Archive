---
title: "dependency errors Ubuntu server 12.04"
date: 2014-03-26
forum: General Help
---

### Post by kevin71 on 2014-03-26
This is what I get when I try to run apt-get check and apt-get -f install. No matter what I do I cannot seem to get any new packages to install or existing ones to update

Any help is appreciated

```
~$ sudo apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.5 is installed
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.48.58) but 3.2.0.60.71 is installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-48-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.



~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  initramfs-tools linux-generic-pae linux-image-generic-pae
3 upgraded, 0 newly installed, 0 to remove and 109 not upgraded.
5 not fully installed or removed.
Need to get 0 B/53.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.5.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-3.2.0-60-generic-pae:
 linux-image-3.2.0-60-generic-pae depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-48-generic-pae; however:
  Package linux-image-3.2.0-48-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.48.58); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.48.58); however:
  Version of linux-headers-generic-pae on system is 3.2.0.60.71.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-60-generic-pae
 linux-image-generic-pae
 linux-generic-pae
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Navneet_Kumar on 2014-03-27
Using a gui package manager such as Synaptic Package Manager would be best.............otherwise you have to manually met dependencies for each of these packages............

---

### Post by kevin71 on 2014-03-27
Since I'm using Ubuntu server I don't have a GUI installed, and due to the dependency problem I can't install a GUI. In either case Synaptic doesn't look like it would help since it's just a frontend for apt, which is where the error is occurring




From what I can tell the problem is that a package requires a lower version dependency than what I have installed, but I can;t seem to roll back to a lower version, at least not automatically...

---

### Post by mcduck on 2014-03-27
> **Navneet_Kumar said:**
> Using a gui package manager such as Synaptic Package Manager would be best.............otherwise you have to manually met dependencies for each of these packages............

There's no functional differecne between using apt-get or Synaptc. :D

Anyway, what does "sudo apt-get update" say?

---

### Post by kevin71 on 2014-03-31
apt-get update seems to work fine, it reads all the package lists and updates them

```
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:4 http://us.archive.ubuntu.com precise-updates/main Sources [453 kB]
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:6 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]
Get:7 http://us.archive.ubuntu.com precise-updates/universe Sources [105 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]
Get:9 http://us.archive.ubuntu.com precise-updates/main i386 Packages [784 kB]
Get:10 http://security.ubuntu.com precise-security/main Sources [101 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [12           .2 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [243            kB]
Get:13 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15           .5 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Get:14 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:15 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [1,789 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [401 kB]
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,6           20 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [96.5            kB]
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,6           46 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,371 kB in 3s (615 kB/s)
Reading package lists... Done

```

A subsequent run shows no new updates

```
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-updates Release
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Reading package lists... Done


```

---

### Post by mcduck on 2014-04-01
The package versions in the repoitories seem to have their dependencies matching correctly with available versions. Perhaps you just happened to run the update while new packages were being added to the repositories or something? Does "sudo apt-get dist-upgrade" work correctly now or does the problem still exist?

---

### Post by kevin71 on 2014-04-01
Thasks for your replies

sudo apt-get dist-upgrade returns the same dependency error as apt-get check, this error has actually been on the system for several weeks

```
~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.5 is installed
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.48.58) but 3.2.0.60.71 is installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-48-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
```

apt-get -f install is the same situation as the first post

```
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools linux-generic-pae linux-image-generic-pae
The following packages will be upgraded:
  initramfs-tools linux-generic-pae linux-image-generic-pae
3 upgraded, 0 newly installed, 0 to remove and 109 not upgraded.
5 not fully installed or removed.
Need to get 0 B/53.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.5.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-3.2.0-60-generic-pae:
 linux-image-3.2.0-60-generic-pae depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-48-generic-pae; however:
  Package linux-image-3.2.0-48-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.48.58); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.48.58); however:
  Version of linux-headers-generic-pae on system is 3.2.0.60.71.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-60-generic-pae
 linux-image-generic-pae
 linux-generic-pae
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


I'm starting to think it may be time to just wipe the system and start fresh

---

### Post by Stijn_Verrept on 2014-04-16
I have the EXACT same problem.  Did you happen to find a solution?

---

### Post by Stijn_Verrept on 2014-04-16
Good news!

I found a solution that worked for me.

Open */var/lib/dpkg/status* in an editor (nano or something)
Remove all the lines that belong to the bad package

Then you can do the 

[I]sudo apt-get -f install 
[/I]
Without any problems!

Good luck :-)

---

### Post by kevin71 on 2014-04-16
Unfortunately a few days after my last post I ran into some more sever problems and was forced to completely reinstall my system. 

From what I can tell this happened because I was using different programs to manage packages (apt mostly, but occasionally installing a package manually with dpkg) so I will keep this in mind if it happens in the future. Thanks

---

### Post by glug1012 on 2015-02-06
Thank you for putting me on the right track.  I found that I did not have to delete the entire line for this to work.  When i found the entry for the package that was causing me trouble (initramfs-tools), this is what I found (Emphasis mine):

[SOURCE]Depends: **initramfs-tools-bin (>= 0.99ubuntu13.1)**, **initramfs-tools-bin (<< 0.99ubuntu13.1.1~)**, klibc-utils (>= 1.5.9-1), busybox-initramfs (>= 1:1.13.3-1ubuntu5), cpio, module-init-tools, udev (>= 147~-5), findutils (>= 4.2.24), util-linux (>> 2.15~rc1)[/SOURCE]

Note how it *requires* initramfs-tools-bin (>=0.99x) and initramfs-tools-bin (<<0.99x).  That's a level of stupid that really does require a computer. I simply deleted the entry requiring the lower version and everything ran normally.

Now I get to do **a lot** of patching and pruning, as this server hasn't been able to apply patches for months.

Thanks again, heartily!

---

### Post by confiq2 on 2015-07-28
> **glug1012 said:**
> 
Note how it *requires* initramfs-tools-bin (>=0.99x) and initramfs-tools-bin (<<0.99x).  That's a level of stupid that really does require a computer. I simply deleted the entry requiring the lower version and everything ran normally.


This saved me wiping whole system!

---

