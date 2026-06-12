---
title: "packages have unmet dependencies"
date: 2016-09-09
forum: General Help
---

### Post by jakka_kiranraju on 2016-09-09
Hi,

I'm using ubuntu 14.04 LTS 64-bit OS Hardware: ThinkPad with i5 processor and 8Gb RAM.

I recently met below issue due to that i can't able to install even a single .deb or can't able to use apt-get update or apt-get upgrade. This is the error when i try to use update or upgrade at the console.

```
perl: Depends: perl-base (= 5.18.2-2ubuntu1.1) but 5.18.2-2ubuntu1.1 is installed
      Depends: perl-modules (>= 5.18.2-2ubuntu1.1) but 5.18.2-2ubuntu1 is installed
      Depends: zlib1g (>= 1:1.2.2.3) but 1:1.2.8.dfsg-1ubuntu1 is installed
```

anybody help me to get rid of it?

Thanks and Regards.

---

### Post by coffeecat on 2016-09-09
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by ajgreeny on 2016-09-09
Hi jakka_kiranraju, welcome to the forums.

Do you have any unusual repositories enabled that might have installed incompatible versions of other packages which may be causing this problem?
```
perl: Depends: perl-base (= [COLOR="#FF0000"]5.18.2-2ubuntu1.1[/COLOR]) but [COLOR="#FF0000"]5.18.2-2ubuntu1.1[/COLOR] is installed
Depends: perl-modules (>= [COLOR="#FF0000"]5.18.2-2ubuntu1.1[/COLOR]) but [COLOR="#FF0000"]5.18.2-2ubuntu1[/COLOR] is installed
Depends: zlib1g (>= 1:1.2.2.3) but 1:1.2.8.dfsg-1ubuntu1 is installed
```
Your terminal output seems a bit nonsensical in places as it complains about needing a version 5.18.2-2ubuntu1.1 that it then says is already installed., however your perl-modules is not quite up to date for some reason.

Please show us the output of terminal commands```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by #&amp;thj^% on 2016-09-09
EDIT: Did not see ajgreeny's reply before posting mine.
> **jakka_kiranraju said:**
> Hi,

I'm using ubuntu 14.04 LTS 64-bit OS Hardware: ThinkPad with i5 processor and 8Gb RAM.

I recently met below issue due to that i can't able to install even a single .deb or can't able to use apt-get update or apt-get upgrade. This is the error when i try to use update or upgrade at the console.

```
perl: Depends: perl-base (= 5.18.2-2ubuntu1.1) but 5.18.2-2ubuntu1.1 is installed
      Depends: perl-modules (>= 5.18.2-2ubuntu1.1) but 5.18.2-2ubuntu1 is installed
      Depends: zlib1g (>= 1:1.2.2.3) but 1:1.2.8.dfsg-1ubuntu1 is installed
