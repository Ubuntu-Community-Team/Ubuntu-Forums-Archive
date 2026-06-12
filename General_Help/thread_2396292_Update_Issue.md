---
title: "Update Issue"
date: 2018-07-13
forum: General Help
---

### Post by mpmckinnon on 2018-07-13
Hi there I am not 100% sure how to fix this short of reinstall and was hoping for some help. I am getting this error message when I am trying to do updates on my computer thank you.

```
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libsnmp30:i386 : Depends: libperl5.26:i386 (>= 5.26.0~rc1) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a sol
ution).

The following additional packages will be installed:
  libperl5.26:i386
The following NEW packages will be installed:
  libperl5.26:i386
0 upgraded, 1 newly installed, 0 to remove and 136 not upgraded.
37 not fully installed or removed.
Need to get 0 B/3,168 kB of archives.
After this operation, 16.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

(Reading database ... 273972 files and directories currently installed.)
Preparing to unpack .../libperl5.26_5.26.2-6_i386.deb ...
Unpacking libperl5.26:i386 (5.26.2-6) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.26_5.26.2-6_i386.deb (--
unpack):
 trying to overwrite shared '/usr/share/doc/libperl5.26/changelog.Debian.gz', which is d
ifferent from other instances of package libperl5.26:i386
Errors were encountered while processing:
 /var/cache/apt/archives/libperl5.26_5.26.2-6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by kc1di on 2018-07-13
You can try this command in a terminal see if it clears the problem.
```
sudo dpkg --configure -a
```

---

### Post by PaulW2U on 2018-07-13
> **mpmckinnon said:**
> E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a sol
ution).
Did you try the suggested command? ```
apt --fix-broken install
```

In a terminal please run:
```
sudo apt --fix-broken install
```
and then report back with any errors, if any.

[NOPARSE]Please use [CODE] tags for any terminal output and/or error messages. thanks.[/NOPARSE]

---

### Post by mpmckinnon on 2018-07-13
Hi there thank you for getting back to me I ran that command and got this

```
dpkg: dependency problems prevent configuration of libsnmp30:i386:
 libsnmp30:i386 depends on libperl5.26 (>= 5.26.0~rc1); however:
  Package libperl5.26:i386 is not installed.

dpkg: error processing package libsnmp30:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsane1:i386:
 libsane1:i386 depends on libsnmp30 (>= 5.7.3+dfsg-1.8ubuntu3~dfsg); however:
  Package libsnmp30:i386 is not configured yet.

dpkg: error processing package libsane1:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsnmp30:i386
 libsane1:i386
```

---

### Post by mpmckinnon on 2018-07-13
I also put in my original question what the error message I got from [COLOR=#000000][FONT=monospace]apt --fix-broken install.[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-07-13
I had seen this in April 2018 also>>>give this a try:
```
sudo rm /usr/share/doc/libperl5.26/changelog.Debian.gz
sudo apt install -f
```

---

### Post by mpmckinnon on 2018-07-13
Thank seems to work thank you so much guys for all your help :-).

---

### Post by #&amp;thj^% on 2018-07-13
Fantastic :)
You can mark this as solved under your first post #1 under thread tools and Mark as Solved.
Kind Regards

---

