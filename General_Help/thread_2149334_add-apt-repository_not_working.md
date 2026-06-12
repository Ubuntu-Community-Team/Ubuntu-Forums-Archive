---
title: "add-apt-repository not working"
date: 2013-05-28
forum: General Help
---

### Post by cdoshi on 2013-05-28
trying to add ppa: sudo add-apt-repository ppa:webupd8team/y-ppa-manager.
I get a similar error, actually I got the same error then after installing pycurl I get this error:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.3/urllib/request.py", line 148, in urlopen
    context.load_verify_locations(cafile, capath)
ssl.SSLError: [X509] PEM lib (_ssl.c:2158)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 54, in body_callback
    self.contents = self.contents + buf
TypeError: Can't convert 'bytes' object to str implicitly
Cannot access PPA ([https://launchpad.net/api/1.0/~webupd8team/+archive/y-ppa-manager](https://launchpad.net/api/1.0/~webupd8team/+archive/y-ppa-manager)) to get PPA information, please check your internet connection.

---

### Post by oldos2er on 2013-05-28
Post moved to its own thread.

---

### Post by Frogs Hair on 2013-05-28
Hello and Welcome

I just installed the package on 13.04 . What is your Ubuntu version ?

---

### Post by cdoshi on 2013-05-29
I tried to add a few repositories and at first  [I]got this error:

[/I][I]ImportError: No module named 'pycurl'


[/I]fixed that from this post: [http://ubuntuforums.org/showthread.php?t=2143067]("http://ubuntuforums.org/showthread.php?t=2143067but") but now i get the following error on "sudo add-apt-repository ppa:webupd8team/y-ppa-manager" :

[I]Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.3/urllib/request.py", line 148, in urlopen
    context.load_verify_locations(cafile, capath)
ssl.SSLError: [X509] PEM lib (_ssl.c:2158)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 54, in body_callback
    self.contents = self.contents + buf
TypeError: Can't convert 'bytes' object to str implicitly
Cannot access PPA ([https://launchpad.net/api/1.0/~webupd8team/+archive/y-ppa-manager](https://launchpad.net/api/1.0/~webupd8team/+archive/y-ppa-manager)) to get PPA information, please check your internet connection.

[/I]Any idea how to fix this?

---

### Post by cdoshi on 2013-05-29
Thanks, my version is ubuntu 13.04 as well.

---

### Post by dino99 on 2013-05-29
before tweaking everything on the early days, maybe should you take some time to learn how linux works. Ubuntu suppose you understand what you are doing; and if you dont, then dont do scary things.

there is enough packages/apps installed by default; why do you want to install pycurl for ? (aka python-pycurl)
[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

---

### Post by cdoshi on 2013-05-29
Thank dino for your reply, I have been using ubuntu for a while now. I just upgraded from 12.04 to 12.10 and then to the new 13.04.
I wanted to actually install the rabbitvcs repository. (sudo add-apt-repository ppa:rabbitvcs/ppa)
But adding any repository gave me the errors as described above. 
I got this error first and fixed it with the link in my post.
[I]ImportError: No module named 'pycurl'
[/I]Now I get the second error. so I am asking for assistance to sort it. Thanx.

---

### Post by oldos2er on 2013-05-29
Threads merged. Please don't open more than one thread for the same or similar questions, it dilutes community effort and is confusing.

---

### Post by Frogs Hair on 2013-05-29
If those were all upgrades you may want take a look at your sources list and check for sources from previous Ubuntu versions versions and old PPAs . I installed the PPA manager to see if it would install properly, but the application does nothing that is not already possible other than combining different operations in one GUI   .  

```
 grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by cdoshi on 2013-05-30
Sorry about that Ann, I had not realized my initial post was moved into a new thread. Wont happen again. :)

---

### Post by cdoshi on 2013-05-30
Thanks Frogs Hair, 
I managed to add the rabbit vcs from the software & updates, which I really needed.
here is the list of the source list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list:## repository.
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:# deb [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
/etc/apt/sources.list:# deb-src [http://ke.archive.ubuntu.com/ubuntu/](http://ke.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports restricted main multiverse universe
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
/etc/apt/sources.list:deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) raring main
/etc/apt/sources.list:deb-src [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) raring main
/etc/apt/sources.list.d/claudiocn-slm-oneiric.list.distUpgrade:deb [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) oneiric main
/etc/apt/sources.list.d/claudiocn-slm-oneiric.list.distUpgrade:deb-src [http://ppa.launchpad.net/claudiocn/slm/ubuntu](http://ppa.launchpad.net/claudiocn/slm/ubuntu) oneiric main
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/gwibber-daily-ppa-natty.list.distUpgrade:deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main
/etc/apt/sources.list.d/gwibber-daily-ppa-natty.list.distUpgrade:deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) natty main
/etc/apt/sources.list.d/medibuntu.list:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/medibuntu.list.save:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/mozillateam-thunderbird-stable-natty.list.distUpgrade:# deb [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/mozillateam-thunderbird-stable-natty.list.distUpgrade:# deb-src [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/ondrej-php5-oneiric.list.distUpgrade:deb [http://ppa.launchpad.net/ondrej/php5/ubuntu](http://ppa.launchpad.net/ondrej/php5/ubuntu) oneiric main
/etc/apt/sources.list.d/ondrej-php5-oneiric.list.distUpgrade:deb-src [http://ppa.launchpad.net/ondrej/php5/ubuntu](http://ppa.launchpad.net/ondrej/php5/ubuntu) oneiric main
/etc/apt/sources.list.d/ondrej-php5-precise.list.distUpgrade:# deb [http://ppa.launchpad.net/ondrej/php5/ubuntu](http://ppa.launchpad.net/ondrej/php5/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/ondrej-php5-precise.list.distUpgrade:# deb-src [http://ppa.launchpad.net/ondrej/php5/ubuntu](http://ppa.launchpad.net/ondrej/php5/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/rabbitvcs-ppa-natty.list.distUpgrade:deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) natty main
/etc/apt/sources.list.d/rabbitvcs-ppa-natty.list.distUpgrade:deb-src [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) natty main
/etc/apt/sources.list.d/rabbitvcs-ppa-oneiric.list.distUpgrade:deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) natty main
/etc/apt/sources.list.d/rabbitvcs-ppa-oneiric.list.distUpgrade:deb-src [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) natty main
/etc/apt/sources.list.d/rabbitvcs-ppa-precise.list.distUpgrade:deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/rabbitvcs-ppa-precise.list.distUpgrade:deb-src [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/screenlets-ppa-natty.list.distUpgrade:deb [http://ppa.launchpad.net/screenlets/ppa/ubuntu](http://ppa.launchpad.net/screenlets/ppa/ubuntu) natty main
/etc/apt/sources.list.d/screenlets-ppa-natty.list.distUpgrade:deb-src [http://ppa.launchpad.net/screenlets/ppa/ubuntu](http://ppa.launchpad.net/screenlets/ppa/ubuntu) natty main
/etc/apt/sources.list.d/shutter-ppa-precise.list:# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/shutter-ppa-precise.list:# deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/shutter-ppa-precise.list.distUpgrade:# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/shutter-ppa-precise.list.distUpgrade:# deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/shutter-ppa-precise.list.save:# deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/shutter-ppa-precise.list.save:# deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) quantal main # disabled on upgrade to quantal
/etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list.distUpgrade:# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list.distUpgrade:# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/webupd8team-sublime-text-2-oneiric.list.distUpgrade:# deb [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) quantal main # disabled on upgrade to precise disabled on upgrade to quantal
/etc/apt/sources.list.d/webupd8team-sublime-text-2-oneiric.list.distUpgrade:# deb-src [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) quantal main # disabled on upgrade to precise disabled on upgrade to quantal


what I dont understand it any package I try to add fails:

sudo add-apt-repository ppa:webupd8team/sublime-text-2
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 98, in get_ppa_info_from_lp
    lp_page = urllib.request.urlopen(request, cafile=LAUNCHPAD_PPA_CERT)
  File "/usr/lib/python3.3/urllib/request.py", line 148, in urlopen
    context.load_verify_locations(cafile, capath)
ssl.SSLError: [X509] PEM lib (_ssl.c:2158)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 54, in body_callback
    self.contents = self.contents + buf
TypeError: Can't convert 'bytes' object to str implicitly
Cannot access PPA ([https://launchpad.net/api/1.0/~webupd8team/+archive/sublime-text-2](https://launchpad.net/api/1.0/~webupd8team/+archive/sublime-text-2)) to get PPA information, please check your internet connection.

---

### Post by Frogs Hair on 2013-05-30
You have both  PPA and Official sources  for 11.04 and 11.10 in the output that shouldn't be there. You may need to purge any unsupported PPAs manually and remove the sources sources from Software & Updates > Other Software.  The synaptic package manager may be helpful if you are able to install it. The PPA Purge won't help if you can't add the repository.

The sources were disabled during the upgrade/s, but may want to remove any unneeded packages run the following .

```
sudo apt-get autoremove
```

```
suso apt-get update
```

---

### Post by cdoshi on 2013-05-31
Thanks Frog Hair,
I cleaned out the source list, did the autoremove but still no luck:

grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:
/etc/apt/sources.list:# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from the 'backports'
/etc/apt/sources.list:## repository.
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-security main restricted
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-security restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-security universe
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-backports restricted main multiverse universe
/etc/apt/sources.list:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-backports restricted main multiverse universe #Added by software-properties
/etc/apt/sources.list:# deb [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/](http://archive.canonical.com/) raring partner
/etc/apt/sources.list:deb [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) raring main
/etc/apt/sources.list:deb-src [http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu](http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu) raring main
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
/etc/apt/sources.list.d/medibuntu.list:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/medibuntu.list.distUpgrade:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/medibuntu.list.save:## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list:deb [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list:deb-src [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list.save:deb [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) raring main
/etc/apt/sources.list.d/webupd8team-sublime-text-2-raring.list.save:# deb-src [http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu](http://ppa.launchpad.net/webupd8team/sublime-text-2/ubuntu) raring main

I found a post that said use the -y switch ie. sudo add-apt-repository ppa:webupd8team/sublime-text-2 -y

it still gave me some errors but added it to the source list but on update the launchpad key was missing so i got the key with:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C2518248EEA14886

---

### Post by Frogs Hair on 2013-05-31
Try the following one at a time.

```
sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get clean 
sudo apt-get update



```

---

### Post by cdoshi on 2013-06-03
Thanx Frogs Hair,
I tried the commands that you suggested but still no joy :(
But I think I have given up now to try to fix this issue.

---

