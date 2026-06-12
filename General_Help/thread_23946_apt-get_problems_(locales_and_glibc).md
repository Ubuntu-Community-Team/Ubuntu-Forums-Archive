---
title: "apt-get problems (locales and glibc)"
date: 2005-04-04
forum: General Help
---

### Post by Sniz on 2005-04-04
I've gotten myself in a mess I can't get out off.

I tried installing Gimpshop but needed a newer version of libc so I installed 
[http://ftp.debian.org/pool/main/g/glibc/libc6_2.3.4-2_i386.deb](http://ftp.debian.org/pool/main/g/glibc/libc6_2.3.4-2_i386.deb)
as suggested in the comments at gimpshop.
And at that moment just about everything broke. Everytime I try to apt-get something I get an error:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NL:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```

apt-get -f install doesn't work. apt-get install locales neither. I totally out of ideas here.

---

### Post by Xian on 2005-04-04
[QUOTE=Sniz]I tried installing Gimpshop but needed a newer version of libc so I installed [http://ftp.debian.org/pool/main/g/glibc/libc6_2.3.4-2_i386.deb](http://ftp.debian.org/pool/main/g/glibc/libc6_2.3.4-2_i386.deb)
as suggested in the comments at gimpshop.
And at that moment just about everything broke.[/QUOTE]
Have you tried going into synaptic and changing the installed verison of libc back to the default?

---

### Post by Sniz on 2005-04-05
[QUOTE=Xian]Have you tried going into synaptic and changing the installed verison of libc back to the default?[/QUOTE]
Synaptec says libc6 version is 2.3.2.dsl-20ubuntu13 but when i mark it for reinstall i get an similar error:
```

E: console-data:  subprocess post-installation script returned error exit status 1

```

so it still won't work :/

---

### Post by Sarojin on 2005-04-22
I just compiled gimpshop and made a debian package for it using the default version of libc that comes with Hoary.  If someone wants to host it (about 10MB) let me know.

---

### Post by eeried on 2005-08-02
I'll go on with this thread since its title is quite appropriate;

I get the same problem, fussy locale messages similar to what Sniz gets:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_FR:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directorylocale: Cannot set LC_ALL to default locale: No such file or directory
```

This line is weird: LANGUAGE = "en_FR:en", -- an improbable language flavor!!

I read that thread too: [http://ubuntuforums.org/showthread.php?t=39840&highlight=setting+locale](http://ubuntuforums.org/showthread.php?t=39840&highlight=setting+locale)

What I get when I want to apt-get install locales is a dependency problem glibc6 and :glibc-2.3.2.ds1-20ubuntu13. 

```
sudo apt-get install glibc-2.3.2.ds1-20ubuntu13)

Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6 instead of glibc-2.3.2.ds1-20ubuntu13
libc6 is already the newest version.
```

If I remove glic6 with synaptic I may break other apps.

This is the output of the locale command on my ubuntu:

```
 sudo locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

Can this locale problem be fixed?

---

### Post by xerosis on 2005-08-02
you have to revert the version of libc in synaptic. changing to libc6 means every package has to be recompiled with it.

---

### Post by rherman on 2005-08-05
Hoary currently uses glibc2.3.2. I compiled Blender 2.37 successfully with compiler optimizations, but I would like to use glibc2.3.5. The repositories are only up to 2.3.2. Anyone know of how I can do this? Is it worth it performance-wise? Thanks.

Rob

---

