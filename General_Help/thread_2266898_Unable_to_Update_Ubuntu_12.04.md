---
title: "Unable to Update Ubuntu 12.04"
date: 2015-02-26
forum: General Help
---

### Post by bte_rajan on 2015-02-26
Hello All, 

I am unable to update ubuntu when I run **sudo apt-get update && sudo apt-get upgrade**

I am getting following error 

W: GPG error: [http://download.opensuse.org](http://download.opensuse.org)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EF2666A18CEC0F6
W: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/libreoffice/libreoffice-4-4/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Thank you in advance

---

### Post by Bucky Ball on 2015-02-26
*Thread moved to **General Help**.*

There are problems with the repos and PPAs you have added manually. Go to Software Sources and disable them. The three Libreoffice PPAs don't appear to exist. You don't need the sources PPA unless you are a developer or want to see the source code, and not sure why you've added the amd64 PPA AND the i386 PPA.

Unsure why you have an opensuse repo in Ubuntu. 

Best to install things from the official Ubuntu repos (Software Centre or Synpatics) unless you have a good reason to add PPAs manually. ;)

---

### Post by bte_rajan on 2015-02-26
Thank you for reply. I am new in Ubuntu, Can you please tell me how can I disable repos and PPAs using Software Sources, Is there any terminal command to do it

---

### Post by Bucky Ball on 2015-02-26
In your Software Sources, you should see every repo/PPA you have installed. Should be in the 'Other Software' tab. Just untick them.

For the terminal:

```
sudo nano /etc/apt/sources.list
```

Find the offending sources, e.g. the four that are causing problems that you list in your first post (the opensuse one and the three Libreoffice PPAs), and place a # in front of them, or delete them if you don't want/use them. They will contain the same text as the ones you posted, but with a deb in front. Just look for any with the same text. 

For instance, to prevent this repo from being used:

```
deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) saucy main restricted
```

You would make it:

```
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) saucy main restricted
```

See [this]("https://help.ubuntu.com/community/Repositories/CommandLine") page for the basics.

---

### Post by bte_rajan on 2015-02-26
I could not find any thing related to opensuse or Libreoffice PPAs. Here are the outcome of sources.list (sudo gedit /etc/apt/sources.list)

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
```

Thanks

---

### Post by plucky on 2015-02-26
> I could not find any thing related to opensuse or Libreoffice PPAs. Here are the outcome of sources.list (sudo gedit /etc/apt/sources.list)



PPAs are stored in /etc/apt/sources.list.d directory.

From a terminal ```
ls -l /etc/apt/sources.list.d/*
``` should show you what ppas are installed.

Disable the ones that are causing the problem as shown by Bucky Ball

Good Luck

---

### Post by Bucky Ball on 2015-02-26
Thanks plucky. My mistake. That lengthy bike ride must have scrambled my brain. ;)

@bte_rajan: Please use [code] tags for terminal output. See the last link in my signature for how. I've added them to your last output.

---

### Post by bte_rajan on 2015-02-26
Thanks a lot for your support @plucky and **@**Bucky ball. The problem is solved now. Thanks again

---

### Post by Bucky Ball on 2015-02-26
Good news. ;)

If you're looking to install something, check the official repos first (Software Centre/Synapics) before thinking about installing third-party PPAs. Safer that way. Good luck.

---

