---
title: "Problem Installing Audacity"
date: 2005-07-11
forum: General Help
---

### Post by Tad030 on 2005-07-11
When I try to install audacity, I receive the following error.  Any suggestions?

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsndfile1 1.0.10-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li) bsndfile1_1.0.10-2_i386.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

---

### Post by Xian on 2005-07-11
[QUOTE=Tad030]When I try to install audacity, I receive the following error.  Any suggestions?

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsndfile1 1.0.10-2
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/li) bsndfile1_1.0.10-2_i386.deb  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?[/QUOTE]
The us.archive.ubuntu.com mirrors have been quirky of late.

Replace each instance of 'us.archive.ubuntu.com' with 'archive.ubuntu.com' in your /etc/apt/sources.list. Then run another 'apt-get update' session in a terminal to refresh the repos.

---

### Post by Tad030 on 2005-07-11
Thanks for the tip, but it says I am not the owner of the file and cannot change permissions.  How do I fix that problem?  Sorry, I'm a newbie

---

### Post by SGC on 2005-07-11
Open the file with this command
sudo gedit /etc/apt/sources.list

Then enter your password

---

### Post by Tad030 on 2005-07-11
Horray!  Worked like a charm.  Much appreciated.  Now if I could just figure out Wine....  :)

---

### Post by Xian on 2005-07-11
[QUOTE=Tad030]Much appreciated.  Now if I could just figure out Wine....  :)[/QUOTE]
When you figure out Wine post a new How-To in [Tips & Tricks](http://www.ubuntuforums.org/forumdisplay.php?f=58). :)

---

### Post by irishboxer on 2007-01-25
Hi, I am also having trouble installing audacity using dapper and i am as new as they come. Here is what it tells me when i apt-get audacity.

:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
99% [2 Packages bzip2 0] [Connecting to us.archive.ubuntu.com] [Waiting for headbzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages [821kB]
99% [6 Packages gzip 0] [Waiting for headers]                        29.6kB/s 0sgzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Sub-process gzip returned an error code (1)
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources [1312kB]
99% [7 Sources gzip 0]                                               29.6kB/s 0sgzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 7B in 8s (1B/s)
Reading package lists... Done
brian@brian-laptop:~$ sudo aptitude install audacity
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  audacity libwxgtk2.4-1
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3376kB of archives. After unpacking 9859kB will be used.
The following packages have unmet dependencies:
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) which is a virtual package.
                 Depends: libgtk1.2 (>= 1.2.10-4) which is a virtual package.
  audacity: Depends: libflac++5c2 which is a virtual package.
            Depends: libid3tag0 (>= 0.15.1b) which is a virtual package.
            Depends: libmad0 (>= 0.15.1b) which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
:~$

---

