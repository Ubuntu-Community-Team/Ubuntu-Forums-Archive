---
title: "libcairo2-dev requires libfontconfig1-dev (&gt;= 2.2.95) but it is not in the repos"
date: 2019-02-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2019-02-10
I wanted to install [gwe](https://gitlab.com/leinardi/gwe) from source and give it a try on 18.04, but i encountered a issue with dependencies
from what i can tell one package in the stock repos requires a package of a version that is not in the repos

```
chad@Z97Killer:~$ sudo apt-get install meson python3-pip libcairo2-dev libgirepository1.0-dev libdazzle-1.0-dev gir1.2-gtksource-3.0 appstream-util # this is only the dependencies that i do not have installed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcairo2-dev : Depends: libfontconfig1-dev (>= **2.2.95**) but it is not going to be installed
 libdazzle-1.0-dev : Depends: libgtk-3-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
chad@Z97Killer:~$ apt-cache policy libcairo2-dev libfontconfig1-dev
libcairo2-dev:
  Installed: (none)
  Candidate: 1.15.10-2ubuntu0.1
  Version table:
     1.15.10-2ubuntu0.1 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     1.15.10-2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
libfontconfig1-dev:
  Installed: (none)
  Candidate: **2.12.6-0ubuntu2**
  Version table:
     2.12.6-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

---

### Post by mc4man on 2019-02-11
If you didn't figure out yet try starting singly, i.e with libfontconfig1-dev only.
If that works install libcairo2-dev, then libgtk-3-dev, ect.

---

### Post by pqwoerituytrueiwoq on 2019-02-11
[FONT=courier new]libfontconfig[/FONT] was a newer package that was available, i believe i updated that one to fix a problem i was having in firefox: [https://askubuntu.com/questions/1076412/firefox-freezing-with-100-cpu-usage-for-30-seconds-when-launching-chromium](https://askubuntu.com/questions/1076412/firefox-freezing-with-100-cpu-usage-for-30-seconds-when-launching-chromium)
but downgradeing that solved this issue

---