```

anybody help me to get rid of it?

Thanks and Regards.
It would be extremely helpful for all us here to help you if you told us what you were doing or trying to install when this happened...
And maybe show us the output of 
```
sudo apt update
sudo apt upgrade
```
Pasting the return here in Code Tags.
Other wise we are just shooting in the dark.

---

### Post by jakka_kiranraju on 2016-09-09
Thanks for your concern::
Here is the output of "cat /etc/apt/sources.list"
```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
deb-src [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty main restricted #Added by software-properties


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty main restricted
deb-src [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty universe main multiverse #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates main restricted
deb-src [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates universe restricted main multiverse #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty universe
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty multiverse
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-security main restricted
deb-src [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-security universe restricted main multiverse #Added by software-properties
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-security universe
deb [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
```


and this was the output of  "ls /etc/apt/sources.list.d"
```
google-chrome.list       webupd8team-java-trusty.list       webupd8team-sublime-text-3-trusty.list
google-chrome.list.save  webupd8team-java-trusty.list.save  webupd8team-sublime-text-3-trusty.list.save
```

When i run sudo apt-get install <apache2 .... >

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dbconfig-common git-man javascript-common libaio1 libjs-codemirror
  libjs-jquery libjs-jquery-cookie libjs-jquery-event-drag
  libjs-jquery-metadata libjs-jquery-mousewheel libjs-jquery-tablesorter
  libjs-jquery-ui libjs-underscore librarian0 mysql-client-core-5.5
  mysql-server-core-5.5 php-gettext php5-cli php5-gd php5-readline
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-bin libarchive-extract-perl liblog-message-simple-perl
  libmodule-pluggable-perl libpod-latex-perl libterm-ui-perl
  libtext-soundex-perl perl perl-modules
Suggested packages:
  apache2-doc apache2-suexec-pristine apache2-suexec-custom perl-doc
  libterm-readline-gnu-perl libterm-readline-perl-perl libb-lint-perl
  libcpanplus-dist-build-perl libcpanplus-perl libfile-checktree-perl
  liblog-message-perl libobject-accessor-perl
The following NEW packages will be installed:
  apache2 apache2-bin libarchive-extract-perl liblog-message-simple-perl
  libmodule-pluggable-perl libpod-latex-perl libterm-ui-perl
  libtext-soundex-perl perl perl-modules
0 upgraded, 10 newly installed, 0 to remove and 583 not upgraded.
Need to get 2,673 kB/6,362 kB of archives.
After this operation, 38.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates/main perl-modules all 5.18.2-2ubuntu1.1 [2,673 kB]
Get:2 [http://free.nchc.org.tw/ubuntu/](http://free.nchc.org.tw/ubuntu/) trusty-updates/main perl-modules all 5.18.2-2ubuntu1.1 [2,673 kB]
Fetched 2,501 kB in 2min 6s (19.8 kB/s)   
E: Failed to fetch [http://free.nchc.org.tw/ubuntu/pool/main/p/perl/perl-modules_5.18.2-2ubuntu1.1_all.deb](http://free.nchc.org.tw/ubuntu/pool/main/p/perl/perl-modules_5.18.2-2ubuntu1.1_all.deb)  Hash Sum mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by #&amp;thj^% on 2016-09-09
You may want to try a different software server.
But this usually fixes things..

```
sudo rm -rf /var/lib/apt/lists/partial/*
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo mkdir ~/sources.list.d && sudo mv /etc/apt/sources.list.d/* ~/sources.list.d/
sudo sed -i s'/us.//g' /etc/apt/sources.list
sudo apt-get update
```
That will put you on a US server to see if that helps with the "Hash Sum mismatch"

---

### Post by jakka_kiranraju on 2016-09-09
When i run all above commands and finally i run update command the output of update command look like below::::

```
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try InRelease
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates InRelease                         
Ign [http://archive.canonical.com](http://archive.canonical.com) try InRelease                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) try InRelease     
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) try Release.gpg
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try Release.gpg    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) try Release.gpg   
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) try Release   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) try Release       
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security Release.gpg
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try Release        
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates Release
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security Release
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) try/main Sources                        
  404  Not Found [IP: 91.189.92.152 80]
Err [http://archive.canonical.com](http://archive.canonical.com) try/partner Sources                 
  404  Not Found [IP: 91.189.92.150 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) try/main amd64 Packages
  404  Not Found [IP: 91.189.92.152 80]
Err [http://archive.canonical.com](http://archive.canonical.com) try/partner amd64 Packages
  404  Not Found [IP: 91.189.92.150 80]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) try/main i386 Packages
  404  Not Found [IP: 91.189.92.152 80]
Err [http://archive.canonical.com](http://archive.canonical.com) try/partner i386 Packages
  404  Not Found [IP: 91.189.92.150 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) try/main Translation-en_IN
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) try/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) try/partner Translation-en_IN
Ign [http://archive.canonical.com](http://archive.canonical.com) try/partner Translation-en
24% [Waiting for headers]


Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/main Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/restricted Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/universe Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/multiverse Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/main amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/restricted amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/universe amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/multiverse amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/main Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/multiverse Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/restricted Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/universe Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try/universe Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/universe Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/restricted Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/main Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/multiverse Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/main amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/restricted amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/universe amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/multiverse amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/main Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/multiverse Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/restricted Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/universe Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-updates/universe Translation-en
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/universe Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/restricted Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/main Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/multiverse Sources
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/main amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/restricted amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/universe amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/multiverse amd64 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/main i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/restricted i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/universe i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Err [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/multiverse i386 Packages
  404  Not Found [IP: 211.73.64.9 80]
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/main Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/main Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/multiverse Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/multiverse Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/restricted Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/restricted Translation-en
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/universe Translation-en_IN
Ign [http://free.nchc.org.tw](http://free.nchc.org.tw) try-security/universe Translation-en
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/try/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/try/partner/source/Sources)  404  Not Found [IP: 91.189.92.150 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/try/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/try/partner/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.150 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/try/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/try/partner/binary-i386/Packages)  404  Not Found [IP: 91.189.92.150 80]


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/try/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/try/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/try/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/try/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.152 80]


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/try/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/try/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.152 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/main/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try/main/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/restricted/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try/restricted/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/universe/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try/universe/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/multiverse/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try/multiverse/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/main/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try/main/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/restricted/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try/restricted/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/universe/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try/universe/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/multiverse/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try/multiverse/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/main/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-updates/main/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/main/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/main/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/universe/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-security/universe/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/main/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-security/main/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/source/Sources](http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/source/Sources)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/main/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/main/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/universe/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/universe/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/binary-amd64/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/main/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/main/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/restricted/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/universe/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/universe/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


W: Failed to fetch [http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/binary-i386/Packages](http://free.nchc.org.tw/ubuntu/dists/try-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 211.73.64.9 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by jakka_kiranraju on 2016-09-09
@1fallen What will be the rollback for above change?

---

### Post by deadflowr on 2016-09-09
Please use code tags when posting terminal output.
See: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by jakka_kiranraju on 2016-09-09
Thanks 

K I'll follow the code tag from now. I'm new to this forum.

---

### Post by #&amp;thj^% on 2016-09-10
> **jakka_kiranraju said:**
> @1fallen What will be the rollback for above change?

This command should do the trick

```
sudo sed -i 's/http:\/\/us./http:\/\//g' /etc/apt/sources.list
```

It will remove the 'us.' prefix in each of the addresses to convert them to addresses of the main server.

**Note: Of course replace 'us' by any other mirror you are using.**

---

