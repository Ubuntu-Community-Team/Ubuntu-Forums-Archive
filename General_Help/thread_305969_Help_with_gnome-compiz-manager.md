---
title: "Help with gnome-compiz-manager"
date: 2006-11-24
forum: General Help
---

### Post by amrclutch1 on 2006-11-24
Can someone please explain to me what the error is in bold?

Here is the my terminal log
```

amrclutch1@clutch-linuxbox:~$ cd
amrclutch1@clutch-linuxbox:~$ cd Desktop
amrclutch1@clutch-linuxbox:~/Desktop$ cd gnome-compiz-manager-0.9.8/
amrclutch1@clutch-linuxbox:~/Desktop/gnome-compiz-manager-0.9.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
**checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool**
amrclutch1@clutch-linuxbox:~/Desktop/gnome-compiz-manager-0.9.8$

```

---

### Post by NetworkGuy on 2006-11-24
You need libperl5.8 from the repositories.  

That should get you started.  You may need more perl libraries after that, but you won't know that until further in the compile.  Unless there is a readme file in your source code that tells you what you dependicies are. :)

---

### Post by amrclutch1 on 2006-11-24
I already have libperl5.8. I checked the Synaptic Package Manager and its installed. Is there anything else I might need? Also im trying to install it from my desktop, should I move it somewhere else?

---

### Post by amrclutch1 on 2006-11-24
does anyone else know what the problem might be? Or where I can get more perl libs, because there aren't any repos in the readme.

---

### Post by bettola on 2006-11-24
try to install the -dev perl package

---

### Post by amrclutch1 on 2006-11-24
I can't find that in the Synaptic pkg manager, And I can't find it anywhere to download it, do you know where I could get it?

---

