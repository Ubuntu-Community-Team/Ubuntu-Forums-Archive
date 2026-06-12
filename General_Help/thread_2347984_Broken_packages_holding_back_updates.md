---
title: "Broken packages holding back updates?"
date: 2016-12-30
forum: General Help
---

### Post by crouchy89 on 2016-12-30
I am still having issues updating the software on my computer ([previous thread]("https://ubuntuforums.org/showthread.php?t=2346521")), with the issue now (I think) being broken packages.

First, I ran the following:

```

sudo apt-get clean
sudo mv /var/lib/apt/lists /tmp
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

Trimming the lines above I receive 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libnss-winbind libpam-winbind pulseaudio-module-gconf
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

I tried installing these packages manually:

```

sudo apt-get install libnss-winbind libpam-winbind pulseaudio-module-gconf 
...
The following packages have unmet dependencies:
 libnss-winbind : Depends: samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: libwbclient0 (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: samba-libs (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
 libpam-winbind : Depends: samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
 pulseaudio-module-gconf : Depends: libpulse0 (= 1:8.0-0ubuntu3.1) but 1:8.0-0ubuntu3 is to be installed
                           Depends: pulseaudio (= 1:8.0-0ubuntu3.1) but 1:8.0-0ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.

```

So I next tried installing each of the dependencies individually, but each time I could not download a more recent version. For example:

```

sudo apt-get install winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
winbind is already the newest version (2:4.3.11+dfsg-0ubuntu0.16.04.1).
winbind set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```


If I run the Software Updater it says that the software on my computer is up to date, downloading from Main Server and server for the United States. Running Ubuntu 16.04 LTS

Any input is greatly appreciated

---

### Post by Yellow Pasque on 2016-12-30
Looking at the sources.list in your previous thread, you have entries for multiverse and universe, but no main (or restricted if you need it). Of course, there may be other entries in .list files in /etc/apt/sources.list.d/

---

### Post by crouchy89 on 2016-12-30
The contents of that folder are the following:

```

cd /etc/apt.sources.list
ls
cran.list                                      mendeleydesktop.list.distUpgrade                                                  private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
cran.list.distUpgrade                          mendeleydesktop.list.save                                                         steam.list
cran.list.save                                 otto-kesselgulasch-gimp-precise.list                                              steam.list.distUpgrade
google-chrome.list                             otto-kesselgulasch-gimp-precise.list.distUpgrade                                  steam.list.save
google-chrome.list.distUpgrade                 otto-kesselgulasch-gimp-precise.list.save                                         webupd8team-java-precise.list
google-chrome.list.save                        otto-kesselgulasch-gimp-trusty.list                                               webupd8team-java-precise.list.distUpgrade
mc3man-gstffmpeg-keep-trusty.list              otto-kesselgulasch-gimp-trusty.list.distUpgrade                                   webupd8team-java-precise.list.save
mc3man-gstffmpeg-keep-trusty.list.distUpgrade  otto-kesselgulasch-gimp-trusty.list.save                                          webupd8team-java-trusty.list
mc3man-gstffmpeg-keep-trusty.list.save         private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list              webupd8team-java-trusty.list.distUpgrade
mendeleydesktop.list                           private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.distUpgrade  webupd8team-java-trusty.list.save

```

---

### Post by Bashing-om on 2016-12-30
crouchy89; Yuk !

As I pass by.

Recheck that command entry :
> 
cd /etc/apt.sources.list

as apt.sources.list
is not a valid default file .
see mine:
> 
sysop@x1604:~$ ls -al /etc/apt/sources.list
-rw-rw-r-- 1 root root 3028 Dec 23 18:02 /etc/apt/sources.list
sysop@x1604:~$

where the path is " /etc/apt/..............."

something strange going on here ?

---

### Post by crouchy89 on 2016-12-30
That appears to have been a typo, sorry

```

cd /etc/apt
ls
$ apt.conf.d  auth.conf  preferences.d  save  sources.list  sources.list.bak  sources.list.d  sources.list.save  trusted.gpg  trusted.gpg~

```
and
```

 ls -al /etc/apt/sources.list
-rw-r--r-- 1 root root 691 Dec 30 10:39 /etc/apt/sources.list

```

---

### Post by mc4man on 2016-12-30
Open up Software & Updates > Updates & make sure that the 1st two are enabled (xenial-security & xenial-updates
Then update (reload) sources & try again

(- there is a screen attached, will show up at some point depending on the weather, moon, whatever...

---

### Post by Bashing-om on 2016-12-30
crouchy89;l Hey;

I will poke at it again.


We are looking at a dependency issue with 3 packages with a few packages in common for the dependencies.
Now in all likely hood, will find that a PPA is at the root of this.
As one instance of the dependency we have:
> 
 sysop@x1604:~$ apt list winbind
Listing... Done
winbind/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64
N: There is 1 additional version. Please use the '-a' switch to see it
sysop@x1604:~$ 

where you have a older version held by some other package ( 3rd party ??) .

so now we look and see if we can determine the source:
show us :
```

apt-cache policy libnss-winbind libpam-winbind pulseaudio-module-gconf

```
I do not do Windows, so samba for me is not a factor in finding your fault.
Do you really need samba; or the source that installs these packages  ?
```

apt show libnss-winbind

``` 
I do like to keep a clean system !


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by crouchy89 on 2016-12-30
@mc4man: those two boxes are checked

@bashing-om

The first line executed returns:

```

apt-cache policy libnss-winbind libpam-winbind pulseaudio-module-gconf
libnss-winbind:
  Installed: 2:4.3.11+dfsg-0ubuntu0.16.04.1
  Candidate: 2:4.3.11+dfsg-0ubuntu0.16.04.3
  Version table:
     2:4.3.11+dfsg-0ubuntu0.16.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
 *** 2:4.3.11+dfsg-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
     2:4.3.8+dfsg-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libpam-winbind:
  Installed: 2:4.3.11+dfsg-0ubuntu0.16.04.1
  Candidate: 2:4.3.11+dfsg-0ubuntu0.16.04.3
  Version table:
     2:4.3.11+dfsg-0ubuntu0.16.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
 *** 2:4.3.11+dfsg-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status
     2:4.3.8+dfsg-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
pulseaudio-module-gconf:
  Installed: 1:8.0-0ubuntu3
  Candidate: 1:8.0-0ubuntu3.1
  Version table:
     1:8.0-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
 *** 1:8.0-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

```

The more recent versions all show up as candidates at least

I think samba is used for interfacing with other hardware

```

 apt show libnss-winbind
Package: libnss-winbind
Version: 2:4.3.11+dfsg-0ubuntu0.16.04.3
Priority: optional
Section: universe/net
Source: samba
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Samba Maintainers <pkg-samba-maint@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 144 kB
Pre-Depends: dpkg (>= 1.15.6~)
Depends: samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.3), winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3), libbsd0 (>= 0.0), libc6 (>= 2.14), libtalloc2 (>= 2.0.4~git20101213), libwbclient0 (= 2:4.3.11+dfsg-0ubuntu0.16.04.3), samba-libs (= 2:4.3.11+dfsg-0ubuntu0.16.04.3)
Suggests: libpam-winbind
Breaks: libpam-winbind (<< 2:3.6.5-2), winbind (<< 2:3.5.11~dfsg-3)
Replaces: libpam-winbind (<< 2:3.6.5-2), samba (<= 2.2.3-2), winbind (<< 2:3.5.11~dfsg-3), winbind4
Homepage: http://www.samba.org
Supported: 5y
Download-Size: 12.3 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Description: Samba nameservice integration plugins
 Samba is an implementation of the SMB/CIFS protocol for Unix systems,
 providing support for cross-platform file and printer sharing with
 Microsoft Windows, OS X, and other Unix systems.  Samba can also function
 as an NT4-style domain controller, and can integrate with both NT4 domains
 and Active Directory realms as a member server.
 .
 This package provides nss_winbind, a plugin that integrates
 with a local winbindd server to provide user/group name lookups to the
 system; and nss_wins, which provides hostname lookups via both the NBNS and
 NetBIOS broadcast protocols.


