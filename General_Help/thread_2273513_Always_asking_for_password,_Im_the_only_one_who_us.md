---
title: "Always asking for password, Im the only one who uses this computer!"
date: 2015-04-13
forum: General Help
---

### Post by Mark_McDonald on 2015-04-13
How do I get around not having to put my password in, everytime I want to install something, or change something.

---

### Post by Keith_Helms on 2015-04-13
That's not recommended.   The idea is both to keep hackers/burglers/mischievous friends/etc from getting in to your system and also to protect you from accidentally changing or deleting something you didn't mean to.

If you *really* want to do so, take a look at this page:

[http://askubuntu.com/questions/147241/execute-sudo-without-password](http://askubuntu.com/questions/147241/execute-sudo-without-password)

---

### Post by grahammechanical on 2015-04-13
Are you using Ubuntu or one of the flavours of Ubuntu? I ask because a few years ago the developers took the decision that Ubuntu would reduce the number of authentications needed. And this has proved to be the case. But I have noticed that some of the flavours still require password authentication for many tasks that would not require authentication in Ubuntu.

Regards.

---

### Post by Mark_McDonald on 2015-04-15
Sorry, I am using Xubuntu. I tried looking into settings and such. Its nothing major, just gets a little annoying sometimes.

---

### Post by mc4man on 2015-04-15
For package management I see no reason for single user setup to  authenticate.  Easily done as such - 
```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/package-manager.pkla
```
Copy below & paste into nano, then save with keyboard actions - 
ctrl+o
enter
ctrl+x

```
[Install package file]
Identity=unix-group:sudo
Action=org.debian.apt.install-file;org.debian.apt.update-cache;org.debian.apt.install-or-remove-packages;org.debian.apt.upgrade-packages
ResultActive=yes

[Install package synaptic]
Identity=unix-group:sudo
Action=com.ubuntu.pkexec.synaptic
ResultActive=yes

[Change add repo]
Identity=unix-group:sudo
Action=com.ubuntu.softwareproperties.applychanges;org.debian.apt.change-repository
ResultActive=yes
```

This *will not* grant auth to terminal based installs, removals or upgrades

---

