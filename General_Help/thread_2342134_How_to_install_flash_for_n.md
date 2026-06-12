---
title: "How to install flash for n"
date: 2016-11-04
forum: General Help
---

### Post by bradwiggo on 2016-11-04
I am trying to play the game n, the download version not the online version, and I can't get it to work, I think I haven't got flash installed, how should I install it.

---

### Post by howefield on 2016-11-04
Open the Software & Updates application and go to the Other Software tab and enable the Canonical Partners repository.

Load up a terminal and use the following commands..

```
sudo apt-get update
```
```
sudo apt-get install adobe-flashplugin
```

---

### Post by bradwiggo on 2016-11-04
> **howefield said:**
> Open the Software & Updates application and go to the Other Software tab and enable the Canonical Partners repository.

Load up a terminal and use the following commands..

```
sudo apt-get update
```
```
sudo apt-get install adobe-flashplugin
```
That gives an error: package 'adobe flash plugin has no installation candidate.

---

### Post by howefield on 2016-11-04
> **bradwiggo said:**
> That gives an error: package 'adobe flash plugin has no installation candidate.

Then you have made an error in not following instruction.

What is the output of

```
apt-cache policy adobe-flashplugin
```

This time share your terminal output so others can see exactly what you are typing and the relevant output.

---

### Post by bradwiggo on 2016-11-05
This is what it says: 
adobe-flashplugin: 
Installed: (none) 
Candidate: (none) 
Version table:

---

### Post by howefield on 2016-11-05
OK, sounds like you have not enabled the Partners repository or failed to do the sudo apt-get update, what is the output of 

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by bradwiggo on 2016-11-07
> **howefield said:**
> OK, sounds like you have not enabled the Partners repository or failed to do the sudo apt-get update, what is the output of 

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

The output fo trying to install after sudo apt-get update is: Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) vivid/partner adobe-flashplugin i386 1:20151228.1-0ubuntu0.15.04.1
  Temporary failure resolving 'archive.canonical.com'
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) vivid/partner adobe-flash-properties-gtk i386 1:20151228.1-0ubuntu0.15.04.1
  Temporary failure resolving 'archive.canonical.com'
E: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20151228.1-0ubuntu0.15.04.1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20151228.1-0ubuntu0.15.04.1_i386.deb)  Temporary failure resolving 'archive.canonical.com'

E: Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20151228.1-0ubuntu0.15.04.1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flash-properties-gtk_20151228.1-0ubuntu0.15.04.1_i386.deb)  Temporary failure resolving 'archive.canonical.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



The output of the code you said is: /etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid universe
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates universe
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
/etc/apt/sources.list.d/libretro-ubuntu-stable-vivid.list:deb [http://ppa.launchpad.net/libretro/stable/ubuntu](http://ppa.launchpad.net/libretro/stable/ubuntu) vivid main
/etc/apt/sources.list.d/libretro-ubuntu-stable-vivid.list.save:deb [http://ppa.launchpad.net/libretro/stable/ubuntu](http://ppa.launchpad.net/libretro/stable/ubuntu) vivid main

---

### Post by howefield on 2016-11-07
Vivid has long gone End of Life and is no longer supported. You could change your sources.list to reflect the new address for end of life repositories but that just leaves you vulnerable to things like the dirty cow exploit and others. So whilst it would work, it is an extremely bad choice.

Move to a currently supported release which currently realistically would be 14.04.5 or 16.04.1 the former being supported till 2019 and the latter 2021. 16.10 is the latest release but supported only 9 months.

---

