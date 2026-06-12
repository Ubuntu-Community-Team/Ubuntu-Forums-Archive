---
title: "Thunderbird: cannot upgrade to 31.1 via Update-Manager (14.04.1 LTS)"
date: 2014-09-07
forum: General Help
---

### Post by Tibetan Wolf on 2014-09-07
Hello there, 

I'm relatively new to Ubuntu and Linux in general.

Recently Mozilla released Firefox 32.0 and Thunderbird 31.1
I was able to upgrade to Firefox 32.0 via Automatic Updates, immediately. However, thunderbird was not upgraded and the latest version and on my system it is still the 31.0 build (the one shipped with the Ubuntu point release).

When I look for updates via Update Manager (or using "sudo apt-get update" + "sudo apt-get upgrade"), the system says that I alredy have the latest version available  (i.e. 31.0 not the 31.1).
I read on several websites that Thunderbird 31.1 along with Firefox 32.0 were added to the official Ubuntu Repository the same day, so I have no idea what's wrong here: I have the latest version of Firefox, but not the latest one of Thunderbird (both released the same day, both with security fixes) and the Update Manager says that everything is up to date...

By the way, sorry for my English and thanks so much in advance.

*System info: Ubuntu 14.04.1 LTS (I've not modified any Updates preference/options) / Thunderbird 31.0*

---

### Post by azgrel on 2014-09-07
I guess it's still going through security and stability tests. But if you don't want to wait for it to appear in official repo you can add Mozilla repo: ```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
``` and update system with ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Tibetan Wolf on 2014-09-07
Thanks so much for your reply, azgrel.

I thought the same, but it was released the same day (Tuesday, 2) of Firefox 32 and apparently they both were added to the official Ubuntu repository... well, according to the Internet... 
May I ask you if you were able to get Thunderbird 31.1 without adding the mozilla ppa you mentioned?

In general I'd like to know if anyone here was able to upgrade Thunderbird to v.31.1 via Automatic Updates/Update Manager?

---

### Post by Tibetan Wolf on 2014-09-08
ehm... anyone? :neutral:

---

### Post by SeijiSensei on 2014-09-08
31.1 is available for the upcoming 14.10 Utopic Unicorn release.

The answers to questions like yours can be found on the corresponding package page at Launchpad:  [https://launchpad.net/ubuntu/+source/thunderbird](https://launchpad.net/ubuntu/+source/thunderbird)

For releases with "long-term support" like 14.04, the maintainers don't upgrade packages just because new releases have come out.  They will "backport" security fixes into the older code as was done with OpenSSL after the "Heartbleed" bug was found.  But new package releases usually appear in the next version of Ubuntu.

---

### Post by Tibetan Wolf on 2014-09-08
Thanks so much for the very useful info, SeijiSensei 

So basically I can check Launchpad to see the publishing history of a package for my distro... But is there a way to do the same via Ubuntu Software Center? I mean, is there a way to check which is the latest version available on the Ubuntu Software Center for apps that I have already installed and currently reside on my system?
I'm asking because when I check,  it always shows the version number of the package that is currently on my system, even if I have not applied any updates... (should I have to open a new thread for this question, please let me know).

---

### Post by SeijiSensei on 2014-09-09
I never use GUI apps for these tasks because the command-line utilities are so powerful.

To see the information for a currently-installed package use dpkg like this:
```
dpkg -s thunderbird
```
On my 14.04 system that returns:
```

$ dpkg -s thunderbird

Package: thunderbird
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 70575
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 1:31.0+build1-0ubuntu0.14.04.1
Replaces: mozilla-thunderbird, thunderbird-gnome-support (<= 3.0.4+nobinonly-0ubuntu3)
Provides: mail-reader
[much more stuff]

```

Use the command "dpkg --help" to see a list of its options, or type "man dpkg" to see its manual page.

---

### Post by Tibetan Wolf on 2014-09-10
Thank you very much, SeijiSensei

---