N: There are 2 additional records. Please use the '-a' switch to see them.

```

Many thanks

---

### Post by Bashing-om on 2016-12-30
crouchy89; Well, surprise surprise.

No 3rd party sources here .
sure makes one wonder:
> 
*** 2:4.3.11+dfsg-0ubuntu0.16.04.1 100
        100 /var/lib/dpkg/status

Now we can spend some time and try and find out the why .. or we can bulldoze ahead:
bulldoze:
```

sudo apt purge libnss-winbind

```
depending in this result we may try and remove the others and then see what results in RE-installing these packages we removed from the system .

[INDENT][INDENT]willing to find out
[/INDENT][/INDENT]

---

### Post by crouchy89 on 2016-12-31
Not much happened:

```

sudo apt purge libnss-winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libnss-winbind*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 144 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 352375 files and directories currently installed.)
Removing libnss-winbind:amd64 (2:4.3.11+dfsg-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...

```

re-install

```

sudo apt-get install libnss-winbind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libnss-winbind : Depends: samba-common (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: winbind (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: libwbclient0 (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
                  Depends: samba-libs (= 2:4.3.11+dfsg-0ubuntu0.16.04.3) but 2:4.3.11+dfsg-0ubuntu0.16.04.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Bashing-om on 2016-12-31
crouchy89; Ho Kay !

That looked hopeful.
Try:
```

sudo apt purge samba-common samba-libs winbind libwbclient0 libnss-winbind
sudo apt install libnss-winbind

``` see if the package manager will now pull in the correct versions .


[INDENT][INDENT]could be yes
[/INDENT][/INDENT]

---

