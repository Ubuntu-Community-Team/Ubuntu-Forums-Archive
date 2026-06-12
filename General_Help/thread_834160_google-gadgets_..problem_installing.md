---
title: "google-gadgets ..problem installing"
date: 2008-06-19
forum: General Help
---

### Post by dexter.deepak on 2008-06-19
i just tried the following link (which is for hardy but i am on gutsy):
[http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild](http://code.google.com/p/google-gadgets-for-linux/wiki/HowToBuild)

i tried apt-get but it says that 
Package libqtwebkit1d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libqtwebkit1d has no installation candidate

then i went for the build process and i get the error at following step :
dpak@dpak-server:~$ ../../configure --enable-debug
bash: ../../configure: No such file or directory

can someone help me ..

---

### Post by Exsecrabilus on 2008-06-19
[http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/](http://tombuntu.com/index.php/2008/06/16/install-google-gadgets-for-linux-on-ubuntu/)

Use method 2, since the repos are an easier way to update than reinstalling .deb packages.

---

### Post by dexter.deepak on 2008-06-19
after editing the sources .list i issued the following command, (after updating):

dpak@dpak-server:~$ sudo apt-get install google-gadgets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  google-gadgets: Depends: libcairo2 (>= 1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
                  Depends: libkrb53 (>= 1.6.dfsg.2) but 1.6.dfsg.1-7ubuntu0.1 is to be installed
                  Depends: libmozjs0d (>= 1.8.1.5) but 1.8.1.4-2ubuntu5 is to be installed
                  Depends: libpango1.0-0 (>= 1.20.1) but 1.18.3-0ubuntu1 is to be installed
                  Depends: libqt4-core (>= 4.3.4) but 4.3.2-0ubuntu3.2 is to be installed
                  Depends: libqt4-gui (>= 4.3.4) but 4.3.2-0ubuntu3.2 is to be installed
                  Depends: libqtwebkit1d but it is not installable
                  Depends: libssl0.9.8 (>= 0.9.8f-1) but 0.9.8e-5ubuntu3.2 is to be installed
E: Broken packages

---

### Post by Exsecrabilus on 2008-06-19
The dependancies are unmet.

You are running Gutsy, I don't think there is a way to upgrade the packages to meet the dependences them unless you upgrade to Hardy or (possibly) enable *gutsy-backports*.

---

### Post by Happy_Man on 2008-06-19
First, in order to get anything working, you will have to run ```
sudo apt-get -f install
```

---

### Post by dexter.deepak on 2008-06-20
i have already enabled the gutsy-backports.it doesnt work.
i will try dist-upgrade now.

---

### Post by Exsecrabilus on 2008-06-20
> **dexter.deepak said:**
> i have already enabled the gutsy-backports.it doesnt work.
i will try dist-upgrade now.
You're gonna upgrade? Hoorah! \\:D/

---

### Post by dexter.deepak on 2008-06-20
man !!:shock:
i owe...i'll never says a damn "yes" to that upgrade process. i thought just doing dist-upgrade will do !!! i now i am astounded to see a size of 1.5gb ob packages to be downloaded !!!](*,)

---

### Post by dexter.deepak on 2008-06-20
..this means, this is the end of my dreams of running google-gadgets on ubuntu ??

---

### Post by Exsecrabilus on 2008-06-20
There's always [Screenlets](http://tombuntu.com/index.php/2008/03/17/os-x-like-widgets-with-screenlets-on-ubuntu-3rd-update/), try that. It's specially designed for Linux (unlike Google which has Linux available as a second option to develop after Windows and OS X.)

If you are trying to upgrade, I would rather you download the .iso file, burn it to a disc and do a fresh install, since it will be faster, you will notice new stuff more and if you changed the system's configuration horribly before, it will be resolved.

---

### Post by dexter.deepak on 2008-06-20
thanks !!
i just forgot the desklets...
google-gadgets previewa looked much more coool.

---

