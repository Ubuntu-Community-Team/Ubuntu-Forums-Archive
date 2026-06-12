---
title: "sudo apt-get update isn't working"
date: 2013-04-23
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-04-23
If I run,
```

sudo apt-get update

```

It gives following erros,

```

Err http://dl.google.com stable Release.gpg
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable Release.gpg
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Ign http://dl.google.com stable Release
Ign http://dl.google.com stable Release
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Err http://dl.google.com stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable/main Translation-en
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable/main Translation-en
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]
Fetched 189 B in 4min 12s (0 B/s)
W: GPG error: http://download.opensuse.org ./ Release: The following signatures were invalid: KEYEXPIRED 1366357218
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages  Unable to connect to dl.google.com:http: [IP: 74.125.135.190 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

How to fix this problem?

---

### Post by vasa1 on 2013-04-23
Sometimes it could just so happen that dl.google.com is down for a while. But where did "W: GPG error: [http://download.opensuse.org](http://download.opensuse.org) ./" come from?

---

### Post by Ashfaqur Rahman on 2013-04-23
I don't know actually!

---

### Post by dino99 on 2013-04-23
if its your hardware, you might follow the ubuntu default archive sources only to get updates. So comment out the exotic entries inside /etc/apt/sources.list, then update again

---

### Post by dandroid13 on 2013-04-23
[http://dl.google.com](http://dl.google.com) is working fine here.

---

### Post by Ashfaqur Rahman on 2013-04-23
Comment out means ## ?
How can I know which is exotic entries or not? @dino99

---

### Post by dandroid13 on 2013-04-23
> **Ashfaqur Rahman said:**
> Comment out means ## ?
How can I know which is exotic entries or not? @dino99

Yes.
The OpenSuse one.

---

### Post by deadflowr on 2013-04-23
Don't know about that opensuse thing, but the entries for google's repo should be in the /etc/apt/sources.list.d directory.
That's where the third party, non-Ubuntu repos go.
You should find a couple files with names like google-talkplugin.list, or google-chrome-stable.list in there.
Simply remove the files. Then run update.

---

### Post by deadflowr on 2013-04-23
You could post the results of

```
cat /etc/apt/sources.list
```

And we can help with what lines should go and what should stay.

---

### Post by Ashfaqur Rahman on 2013-04-23
Here is the result of,
```

cat /etc/apt/sources.list

```

I have already comment out the opensuse one.
```

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal universe
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://bd.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://bd.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
##deb http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/ ./
##deb-src http://download.opensuse.org/repositories/home:/sarimkhan/xUbuntu_12.10/ ./

```

---

### Post by Ashfaqur Rahman on 2013-04-23
Problem Solved!

Just removed google-chrome.list and google-talkplugin.list from /etc/apt/sources.list.d derectory .

Whats wrong with these sources?

---

### Post by pcatalani on 2013-05-07
> **Ashfaqur Rahman said:**
> Problem Solved!

Just removed google-chrome.list and google-talkplugin.list from /etc/apt/sources.list.d derectory .

Whats wrong with these sources?

FYI, same here w/ Kubuntu 13.04. I found two ways to resolve, but not certain the correctness:
1) Remove/comment the following lines from sources.list:
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

__OR__
2) comment the one single line(below) from sources.list.d/google-chrome.list:
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

I used option #2.

---

