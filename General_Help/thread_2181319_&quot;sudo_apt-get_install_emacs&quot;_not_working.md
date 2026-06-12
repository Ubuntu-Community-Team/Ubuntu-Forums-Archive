---
title: "&quot;sudo apt-get install emacs&quot; not working"
date: 2013-10-17
forum: General Help
---

### Post by Frank_Friedman on 2013-10-17
Hello, 

I am trying to install emacs on my ubuntu server (12.04, 64-bit ser) but am having major problems.  (It seems that apt-get will not install anything).  Here is what happens when I try to install emacs:

> sudo apt-get install emacs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package emacs

I tried emacs24, Emacs, Emacs24, emacs22, emacs23... nothing works.

Before I go any further, here is my /etc/lsb-relase file:
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

Reading forums and googling to fix the problem, I tried (and receive) this:
> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


The next thing to try was to do an update (I am on 12.04.2).  And I get this:
> sudo apt-get update
[sudo] password for friedman:
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
 
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving '[security.ubuntu.com]("http://security.ubuntu.com")'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise/InRelease)
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/InRelease)
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/InRelease)
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease)
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving '[security.ubuntu.com]("http://security.ubuntu.com")'
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Temporary failure resolving '[us.archive.ubuntu.com]("http://us.archive.ubuntu.com")'
 
W: Some index files failed to download. They have been ignored, or old ones used instead.




my sources.list file looks like this:
> # deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ precise main restricted
#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130214)]/ precise main restricted
 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
 
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
 
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main




I just want to install emacs... and eventually other packages.  Any help, suggestions, hints, ideas, etc... would be greatly appreciated!

Thanks,
Frank

---

### Post by Dave_L on 2013-10-17
It might just be a temporary internet problem, which will resolve itself.

Here are some more suggestions: [http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error](http://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error)

I'm using 12.04.3, and also use emacs.

---

### Post by Lars Noodén on 2013-10-17
There are also several packages to choose from, but none named just "emacs" you have to choose "emacs24" or "emacs24-nox" for example.  I choose the latter.

---

### Post by buzzingrobot on 2013-10-17
Here's a link to where you can search for specific packages available in each Ubuntu release:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

I'd agree that you were probably hitting some of the servers at a bad time.  Today is release day for 13.10, and the primary U.S. servers are going to be hammered.

---

### Post by Lars Noodén on 2013-10-17
Now might be a good time to test the package "apt-p2p" to see if it can avoid some of the server congestion we'll see for the coming day or so.

---

### Post by philinux on 2013-10-17
In precise it's just emacs. I agree with others though the servers may be hard pressed with 13.10 out.

[http://packages.ubuntu.com/precise/emacs](http://packages.ubuntu.com/precise/emacs)

---

### Post by Dave_L on 2013-10-17
> **Lars Noodén said:**
> There are also several packages to choose from, but none named just "emacs" you have to choose "emacs24" or "emacs24-nox" for example.  I choose the latter.

Actually "emacs" is a package. Its description in synaptic is:

> The GNU Emacs editor (metapackage) 
 
GNU Emacs is the extensible self-documenting text editor.
This is a metapackage which will always depend on the latest Emacs
release.

[http://packages.ubuntu.com/search?keywords=emacs&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=emacs&searchon=names&suite=all&section=all)

There's also this PPA with possibly newer versions (but they might be less stable than the default version): [https://launchpad.net/~cassou/+archive/emacs](https://launchpad.net/~cassou/+archive/emacs)

---

### Post by Lars Noodén on 2013-10-17
> **Dave_L said:**
> Actually "emacs" is a package. Its description in synaptic is:

It appears to be a version dependent naming system.  In 13.10, there is no "emacs" but v23 and v24 to choose from.

---

