---
title: "dpkg: error processing package"
date: 2017-02-20
forum: General Help
---

### Post by valeriymotornyy on 2017-02-20
Hi,

I was trying to install php7 on Ubuntu 16.04.

I ran: sudo apt-get install php7.0
These are the errors i received: 

```

Setting up php7.0-common (7.0.16-2+deb.sury.org~xenial+1) ...
dpkg: error processing package php7.0-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php7.0-json:
 php7.0-json depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-opcache:
 php7.0-opcache depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0-opcache (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    dpkg: dependency problems prevent configuration of php7.0-readline:
 php7.0-readline depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0-readline (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php7.0-cli:
 php7.0-cli depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.
 php7.0-cli depends on php7.0-json; however:
  Package php7.0-json is not configured yet.
 php7.0-cli depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.
 php7.0-cli depends on php7.0-readline; however:
  Package php7.0-readline is not configured yet.


dpkg: error processing package php7.0-cli (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php7.0-fpm:
 php7.0-fpm depends on php7.0-cli; however:
  Package php7.0-cli is not configured yet.
 php7.0-fpm depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.
 php7.0-fpm depends on php7.0-json; however:
  Package php7.0-json is not configured yet.
 php7.0-fpm depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.


dpkg: error processing package php7.0-fpm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php7.0:
 php7.0 depends on libapache2-mod-php7.0 | php7.0-fpm | php7.0-cgi; however:
  Package libapache2-mod-php7.0 is not installed.
  Package php7.0-fpm is not configured yet.
  Package php7.0-cgi is not installed.
 php7.0 depends on php7.0-common; however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php7.0-gd:
 php7.0-gd depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0-gd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php7.0-mysql:
 php7.0-mysql depends on php7.0-common (= 7.0.16-2+deb.sury.org~xenial+1); however:
  Package php7.0-common is not configured yet.


dpkg: error processing package php7.0-mysql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 php7.0-common
 php7.0-json
 php7.0-opcache
 php7.0-readline
 php7.0-cli
 php7.0-fpm
 php7.0
 php7.0-gd
 php7.0-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to run: sudo apt-get update 
But i also get errors like:

```

W: The repository 'http://ppa.launchpad.net/adabbas/1stppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/adabbas/1stppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I tried to clean cache, repair broken packages, reinstall php7 but nothing seems to do the trick.
Any suggestions will be much appreciated.

Thanks,
Val

---

### Post by howefield on 2017-02-20
For your second error, if you go to [http://ppa.launchpad.net/adabbas/1stppa/ubuntu](http://ppa.launchpad.net/adabbas/1stppa/ubuntu) you'll see that there is no repository for Xenial, you are querying a non existent source hence the "does not have a Release file" and subsequent errors. Remove the file pointing to it from your /etc/apt/sources.list.d/ folder.

Might be helpful to see your other ppas which may be causing the first error also.. can you post the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by valeriymotornyy on 2017-02-20
Thanks for the reply !! Here is the output to my ppas:

```

/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://ie.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/adabbas-ubuntu-1stppa-xenial.list:deb http://ppa.launchpad.net/adabbas/1stppa/ubuntu xenial main
/etc/apt/sources.list.d/adabbas-ubuntu-1stppa-xenial.list.save:deb http://ppa.launchpad.net/adabbas/1stppa/ubuntu xenial main
/etc/apt/sources.list.d/atlassian-hipchat4.list:deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client xenial main
/etc/apt/sources.list.d/atlassian-hipchat4.list.save:deb https://atlassian.artifactoryonline.com/atlassian/hipchat-apt-client xenial main
/etc/apt/sources.list.d/gnome-terminator-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu xenial main
/etc/apt/sources.list.d/gnome-terminator-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/gnome-terminator/ppa/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/mc3man-ubuntu-xerus-media-xenial.list:deb http://ppa.launchpad.net/mc3man/xerus-media/ubuntu xenial main
/etc/apt/sources.list.d/mc3man-ubuntu-xerus-media-xenial.list.save:deb http://ppa.launchpad.net/mc3man/xerus-media/ubuntu xenial main
/etc/apt/sources.list.d/nodesource.list:deb https://deb.nodesource.com/node_6.x xenial main
/etc/apt/sources.list.d/nodesource.list:deb-src https://deb.nodesource.com/node_6.x xenial main
/etc/apt/sources.list.d/nodesource.list.save:deb https://deb.nodesource.com/node_6.x xenial main
/etc/apt/sources.list.d/nodesource.list.save:deb-src https://deb.nodesource.com/node_6.x xenial main
/etc/apt/sources.list.d/ondrej-ubuntu-php-xenial.list:deb http://ppa.launchpad.net/ondrej/php/ubuntu xenial main
/etc/apt/sources.list.d/ondrej-ubuntu-php-xenial.list.save:deb http://ppa.launchpad.net/ondrej/php/ubuntu xenial main
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list.save:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-stable.list:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-stable.list.save:deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/phalcon-ubuntu-stable-xenial.list:deb http://ppa.launchpad.net/phalcon/stable/ubuntu xenial main
/etc/apt/sources.list.d/phalcon-ubuntu-stable-xenial.list.save:deb http://ppa.launchpad.net/phalcon/stable/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list:deb http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-atom-xenial.list.save:deb http://ppa.launchpad.net/webupd8team/atom/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-brackets-xenial.list:deb http://ppa.launchpad.net/webupd8team/brackets/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-brackets-xenial.list.save:deb http://ppa.launchpad.net/webupd8team/brackets/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-sublime-text-3-xenial.list:deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-sublime-text-3-xenial.list.save:deb http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu xenial main

```

I removed i removed file that was pointing to adabbas/1stppa/ubuntu in /etc/apt/sources.list.d/
The apt-get update didn't return any errors. But installing php still returns the same errors as previous.

I just thought that the failed update might be cause of the php installation fail but maybe those are not related.

Thanks,
Val

---

### Post by valeriymotornyy on 2017-02-20
Also part of the error message when im trying to install php are these warning about missing packages (i cant post the whole list because its too long).
Most of them look like they have nothing to do with php it self, but should i install them any ? 

```

dpkg: warning: files list file for package 'mokutil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatk-adaptor:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbisfile3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libquadmath0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxkbfile1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-sound-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnpth0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgom-1.0-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt5qml5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-gconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vdpau-driver-all:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'evolution-data-server' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaccount-plugin-generic-oauth' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhtml-tagset-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-ping' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcgmanager0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'evince' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxi6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libedit2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'intel-gpu-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwinpr-interlocked0.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblist-moreutils-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qmlscene' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'baobab' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hplip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libart-2.0-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libenchant1c2a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libraw15:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'transmission-gtk' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgomp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-draw' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkpathsea6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-domain-tld-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpaper1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plainbox-provider-checkbox' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt5quick5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rhythmbox-plugins' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatomic1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxaw7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython3-stdlib:amd64' missing; assuming package has no files currently installed

```

Thanks,
Val

---

### Post by gordintoronto on 2017-02-20
It might be useful to make a copy of your sources.list and sources.list.d, then comment out everything which is not in ubuntu.com, then see how your commands work.

---

