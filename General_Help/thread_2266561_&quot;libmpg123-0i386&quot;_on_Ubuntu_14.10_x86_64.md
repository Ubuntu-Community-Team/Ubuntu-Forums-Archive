---
title: "&quot;libmpg123-0:i386&quot; on Ubuntu 14.10 x86_64"
date: 2015-02-23
forum: General Help
---

### Post by DarkLeach7 on 2015-02-23
I'm a previous Ubuntu user so I know my way around a bit, however I have a problem that I can't seem to solve and I'm not getting a clear answer through looking at various other places.
I recently decided to Install Ubuntu 14.10 on my laptop again as I wanted to get back into Ubuntu again.
However I have a problem with installing wine.
Wine seemed okay installing at first but then the Ubuntu Software Center Window just froze up, I let it sit for about half and hour or so just in case something was actually happening, but it was still locked up, So I force closed it.
I went into terminal and ran
```
sudo apt-get install wine1.7
```
and I got this as output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine1.7 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.7-i386:i386 : Depends: libmpg123-0:i386 (>= 1.13.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
wine doesn't work at all even though it says it's installed here
so I tried to run
```
sudo apt-get -f install
```
and I got this as output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  libmpg123-0:i386
The following NEW packages will be installed:
  libmpg123-0:i386
0 upgraded, 1 newly installed, 0 to remove and 17 not upgraded.
3 not fully installed or removed.
Need to get 0 B/115 kB of archives.
After this operation, 374 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
I type 'Y" and I get this as output
```

(Reading database ... 229334 files and directories currently installed.)
Preparing to unpack .../libmpg123-0_1.18.0-1ubuntu1_i386.deb ...
Unpacking libmpg123-0:i386 (1.18.0-1ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libmpg123-0_1.18.0-1ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libmpg123-0/copyright', which is different from other instances of package libmpg123-0:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libmpg123-0_1.18.0-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
This is as far as I can get, I try and download the .deb from launchpad and run it and the Ubuntu Software Center shows
"Failed to satisfy all dependecies (broken cache)" and I can't install it
Some pages I found seem to say that they worked by me adding multiarch to dpkg ```
 sudo dpkg --add-architecture i386
``` (by adding the i386 architecture to the multiarch file) and I tried that and it still doesn't work. (I have since deleted that so it's back to how it was)
I then try and running this to see if I can at least get rid of it
```
sudo apt-get remove wine1.7
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 wine1.7-amd64 : Depends: wine1.7:any (= 1:1.7.34-0ubuntu1~ppa1)
 wine1.7-i386:i386 : Depends: libmpg123-0:i386 (>= 1.13.7) but it is not going to be installed
                     Depends: wine1.7:any:i386 (= 1:1.7.34-0ubuntu1~ppa1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
I can't seem to get rid of it either, so I'm stuck with a broken install with no clue how to fix it.
I have a partition of Windows 8.1 on my laptop in case I have to run anything Windows, so this isn't dire. I was just wondering if there's any possible fix for this.
So I can get rid of the Red sign in the top bar that says "Error: BrokenCount >0" with something about unmet dependencies.
As well as to get the software center to stop bugging me about "New software can't be installed, beacuse there is a problem with the software currently installed. Do you want to repair this problem now?" because I click on "Repair" option, enter my password and I just get thrown to the libmpg123-0 with the same "broken cache" error with this as failed output
 ```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 229334 files and directories currently installed.) 
Preparing to unpack .../libmpg123-0_1.18.0-1ubuntu1_i386.deb ... 
Unpacking libmpg123-0:i386 (1.18.0-1ubuntu1) ... 
dpkg: error processing archive /var/cache/apt/archives/libmpg123-0_1.18.0-1ubuntu1_i386.deb (--unpack): 
 trying to overwrite shared '/usr/share/doc/libmpg123-0/copyright', which is different from other instances of package libmpg123-0:i386 
Errors were encountered while processing: 
 /var/cache/apt/archives/libmpg123-0_1.18.0-1ubuntu1_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of wine1.7-i386: 
 wine1.7-i386 depends on libmpg123-0 (>= 1.13.7); however: 
  Package libmpg123-0:i386 is not installed. 
 
dpkg: error processing package wine1.7-i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of wine1.7: 
 wine1.7 depends on wine1.7-i386 (= 1:1.7.34-0ubuntu1~ppa1); however: 
  Package wine1.7-i386 is not configured yet. 
 
dpkg: error processing package wine1.7 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of wine1.7-amd64: 
 wine1.7-amd64 depends on wine1.7:any (= 1:1.7.34-0ubuntu1~ppa1); however: 
  Package wine1.7 is not configured yet. 
 
dpkg: error processing package wine1.7-amd64 (--configure): 
 dependency problems - leaving unconfigured 


```
TL;DR I'm having a problem with "libmpg123-0:i386" on my x86_64 version of Ubuntu 14.10 and applications I want to install require the 32 bit version. Which refuses to install.

Any help would be greatly appreciated

**UPDATE**:
After a bit of more thorough searching, I found a solution that seems to be working. Nothing has broken as a result of this so far so I'll post it here.
It wasn't letting me install this because of a conflict of some kind but I found a force option through dpkg
```

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmpg123-0_1.18.0-1ubuntu1_i386.deb

```
and I recieved this as output
```

(Reading database ... 229334 files and directories currently installed.)
Preparing to unpack .../libmpg123-0_1.18.0-1ubuntu1_i386.deb ...
Unpacking libmpg123-0:i386 (1.18.0-1ubuntu1) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite shared '/usr/share/doc/libmpg123-0/copyright', which is different from other instances of package libmpg123-0:i386
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite shared '/usr/share/doc/libmpg123-0/changelog.Debian.gz', which is different from other instances of package libmpg123-0:i386
Setting up libmpg123-0:i386 (1.18.0-1ubuntu1) ...
Processing triggers for libc-bin (2.19-10ubuntu2.2) ...

```
and sure enough running sudo apt-get -f install again Wine completed installing and seems to work just fine.
If anything eventually breaks because of this I'll post back here, but everything is running smoothly, MP3s and all.
I hope this helps someone in the future.

---

