---
title: "Should I pin thunderbird-locale-en-us from Mozilla Team ppa?"
date: 2023-07-12
forum: General Help
---

### Post by donald187 on 2023-07-12
I've added the repository ppa:mozillateam/ppa and have Thunderbird installed from that ppa.  

```

$ apt policy thunderbird
thunderbird:
  Installed: 1:102.13.0+build1-0ubuntu0.22.04.1~mt1
  Candidate: 1:102.13.0+build1-0ubuntu0.22.04.1~mt1
  Version table:
     1:102.13.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
 *** 1:102.13.0+build1-0ubuntu0.22.04.1~mt1 900
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

Here's /etc/apt/preferences.d/99mozillateam.

```

$ sudo cat /etc/apt/preferences.d/99mozillateam
Package: thunderbird
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 900

```

Thunderbird from the Ubuntu repositories just upgraded to 102.13.0 so it now has the same version as Thunderbird from the Mozilla Team repository.  I got this in /var/log/unattended-upgrades/unattended-upgrades.log

```

2023-07-12 06:24:36,163 INFO Starting unattended upgrades script
2023-07-12 06:24:36,163 INFO Allowed origins are: o=Ubuntu,a=jammy, o=Ubuntu,a=jammy-security, o=UbuntuESMApps,a=jammy-apps-security, o=UbuntuESM,a=jammy-infra-security, o=LP-PPA-mozillateam,a=jammy
2023-07-12 06:24:36,163 INFO Initial blacklist: 
2023-07-12 06:24:36,164 INFO Initial whitelist (not strict): 
2023-07-12 06:24:37,548 INFO Packages that will be upgraded: thunderbird-locale-en-us
2023-07-12 06:24:37,548 INFO Writing dpkg log to /var/log/unattended-upgrades/unattended-upgrades-dpkg.log
2023-07-12 06:24:39,526 INFO All upgrades installed
2023-07-12 06:24:39,762 INFO Package thunderbird-gnome-support is kept back because a related package is kept back or due to local apt_preferences(5).
2023-07-12 06:24:39,763 INFO Package thunderbird-locale-en is kept back because a related package is kept back or due to local apt_preferences(5).

```

The packages thunderbird-gnome-support and thunderbird-locale-en were kept back and the corresponding packages from the Mozilla Team repository were kept installed as I assume is the way it should be.  

```

$ apt policy thunderbird-gnome-support
thunderbird-gnome-support:
  Installed: 1:102.13.0+build1-0ubuntu0.22.04.1~mt1
  Candidate: 1:102.13.0+build1-0ubuntu0.22.04.1
  Version table:
     1:102.13.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
 *** 1:102.13.0+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

```

$ apt policy thunderbird-locale-en
thunderbird-locale-en:
  Installed: 1:102.13.0+build1-0ubuntu0.22.04.1~mt1
  Candidate: 1:102.13.0+build1-0ubuntu0.22.04.1
  Version table:
     1:102.13.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
 *** 1:102.13.0+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```


My question is about the package thunderbird-locale-en-us which was upgraded to the package from the Ubuntu repositories.  From /var/log/apt/history.log

```

Start-Date: 2023-07-12  06:24:37
Commandline: /usr/bin/unattended-upgrade
Upgrade: thunderbird-locale-en-us:amd64 (1:102.13.0+build1-0ubuntu0.22.04.1~mt1, 1:102.13.0+build1-0ubuntu0.22.04.1)
End-Date: 2023-07-12  06:24:38

```

```

$ apt policy thunderbird-locale-en-us
thunderbird-locale-en-us:
  Installed: 1:102.13.0+build1-0ubuntu0.22.04.1
  Candidate: 1:102.13.0+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:102.13.0+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main i386 Packages
        100 /var/lib/dpkg/status
     1:102.13.0+build1-0ubuntu0.22.04.1~mt1 500
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main i386 Packages
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/main i386 Packages

```

Should thunderbird-locale-en-us actually be installed from the Mozilla Team repository?  Should I add an entry to /etc/apt/preferences.d/99mozillateam to make it look like

```

Package: thunderbird
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 900

Package: thunderbird-locale-en-us
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 900

```

and then downgrade it using 

```

sudo apt install thunderbird-locale-en-us=1:102.13.0+build1-0ubuntu0.22.04.1~mt1

```

?

---

### Post by donald187 on 2023-07-12
Hmmm.  I just got the bright idea of running "apt show" on the package.

```

$ apt -a show thunderbird-locale-en-us
Package: thunderbird-locale-en-us
Version: 1:102.13.0+build1-0ubuntu0.22.04.1
Priority: optional
Section: web
Source: thunderbird
Origin: Ubuntu
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 131 kB
Depends: thunderbird-locale-en
Task: ubuntu-desktop-default-languages
Download-Size: 9,250 B
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
Description: Transitional English language pack for Thunderbird
 This is a transitional package to ensure that upgrades work correctly.
 It can be safely removed

Package: thunderbird-locale-en-us
Version: 1:102.13.0+build1-0ubuntu0.22.04.1~mt1
Priority: optional
Section: web
Source: thunderbird
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Installed-Size: 131 kB
Depends: thunderbird-locale-en
Download-Size: 101 kB
APT-Sources: https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
Description: Transitional English language pack for Thunderbird
 This is a transitional package to ensure that upgrades work correctly.
 It can be safely removed

Package: thunderbird-locale-en-us
Version: 1:91.8.0+build2-0ubuntu1
Priority: optional
Section: web
Source: thunderbird
Origin: Ubuntu
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 130 kB
Depends: thunderbird-locale-en
Task: ubuntu-desktop-default-languages
Download-Size: 9,074 B
APT-Sources: http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
Description: Transitional English language pack for Thunderbird
 This is a transitional package to ensure that upgrades work correctly.
 It can be safely removed

```

"This is a transitional package to ensure that upgrades work correctly.  It can be safely removed."  But I don't know if it matters which repository it comes from.  I would think it does matter since I will be doing upgrades within the Mozilla Team repository.

---

### Post by donald187 on 2023-07-13
I'm guessing it doesn't matter.  My guess is that at one time they used to use the package thunderbird-locale-en-us and at some point they instead used the package thunderbird-locale-en.  So they created this transitional package which depends on the new package as it says in "apt show thunderbird-locale-en-us". above.  This process is described in the following link.  So it looks as though I can just leave it alone.

[https://askubuntu.com/questions/20377/what-exact-purpose-have-transitional-packages](https://askubuntu.com/questions/20377/what-exact-purpose-have-transitional-packages)

---

### Post by donald187 on 2023-07-13
It seems that thunderbird-locale-en is the "real" package.  Which is being held back in favor of the package from the Mozilla Team repository.  So this is what matters.  And what would happen again if Thunderbird from the Ubuntu repositories were to have a higher version number than Thunderbird from the Mozilla Team repository. Unless there's something I'm missing.  Perhaps in this scenario thunderbird-locale-en-us would require thunderbird-locale-en to have a higher version than what is in the Mozilla Team repository?  Would this create a problem?  But "apt show thunderbird-locale-en-us" doesn't show a minimum version requirement for thunderbird-locale-en as I sometimes see.  So it seems this wouldn't be a problem.

I'll make an executive decision  :P and mark this thread as solved.

EDIT:  The real answer is to follow DuckHook's instructions for using the ppa for Firefox but to use Thunderbird instead.
.
[https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386](https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386)

---

