---
title: "Software Update fails - Unable to find expected entry"
date: 2014-07-27
forum: General Help
---

### Post by hari6 on 2014-07-27
Hey guys.

I recently installed Xubuntu 14.04 on my laptop and things were going good, I was able to install all codecs and commonly required stuff with ease. I wanted to install Skype and reading on one of the forums, I came to know that we should add support i386 packages in dpkg.(My bad, 'cause apparently that was needed only for earlier versions such as 12.04)

So anyways I followed that instruction and typed:

sudo dpkg --add-architecture i386

Then i tried installing Skype through the .deb file I downloaded but since it didn't meet the dependencies it wasn't installed properly. So i removed it normally using "sudo apt-get remove skype"

After that I tried updating by "apt-get update" and I got the following:
```

hari@hari-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get update
[sudo] password for hari: 
Ign http://mirror.nus.edu.sg trusty InRelease
Ign http://mirror.nus.edu.sg trusty-updates InRelease
Ign http://mirror.nus.edu.sg trusty-backports InRelease
Ign http://mirror.nus.edu.sg trusty-security InRelease
Hit http://mirror.nus.edu.sg trusty Release.gpg
Hit http://mirror.nus.edu.sg trusty-updates Release.gpg
Hit http://mirror.nus.edu.sg trusty-backports Release.gpg
Hit http://mirror.nus.edu.sg trusty-security Release.gpg
Hit http://mirror.nus.edu.sg trusty Release
Hit http://mirror.nus.edu.sg trusty-updates Release
Hit http://mirror.nus.edu.sg trusty-backports Release
Hit http://mirror.nus.edu.sg trusty-security Release
Hit http://mirror.nus.edu.sg trusty/main Sources
Hit http://mirror.nus.edu.sg trusty/restricted Sources
Hit http://mirror.nus.edu.sg trusty/universe Sources
Hit http://mirror.nus.edu.sg trusty/multiverse Sources
Hit http://mirror.nus.edu.sg trusty/main amd64 Packages
Hit http://mirror.nus.edu.sg trusty/restricted amd64 Packages
Hit http://mirror.nus.edu.sg trusty/universe amd64 Packages
Hit http://mirror.nus.edu.sg trusty/multiverse amd64 Packages
Hit http://mirror.nus.edu.sg trusty-updates/main Sources
Hit http://mirror.nus.edu.sg trusty-updates/restricted Sources
Hit http://mirror.nus.edu.sg trusty-updates/universe Sources
Hit http://mirror.nus.edu.sg trusty-updates/multiverse Sources
Hit http://mirror.nus.edu.sg trusty-updates/main amd64 Packages
Hit http://mirror.nus.edu.sg trusty-updates/restricted amd64 Packages
Hit http://mirror.nus.edu.sg trusty-updates/universe amd64 Packages
Hit http://mirror.nus.edu.sg trusty-updates/multiverse amd64 Packages
Hit http://mirror.nus.edu.sg trusty-backports/main Sources
Hit http://mirror.nus.edu.sg trusty-backports/restricted Sources
Hit http://mirror.nus.edu.sg trusty-backports/universe Sources
Hit http://mirror.nus.edu.sg trusty-backports/multiverse Sources
Hit http://mirror.nus.edu.sg trusty-backports/main amd64 Packages
Hit http://mirror.nus.edu.sg trusty-backports/restricted amd64 Packages
Hit http://mirror.nus.edu.sg trusty-backports/universe amd64 Packages
Hit http://mirror.nus.edu.sg trusty-backports/multiverse amd64 Packages
Hit http://mirror.nus.edu.sg trusty-security/main Sources
Hit http://mirror.nus.edu.sg trusty-security/restricted Sources
Hit http://mirror.nus.edu.sg trusty-security/universe Sources
Hit http://mirror.nus.edu.sg trusty-security/multiverse Sources
Hit http://mirror.nus.edu.sg trusty-security/main amd64 Packages
Hit http://mirror.nus.edu.sg trusty-security/restricted amd64 Packages
Hit http://mirror.nus.edu.sg trusty-security/universe amd64 Packages
Hit http://mirror.nus.edu.sg trusty-security/multiverse amd64 Packages
W: Failed to fetch http://mirror.nus.edu.sg/ubuntu/dists/trusty/Release  Unable to find expected entry 'main/binary-i386sudo/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.nus.edu.sg/ubuntu/dists/trusty-updates/Release  Unable to find expected entry 'main/binary-i386sudo/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.nus.edu.sg/ubuntu/dists/trusty-backports/Release  Unable to find expected entry 'main/binary-i386sudo/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.nus.edu.sg/ubuntu/dists/trusty-security/Release  Unable to find expected entry 'main/binary-i386sudo/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I searched in the forums and came across many suggestions:

1. I tried removing the architecture i386 and tried again but got the same message.

2. I used this command: dpkg -l | grep i386 to see all such packages

```

hari@hari-HP-Pavilion-dv6-Notebook-PC:~$ sudo dpkg -l | grep i386
rc  skype                                       4.3.0.37-1                                 i386         Wherever you are, wherever they are

```

This is weird because i thought i uninstalled it.

3. I also tried looking up sources.list, this is the content:

```

# deb cdrom:[Xubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.nus.edu.sg/ubuntu/ trusty main restricted
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.nus.edu.sg/ubuntu/ trusty-updates main restricted
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.nus.edu.sg/ubuntu/ trusty universe
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty universe
deb http://mirror.nus.edu.sg/ubuntu/ trusty-updates universe
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.nus.edu.sg/ubuntu/ trusty multiverse
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty multiverse
deb http://mirror.nus.edu.sg/ubuntu/ trusty-updates multiverse
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.nus.edu.sg/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-backports main restricted universe multiverse

deb http://mirror.nus.edu.sg/ubuntu/ trusty-security main restricted
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-security main restricted
deb http://mirror.nus.edu.sg/ubuntu/ trusty-security universe
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-security universe
deb http://mirror.nus.edu.sg/ubuntu/ trusty-security multiverse
deb-src http://mirror.nus.edu.sg/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main                                 # I tried commenting these lines here but no use.
deb-src http://extras.ubuntu.com/ubuntu trusty main

```
 
4. I checked source.list.d/ folder as well but no files there.

While it's not an earth shattering problem, I still feel annoyed by it.

Hope this info helps.

Any information that helps would be appreciated. Thanks.

---

### Post by steeldriver on 2014-07-27
I suspect the rogue entry is in a separate file inside /etc/apt/sources.list.d/ - try

```

ls /etc/apt/sources.list.d/

grep 'sudo' /etc/apt/sources.list.d/*

```

and post back what you find

---

### Post by kc1di on 2014-07-27
[this page's]("http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html") instructions worked fine for me.  give it a try.
I also run Xubuntu 14.04

---

### Post by hari6 on 2014-07-27
I didn't find any files under /etc/apt/sources.list.d/ ...are they hidden?

Also i no longer require to install Skype... I just want to know if updater will fail since it's not getting certain packages under i386sudo

---

### Post by steeldriver on 2014-07-27
I don't think there is a directory called 'main/binary-i386**sudo**/Packages' - it's most likely a typo for just 'main/**binary-i386**/Packages' (perhaps you tried to *use* sudo to modify the sources.list, and made a mistake in the command?)

---

### Post by hari6 on 2014-07-27
Ok guys...I found the problem. I had accidentally checked "Software restricted by Copyright or Legal issues" under Software Sources. Now "apt-get update" works fine.

---

### Post by kc1di on 2014-07-27
Glad you found it , did you get skype to work for you?

---

### Post by hari6 on 2014-07-27
> **kc1di said:**
> Glad you found it , did you get skype to work for you?

Well, Skype is still problematic. While i added the Canonical partner repo and tried installing i get a message:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin but it is not installable
E: Unable to correct problems, you have held broken packages.

```

I'll try snooping around some more. (I tried "--fix-missing" and "-f install", didn't work though)

---

### Post by kc1di on 2014-07-28
Again the method on [this page worked]("http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html") well for me.

---

### Post by hari6 on 2014-07-29
> **kc1di said:**
> Again the method on [this page worked]("http://www.noobslab.com/2014/01/skype-released-new-version-install-in.html") well for me.

I tried it. Gives the same error.

---

### Post by kc1di on 2014-07-29
you may need to uninstall the one you originally installed,  
```
sudo apt-get purge skype
```

then try the web page method again.

---

