---
title: "cannot install lib6c-dev"
date: 2008-01-20
forum: General Help
---

### Post by cheaptrick on 2008-01-20
hi i have a problem installing libc6-dev both from the sypnatic and sudo apt-get

this came up in the terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5 is to be installed
E: Broken packages

i checked the package manager libc6 is already in my system, so i dont really understand whats going on


any help will be appreciated , thanks.

---

### Post by aphirst on 2008-01-20
Have you tried:

```
sudo apt-get update && sudo apt-get upgrade
```

It is REALLY easy to confuse your package manager with outdated versions of libc6. I killed my 7.04 with a libc6 from a debian repos which was 1 version too new (!).

```
sudo dpkg --configure -a
```
may help

---

### Post by chrisccoulson on 2008-01-20
Are you sure you don't have any third party repositories in your sources.list?

---

### Post by aphirst on 2008-01-20
Yes, the pure debian repositories will KILL your libc6 . IT HAPPENED TO ME! It took a reinstall to fix. :(

---

### Post by cheaptrick on 2008-01-21
aphirst, i tried that it didnt work.
i think i might have some 3rd party repository in my source.
how do you check and fix it?

---

### Post by chrisccoulson on 2008-01-21
Post your /etc/apt/sources.list in [CODE] tags, so we can have a look at it

---

