---
title: "major synaptic/add/remove error (gutsy) advice please"
date: 2008-04-11
forum: General Help
---

### Post by lycaenops on 2008-04-11
Hi,

long post, I'm afraid. All advice appreciated... thanks.

I tried to install adobe reader following the instructions on this page:
[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html#comment-76277]("http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html#comment-76277")
All commands were copy/pasted to avoid user error, nevertheless all did *not* go to plan...
Here is my terminal readout for the experience:

> lemony@lemony-biscuits:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
[sudo] password for lemony:
OK
lemony@lemony-biscuits:~$ sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
--20:37:09--  [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving medibuntu.sos-sts.com... 82.165.117.31
Connecting to medibuntu.sos-sts.com|82.165.117.31|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.medibuntu.org](http://www.medibuntu.org) [following]
--20:37:09--  [http://www.medibuntu.org/](http://www.medibuntu.org/)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,485 (5.4K) [text/html]

100%[====================================>] 5,485         --.--K/s             

20:37:10 (174.52 KB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [5485/5485]

lemony@lemony-biscuits:~$ sudo apt-get update
E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
lemony@lemony-biscuits:~$ sudo apt-get install acroread mozilla-acroread acroread-plugins
E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
lemony@lemony-biscuits:~$ sudo apt-get install acroread mozilla-acroread acroread-plugins 
E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
lemony@lemony-biscuits:~$ sudo apt-get install -f'
> sudo apt-get install -f
> sudo apt-get install update


So... no adobe reader, no medibuntu... oh well. Let's go to add/remove to see if I can get it that way, then...
Neither add/remove nor synaptic would open, citing the following error:

> Failed to check for installed and available applications.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and corrections of the file '/etc/apt/sources list' and reload the software list information with 'sudo apt-get update' and 'sudo apt-get install -f'.

If anyone knows what I should do next, please share advice or link[s] to same. Cheers all.:popcorn:

---

### Post by wannadumpwindows on 2008-04-11
Post the contents of:

```
sudo gedit /etc/apt/sources.list
```

And we can help you more from there!

---

### Post by lycaenops on 2008-04-12
OK, here's the lot:
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Thank you muchly:)

---

### Post by plucky on 2008-04-12
> E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list


The error **!DOCTYPE’** is located in **medibuntu.list** on line 1 of that file.Anyhow you have added the medibuntu repository for Feisty instead of Gutsy.
To fix the problem, open a terminal and ```
cd /etc/apt/sources.list.d
```
Then ```
ls -l
``` to make sure you are in the right directory. You should see **medibuntu.list**

Delete it with ```
rm -i medibuntu.list
```

To add medibuntu for Gutsy use in a terminal window ```
 sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

and for the key ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

You should be good to go

Good Luck

---

### Post by lycaenops on 2008-04-14
Thanks so much, especially for explaining what the problem was.:KS Much appreciated. I'll sort it out later - not been well hence late thank - and then mark the thread as solved as soon as I work out how to.:)

---

