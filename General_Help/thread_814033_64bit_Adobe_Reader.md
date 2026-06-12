---
title: "64bit Adobe Reader"
date: 2008-05-31
forum: General Help
---

### Post by satimis on 2008-05-31
Hi folks,


Ubuntu 7.10 desktop amd64


Where can I find 64bit Adobe Reader add-on for Firefox?  TIA


B.R.
satimis

---

### Post by quibbler on 2008-05-31
> **satimis said:**
> Hi folks,


Ubuntu 7.10 desktop amd64


Where can I find 64bit Adobe Reader add-on for Firefox?  TIA


B.R.
satimis

This may help you:

[http://ubuntuforums.org/showthread.php?t=679824](http://ubuntuforums.org/showthread.php?t=679824)

Regards quibbler

---

### Post by Nepherte on 2008-05-31
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by satimis on 2008-06-02
> **quibbler said:**
> This may help you:

[http://ubuntuforums.org/showthread.php?t=679824](http://ubuntuforums.org/showthread.php?t=679824)

Regards quibbler
Hi quibbler


Thanks for your URL


Following problem encountered on installing nspluginwrapper

$ sudo apt-get install nspluginwrapper```

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
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
                   Depends: lib32gcc1 (>= 1:4.2.1) but it is not going to be installed
E: Broken packages

```


Then;

$ sudo apt-get install ia32-libs```

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
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
E: Broken packages

```


Can't proceed further.  Any help?  TIA


B.R.
satimis

---

### Post by satimis on 2008-06-02
> **Nepherte said:**
> [http://www.medibuntu.org/](http://www.medibuntu.org/)
Hi Nepherte,


Thanks for your URL.


Performed following steps.


Download;
acroread_8.1.2-0medibuntu6_amd64.deb
acroread-escript_8.1.2-0medibuntu6_amd64.deb
acroread-plugins_8.1.2-0medibuntu6_amd64.deb

on /home/satimis/Acroread_download


$ cd Acroread_download/
:~/Acroread_download$ ls```

acroread_8.1.2-0medibuntu6_amd64.deb
acroread-escript_8.1.2-0medibuntu6_amd64.deb
acroread-plugins_8.1.2-0medibuntu6_amd64.deb

```


:~/Acroread_download$ sudo mkdir /opt/Acroread_8
:~/Acroread_download$ sudo cp acroread_8.1.2-0medibuntu6_amd64.deb /opt/Acroread_8/


$ cd /opt/Acroread_8/


:/opt/Acroread_8$ sudo dpkg -i acroread_8.1.2-0medibuntu6_amd64.deb ```

Selecting previously deselected package acroread.
(Reading database ... 92907 files and directories currently installed.)
Unpacking acroread (from acroread_8.1.2-0medibuntu6_amd64.deb) ...
dpkg: dependency problems prevent configuration of acroread:
 acroread depends on ia32-libs (>= 1.6); however:
  Package ia32-libs is not installed.
 acroread depends on lib32z1 (>= 1:1.2.3.3.dfsg-1); however:
  Package lib32z1 is not installed.
 acroread depends on libc6-i386 (>= 2.3.2); however:
  Package libc6-i386 is not installed.
 acroread depends on libldap-2.4-2; however:
  Package libldap-2.4-2 is not installed.
 acroread depends on libstdc++5; however:
  Package libstdc++5 is not installed.
dpkg: error processing acroread (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acroread

```
Still suffering dependencies problem.  Any suggesion?  TIA


B.R.
satimis

---

### Post by bapfreak on 2008-11-10
Download Adobe Reader deb from official website.

Then run:

sudo dpkg --force-all -i AdobeReader8.deb ( or whatever its called )

I am running Ubuntu Ibex x64 and I just did this two minutes ago.

Adobe Reader 8 works, the company just hasn't made an installer for
x64 yet.

---

