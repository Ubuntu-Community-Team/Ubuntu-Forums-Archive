---
title: "ubuntu specific package versions don't satisfy dependencies"
date: 2023-01-14
forum: General Help
---

### Post by dsz1728 on 2023-01-14
I am seeing an increasing number of packages that I am unable to install due to unmet dependencies, for reasons like this:

```

The following packages have unmet dependencies:
 libfreetype6-dev : Depends: libfreetype-dev (= 2.10.1-2) but 2.10.1-2ubuntu0.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

Is there a way to tell apt to accept version XXXXubuntu0.1 as version XXXX?  Or some other way around this problem?   It is becoming rather debilitating.

---

### Post by deadflowr on 2023-01-14
Is this mixed architecture system?
The 2.10.1-2 version is only allowed* for arm-based (arm64, armhf) packages and the 2.10.1-2ubuntu0.1 version is for x86-based (amd64, i386) packages.

([I]* for full clarity I'm ignoring both the ppc64el and s390x architectures since those aren't very commonly used by the majority of our user base.
Those both share the same version strings as the arm-based packages, fwiw[/I])

---

### Post by dsz1728 on 2023-01-14
No, this is on a Dell xp-13 laptop, which came with Ubuntu 20.04 pre-installed.

---

### Post by deadflowr on 2023-01-14
weird, huh.
Run
```
sudo apt update
```
post back what it shows.

---

### Post by dsz1728 on 2023-01-14
No, this is on a Dell xp-13 laptop, which came with Ubuntu 20.04 pre-installed.

[Don't know how this post got duplicated!  I would delete it if I could, but don't see that option.]

---

### Post by dsz1728 on 2023-01-14
```

% sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://archive.canonical.com/ubuntu focal InRelease
Hit:3 http://ppa.launchpad.net/inkscape.dev/stable/ubuntu focal InRelease
Hit:4 http://dl.google.com/linux/chrome/deb stable InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

---

### Post by #&amp;thj^% on 2023-01-14
what are you trying to install?
```
 libfreetype-dev | 2.10.1-2               | focal          | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.10.1-2ubuntu0.2      | focal-security | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.10.1-2ubuntu0.2      | focal-updates  | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.11.1+dfsg-1build1    | jammy          | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.11.1+dfsg-1ubuntu0.1 | jammy-security | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.11.1+dfsg-1ubuntu0.1 | jammy-updates  | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.12.1+dfsg-3          | kinetic        | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.12.1+dfsg-3          | lunar          | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 libfreetype-dev | 2.12.1+dfsg-4          | lunar-proposed | amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

---

### Post by dsz1728 on 2023-01-14
> **1fallen said:**
> what are you trying to install?

Well, I've encountered this problem various times.  But here's one in particular:

```

% sudo apt install libfontconfig1-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libfontconfig1-dev : Depends: libfreetype6-dev (>= 2.8.1) but it is not going to be installed
                      Depends: uuid-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

% sudo apt install libfreetype6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libfreetype6-dev : Depends: libfreetype-dev (= 2.10.1-2) but 2.10.1-2ubuntu0.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by #&amp;thj^% on 2023-01-14
That's helpful thanks, have you corrected apt yet IE:
```
sudo apt clean
```
next
```
sudo apt --fix-broken install
```
and maybe you lack a repo for your sources:
```
cat /etc/apt/sources.list
```
I only saw a couple enabled from your apt update return

---

### Post by dsz1728 on 2023-01-14
> **1fallen said:**
> That's helpful thanks, have you corrected apt yet IE:
```
sudo apt clean
```

Interesting.  What does that do?  It's not documented in the man page.
> next
```
sudo apt --fix-broken install
```

Did those, and tried again with same results.

> and maybe you lack a repo for your sources:
```
cat /etc/apt/sources.list
```
I only saw a couple enabled from your apt update return

I do not have any deb-src entries enabled.  But I did try it earlier with a bunch of them uncommented, and had the same behavior.
Here is what is currently uncommented in all my apt sources:

```

% grep -v '^#' /etc/apt/sources.list /etc/apt/sources.list.d/* | grep -v '^.*: *$'
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu focal partner
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu focal main universe restricted multiverse
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-focal.list:deb http://ppa.launchpad.net/inkscape.dev/stable/ubuntu focal main

```

And here are all the commented-out deb-src entries in /etc/apt/sources.list:

```

# deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://archive.canonical.com/ubuntu focal partner
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

```

---

### Post by deadflowr on 2023-01-14
You need to enable both the security and updates repositories.
(You can also disable the Partners repository since it's empty.)

Open the app Software and Updates and first go to Updates and enable both the security and the updates options.
Then go to Other Software and disable Canonical Partners.

> Interesting. What does that do? It's not documented in the man page.
It cleans the package cache on your system.
It is documented, but in apt-get's man page documentation.
I think apt's man page explains why it's not there too.

---

### Post by dsz1728 on 2023-01-15
Ok, I think everything is fixed now!   Based on what you said about the repositories I need, I realized my sources.list was missing these --- not just commented out.   I had wondered why 'apt-get upgrade' never did anything!  As it happens, I somehow had also lost the Software and Updates app, and trying to install software-properties-gtk ran into the same dependency problem.   But I found a copy of the default sources.list for focal and replace the one had with that, then did 'apt-get update; apt-get upgrade'.  After upgrading 612 packages, everything seems to work.

Incidentally, I do see the 'clean' option for apt-get, but the word "clean" does not appear in my man page for apt.

Thanks for your help.

---

