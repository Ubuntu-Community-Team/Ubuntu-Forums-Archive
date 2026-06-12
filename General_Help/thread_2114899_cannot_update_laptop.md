---
title: "cannot update laptop"
date: 2013-02-11
forum: General Help
---

### Post by jlh68 on 2013-02-11
I get the folloing messages: the attached image and the below quote.


> Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.

I was only trying to UPDATE my system not do a partial Upgrade if that measns to go to another version of the OS.

In any case I can not update my system.

---

### Post by ibjsb4 on 2013-02-11
You do not have a meta-package installed.  Did you remove it for a reason?  If not, just install it.

---

### Post by jlh68 on 2013-02-11
Synaptic shows that ubuntu-desktop is installed, and I reinstalled it and I still ge the message that ubuntu-desktop is not installed.

What else should I be looking for in Synaptic or other wise?

---

### Post by tgalati4 on 2013-02-11
Open a terminal:

```
sudo apt-get check
```

C64 was my first computer.

---

### Post by jlh68 on 2013-02-12
Here is result of the apt-get check command:

> john@Nighthawk:~$ sudo apt-get check
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
john@Nighthawk:~$ 

To me it does not show me much to go on.

---

### Post by ibjsb4 on 2013-02-12
If this is just a matter of a partial upgrade, I think I  would just wait it out.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

Does a terminal update tell you anything different?

```
sudo apt-get update
```

---

### Post by jlh68 on 2013-02-12
I tried to reinstal ubuntu-desktop and got the following message:

> W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/main amd64 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/contrib amd64 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/non-free amd64 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/main i386 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/contrib i386 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.debian.org/](http://security.debian.org/) squeeze/updates/non-free i386 Packages (/var/lib/apt/lists/security.debian.org_dists_squeeze_updates_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) squeeze/main amd64 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_squeeze_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) squeeze/non-free amd64 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_squeeze_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) squeeze/main i386 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_squeeze_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.deb-multimedia.org/](http://www.deb-multimedia.org/) squeeze/non-free i386 Packages (/var/lib/apt/lists/www.deb-multimedia.org_dists_squeeze_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/contrib amd64 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/non-free amd64 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/main amd64 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/contrib i386 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/non-free i386 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates/main i386 Packages (/var/lib/apt/lists/ftp.us.debian.org_debian_dists_squeeze-proposed-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/main amd64 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/contrib amd64 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_contrib_binary-amd64_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/non-free amd64 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/main i386 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/contrib i386 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_contrib_binary-i386_Packages)
W: Duplicate sources.list entry [http://backports.debian.org/debian-backports/](http://backports.debian.org/debian-backports/) squeeze-backports/non-free i386 Packages (/var/lib/apt/lists/backports.debian.org_debian-backports_dists_squeeze-backports_non-free_binary-i386_Packages)
W: Duplicate sources.list entry [http://mozilla.debian.net/](http://mozilla.debian.net/) squeeze-backports/iceweasel-release amd64 Packages (/var/lib/apt/lists/mozilla.debian.net_dists_squeeze-backports_iceweasel-release_binary-amd64_Packages)
W: Duplicate sources.list entry [http://mozilla.debian.net/](http://mozilla.debian.net/) squeeze-backports/iceweasel-release i386 Packages (/var/lib/apt/lists/mozilla.debian.net_dists_squeeze-backports_iceweasel-release_binary-i386_Packages)


What is the significance of this?

---

### Post by jlh68 on 2013-02-12
It looks like I have some duplicate sources in the /var/lib/apt/lists/partial file.

How do I remove the doulble listed sources?  Or should the whole /partial file folder be removed?

---

### Post by ibjsb4 on 2013-02-12
That list  says your running debian and not ubuntu.  Whats with that?

Whats in your sources list?  In terminal:

```
cat /etc/apt/sources.list
```

---

### Post by jlh68 on 2013-02-12
here is my sources list.  Next question is how did I get to debian from Ubuntu and how do I get it back to Ubuntu?

> john@Nighthawk:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

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

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main contrib non-free #deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free
# deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free

deb [http://www.deb-multimedia.org](http://www.deb-multimedia.org) squeeze main non-free

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates contrib non-free main

deb [http://backports.debian.org/debian-backports](http://backports.debian.org/debian-backports) squeeze-backports main contrib non-free

deb [http://mozilla.debian.net/](http://mozilla.debian.net/) squeeze-backports iceweasel-release
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main contrib non-free #deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze main contrib non-free

deb [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free
# deb-src [http://security.debian.org/](http://security.debian.org/) squeeze/updates main contrib non-free

deb [http://www.deb-multimedia.org](http://www.deb-multimedia.org) squeeze main non-free

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) squeeze-proposed-updates contrib non-free main

deb [http://backports.debian.org/debian-backports](http://backports.debian.org/debian-backports) squeeze-backports main contrib non-free

deb [http://mozilla.debian.net/](http://mozilla.debian.net/) squeeze-backports iceweasel-release
john@Nighthawk:~$ 


---

### Post by ibjsb4 on 2013-02-12
I really don't know if debian and ubuntu can be mixed like this, never tried it.  So my best idea is to remove all debian/squeeze sources.

Or easier, just comment(#)them out.  You can do this with gedit.

In terminal:

```
gksudo gedit /etc/apt/sources.list
```

Example of last line:

#deb [http://mozilla.debian.net/](http://mozilla.debian.net/) squeeze-backports iceweasel-release

---

### Post by jlh68 on 2013-02-12
I commented out all the deb line in the sources.list and that corrected the problem.  I was able to a normal Ubuntu type update.
My computer is back to "normal"

**ibjsb4**  thanks for your help in guiding me through the getting the problem removed.

---

### Post by ibjsb4 on 2013-02-12
Welcome  :)

One last thing

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

