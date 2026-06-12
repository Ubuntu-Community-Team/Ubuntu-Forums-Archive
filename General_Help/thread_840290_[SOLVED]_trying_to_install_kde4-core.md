---
title: "[SOLVED] trying to install kde4-core"
date: 2008-06-25
forum: General Help
---

### Post by moore.bryan on 2008-06-25
when i try to install kde4-core, i get the following:
```
(Reading database ... 199862 files and directories currently installed.)
Unpacking libqt4-webkit (from .../libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb (--unpac                    k):
 trying to overwrite `/usr/lib/libQtWebKit.so.4', which is also in package libqtwebkit0d
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libplasma2:
 libplasma2 depends on libqt4-webkit (>= 4.4.0); however:
  Package libqt4-webkit is not installed.
dpkg: error processing libplasma2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-bin:
 kdebase-workspace-bin depends on libplasma2; however:
  Package libplasma2 is not configured yet.
dpkg: error processing kdebase-workspace-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace:
 kdebase-workspace depends on kdebase-workspace-bin (>= 4:4.0.83-0ubuntu1~hardy1~ppa7); however:
  Package kdebase-workspace-bin is not configured yet.
dpkg: error processing kdebase-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksysguard-kde4:
 ksysguard-kde4 depends on libplasma2; however:
  Package libplasma2 is not configured yet.
dpkg: error processing ksysguard-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-libs4+5:
 kdebase-workspace-libs4+5 depends on libplasma2; however:
  Package libplasma2 is not configured yet.
dpkg: error processing kdebase-workspace-libs4+5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde4-core:
 kde4-core depends on kdebase-workspace (>= 4:4.0.0); however:
  Package kdebase-workspace is not configured yet.
dpkg: error processing kde4-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libplasma2
 kdebase-workspace-bin
 kdebase-workspace
 ksysguard-kde4
 kdebase-workspace-libs4+5
 kde4-core

```
what gives?

---

### Post by Zorael on 2008-06-25
Does a '**sudo apt-get install -f**' fix it?

---

### Post by moore.bryan on 2008-06-25
unfortunately, no:
```

moore@thinkpad:~$ sudo apt-get install -f kde4-core
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
  kde4-core: Depends: kdebase-kde4 (>= 4:4.0.0) but it is not going to be installed
             Depends: kdebase-workspace (>= 4:4.0.0) but it is not going to be installed
E: Broken packages

```

---

### Post by moore.bryan on 2008-06-25
this:
```
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
is what seems to be causing all the problems. could this deb be broke in the repos?

---

### Post by Zorael on 2008-06-25
> **moore.bryan said:**
> ```
(Reading database ... 199862 files and directories currently installed.)
Unpacking libqt4-webkit (from .../libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libQtWebKit.so.4', which is also in package **libqtwebkit0d**
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-webkit_4.4.0-1ubuntu5~hardy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```
libqtwebkit0d is intruiging. This package does not exist on the official repositories.
```
$ apt-cache policy libqtwebkit0d
W: Unable to locate package libqtwebkit0d
```


Perhaps you installed it from a third-party source? Removing it might cause something to go down along with it.
```
$ sudo aptitude remove libqtwebkit0d
$ sudo dpkg --remove libqtwebkit0d
$ sudo aptitude install kde4-core
```


On a side note, if you're using apt-get, I suggest you use aptitude when installing stuff; it's better at resolving dependency problems.

---

### Post by moore.bryan on 2008-06-25
> **Zorael said:**
> libqtwebkit0d is intruiging.
i have no idea from where this came and didn't even see it in the original gobbledegook...
> Removing it might cause something to go down along with it.
```
$ sudo aptitude remove libqtwebkit0d
$ sudo dpkg --remove libqtwebkit0d
$ sudo aptitude install kde4-core
```

perfect/success!
> 
On a side note, if you're using apt-get, I suggest you use aptitude when installing stuff; it's better at resolving dependency problems.
i don't usually use apt-get, only did because it was suggested. aptitude is *much* better.
many thanks!

---

