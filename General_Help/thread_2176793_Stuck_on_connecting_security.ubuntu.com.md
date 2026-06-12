---
title: "Stuck on connecting security.ubuntu.com"
date: 2013-09-26
forum: General Help
---

### Post by courtney2 on 2013-09-26
This happens for a lot (if not all) of the installs I try to do through Terminal. Each time I try to install something it'll appear to almost finish then it will get stuck on "100% [Connecting to security.ubuntu.com]" and it won't do anything else but pop up but "Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)" and "Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release". I'm not sure how to get around it, but I'm currently trying to install WINE and even through the software center it fails and doesn't seem to fully install...any ideas?

Also, I find it funny how on Ubuntu the spelling of "center" is wrong and wants to write "centre" haha

---

### Post by courtney2 on 2013-09-26
This is the string that it gets stuck on last before it freezes up "Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe Translation-en_CA"

---

### Post by Bashing-om on 2013-09-26
courtney2; Hi !

To me that indicates a problem with the sources.list index file. Let us take a gander at what that source list is;\post the out put -between code (#) tags -  of terminal codes:
```

cat /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```
We will see what is not going on and why.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by courtney2 on 2013-09-26
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

drwxr-xr-x 2 root root 4096 Sep 26 00:11 .
drwxr-xr-x 6 root root 4096 Sep 25 23:56 ..
-rw-r--r-- 1 root root  176 Sep 26 00:33 google-chrome.list
-rw-r--r-- 1 root root  176 Sep 26 00:33 google-chrome.list.save
-rw-r--r-- 1 root root  160 Sep 26 00:33 private-ppa.launchpad.net_commercial-ppa-uploaders_billiards_ubuntu.list
-rw-r--r-- 1 root root  160 Sep 26 00:33 private-ppa.launchpad.net_commercial-ppa-uploaders_billiards_ubuntu.list.save
-rw-r--r-- 1 root root  484 Sep 26 00:33 ubuntu-wine-ppa-raring.list
-rw-r--r-- 1 root root  414 Sep 26 00:33 ubuntu-wine-ppa-raring.list.save
-rw-r--r-- 1 root root  118 Sep 26 00:33 wfg-0ad-raring.list
-rw-r--r-- 1 root root  118 Sep 26 00:33 wfg-0ad-raring.list.save

I wasn't quite sure how you wanted me to post this but...this is the output

---

### Post by Bashing-om on 2013-09-26
courtney2; Well !

I did not see an error as I expected to see on the sources.list file; However, maybe maybe this:
in your sources.list:
> 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
 In conjunction with the added PPAs. 
Perhaps as security is not enabled the package manager is hollering about one of the PPAs.
Remove the "#" before the sources line:
> 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
 to enable them.
Worth a shot and see what haps ///
Remember to always make a back up of any file one is going to edit .. Murphy's law always applies -> what ever can go wrong will go wrong !
Any hesitation about editing that file ...ask,

code tags: 
ok at the top of the post are 3 tool bars, in the second row 3rd from right end is the "#" symbol. You have something copied onto the "clipboard",
the cursor placed where you want that text inserted into the post ...click on the "#" and then "paste".
That text is then inserted - between code tags.
Edit: Wine:
Unless you really know what you are doing I would strongly advise that you install Wine via the repository rather than the PPA .. try'n to avoid dependency issues due to later version files that might get installed from the PPA !
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine/ppa

``` 

[INDENT][INDENT]makes sense to me
[/INDENT][/INDENT]

---

### Post by courtney2 on 2013-09-29
> **Bashing-om said:**
> courtney2; Well !

I did not see an error as I expected to see on the sources.list file; However, maybe maybe this:
in your sources.list:
 In conjunction with the added PPAs. 
Perhaps as security is not enabled the package manager is hollering about one of the PPAs.
Remove the "#" before the sources line:
 to enable them.
Worth a shot and see what haps ///
Remember to always make a back up of any file one is going to edit .. Murphy's law always applies -> what ever can go wrong will go wrong !
Any hesitation about editing that file ...ask,

code tags: 
ok at the top of the post are 3 tool bars, in the second row 3rd from right end is the "#" symbol. You have something copied onto the "clipboard",
the cursor placed where you want that text inserted into the post ...click on the "#" and then "paste".
That text is then inserted - between code tags.
Edit: Wine:
Unless you really know what you are doing I would strongly advise that you install Wine via the repository rather than the PPA .. try'n to avoid dependency issues due to later version files that might get installed from the PPA !
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine/ppa

``` 
[INDENT][INDENT]makes sense to me
[/INDENT]
[/INDENT]


I'm not entirely sure if I follow..how do I remove the hashtags? It won't let me..a bit of a walkthrough would be nice, I'm very very new to anything Linux :P

---

### Post by Elfy on 2013-09-29
Closed.

Op has started new thread here [http://ubuntuforums.org/showthread.php?t=2177525](http://ubuntuforums.org/showthread.php?t=2177525)

---

