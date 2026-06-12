---
title: "libsdl1.2-dev problems"
date: 2006-07-26
forum: General Help
---

### Post by MiguelC on 2006-07-26
Hi to all. I have the following problem : I'm trying to install QEMU 0.8.2. It requires libsdl1.2-dev but I received this

The following packages have unmet dependencies.
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installedor                          libglu-dev
E: Broken packages

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1-0ubuntu14 is to be installed
                    Depends: libgl1-mesa-dev but it is not going to be installedor
                             libgl-dev
E: Broken packages

what am I doing wrong?  :confused:   Thanks

PS : I'm using Dapper

---

### Post by gingermark on 2006-07-26
Can you post your sources.list (located in /etc/apt) please? [libglu1-mesa-dev](http://packages.ubuntu.com/dapper/libdevel/libglu1-mesa-dev) should be available, so I suspect it's a repository issue.

---

### Post by MiguelC on 2006-07-26
Here it goes:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by gingermark on 2006-07-26
Very odd, after looking a bit more, it seems to be in the main repository, which you seem to have enabled.

You could try downloading and manually installing libglu1-mesa-dev manually, but if you don't have it's dependencies already that could get messy.

I just browsed the main repository and it doesn't seem to be there, but I have it installed on my system, so that's really odd.

I'm really sorry I couldn't be more help.

---

### Post by MiguelC on 2006-07-27
No problem. Thanks for your help

---

