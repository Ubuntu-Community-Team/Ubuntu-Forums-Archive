---
title: "Firefox and flashplugin almost crashing Xorg"
date: 2014-08-08
forum: General Help
---

### Post by papibe on 2014-08-08
Hi all,

In the past, plugin-contain would try to eat the CPU resulting in a moderate lag. However, this is different.

Now Xorg is being affected in a HUGE way, almost halting the desktop.

This is usually heppens when visiting Flash intensive web pages. Particularly, this one for example:
```
http://soundbible.com/tags-alarm.html
``` 
Would almost bring my desktop to a halt:
```
top -n 14 -b | awk '/Xorg/ {print}; /plugin/ {print}; /top -/ {print " "}' 
```
```
 1045 root      20   0  278908 105660  61716 R  59.8  2.7  16:47.95 Xorg
 6552 user      20   0  534004 109084  51228 S  29.4  2.7   0:00.93 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  52.3  2.7  16:49.53 Xorg
 6552 user      20   0  704528 185032  61820 S  44.6  4.6   0:02.28 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  89.0  2.7  16:52.22 Xorg
 6552 user      20   0  720656 209232  70668 S   8.9  5.3   0:02.55 plugin-con+
 
 1045 root      20   0  278908 105660  61716 S  75.6  2.7  16:54.51 Xorg
 6552 user      20   0  804668 247072  75752 R  22.5  6.2   0:03.23 plugin-con+
 
 1045 root      20   0  278908 105660  61716 S  71.2  2.7  16:56.66 Xorg
 6552 user      20   0  901720 287672  79536 R  27.8  7.2   0:04.07 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  [COLOR="#FF0000"]**92.1**[/COLOR]  2.7  16:59.45 Xorg
 6552 user      20   0  929344 304288  84576 S   6.3  7.6   0:04.26 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  [COLOR="#FF0000"]**92.4**[/COLOR]  2.7  17:02.25 Xorg
 6552 user      20   0  938560 316772  89632 S   5.6  8.0   0:04.43 plugin-con+
 
 1045 root      20   0  278908 105660  61716 S  [COLOR="#FF0000"]**92.4**[/COLOR]  2.7  17:05.05 Xorg
 6552 user      20   0  952412 328204  92184 R   6.3  8.2   0:04.62 plugin-con+
 
 6552 user      20   0 1152636 401284  94688 S  50.0 10.1   0:06.13 plugin-con+
 1045 root      20   0  278908 105660  61716 R  47.0  2.7  17:06.47 Xorg
 
 1045 root      20   0  278908 105660  61716 R  [COLOR="#FF0000"]**91.1**[/COLOR]  2.7  17:09.22 Xorg
 6552 user      20   0 1165440 416844  97216 S   9.3 10.5   0:06.41 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  [COLOR="#FF0000"]**94.4**[/COLOR]  2.7  17:12.07 Xorg
 6552 user      20   0 1186432 424184  99744 S   4.3 10.7   0:06.54 plugin-con+
 
 1045 root      20   0  278908 105660  61716 R  [COLOR="#FF0000"]**94.7**[/COLOR]  2.7  17:14.93 Xorg
 6552 user      20   0 1191040 428316 102272 S   3.3 10.8   0:06.64 plugin-con+
 
 1045 root      20   0  278972 105660  61716 S  64.9  2.7  17:16.89 Xorg
 6552 user      20   0 1292784 473120 103656 R  30.1 11.9   0:07.55 plugin-con+
 
 6552 user      20   0 1555056 572228 103704 R  79.4 14.4   0:09.95 plugin-con+
 1045 root      20   0  279020 105660  61716 S  16.5  2.7  17:17.39 Xorg

```
Is this a Firefox bug?
Is it a Flash problem?
Why Xorg is being affected is this way?

I appreciate any tips and comments.
Regards.

Version information:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

$ uname -a
Linux vaughan 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

$ apt-cache policy firefox
firefox:
  Installed: 31.0+build1-0ubuntu0.14.04.1
  Candidate: 31.0+build1-0ubuntu0.14.04.1
  Version table:
 *** 31.0+build1-0ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
     28.0+build2-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

$ apt-cache policy Xorg
xorg:
  Installed: 1:7.7+1ubuntu8
  Candidate: 1:7.7+1ubuntu8
  Version table:
 *** 1:7.7+1ubuntu8 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

$ apt-cache policy compiz
compiz:
  Installed: 1:0.9.11.2+14.04.20140714-0ubuntu1
  Candidate: 1:0.9.11.2+14.04.20140714-0ubuntu1
  Version table:
 *** 1:0.9.11.2+14.04.20140714-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:0.9.11+14.04.20140409-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

$ apt-cache policy flashplugin-installer 
flashplugin-installer:
  Installed: 11.2.202.394ubuntu0.14.04.1
  Candidate: 11.2.202.394ubuntu0.14.04.1
  Version table:
 *** 11.2.202.394ubuntu0.14.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
        100 /var/lib/dpkg/status
     11.2.202.350ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages

```

---

### Post by vasa1 on 2014-08-08
What about your computer specs? I tried the page on a Dell Core2Duo 1545 laptop with integrated graphics. While CPU and RAM did rise, it didn't seem particularly bad. Xorg didn't exceed 5%. This is on the home page of the link you provided.

My system is the Openbox session of Lubuntu 14.04 fully updated. So no compiz or other compositing effects.

And Firefox is current as well (but direct from Mozilla, not Canonical's version).

---

### Post by papibe on 2014-08-09
Thanks for taking interest, vasa1 :)

I did the test on a Dell Dimension E520, with a Pentium D (2 cores), 4Gb RAM, Nvidia 9500GT, and an Samsung SSD.

I'm gonna try the same test on my laptop later (Toshiba Satellite, i7, 4Gb RAM, Nvdia 310M).

Regards.

---

### Post by QIII on 2014-08-09
Hey, papibe.  I get a black flash container occasionally with runaway xorg.  The cause may be similar even if the symptoms are not.  Last time I had it happen was on one of my desktops: AMD Phenom II 1100T, 16GB, ATI HD 5870.

So there's a lot of horsepower there.

If I kill plugin-container, everything goes back to normal.  I lose the content of course.

Try that.  If you get similar results maybe we can narrow it down to the flash plugin container and work from there.

---

### Post by papibe on 2014-08-12
OK, this is a bug, and I have to add Nvidia to the probably guilty parties.

Run on my Toshiba  Satellite A665, i7, 4Gb RAM, Nvidia 310M:
```

 1008 root      20   0  215488  62148  34868 R  83.3  1.6   0:13.05 Xorg
 2600 user      20   0  615644 131928  60148 S  12.3  3.3   0:01.77 plugin-con+
 
 1008 root      20   0  215624  62148  34868 R  [COLOR="#FF0000"]**86.0**[/COLOR]  1.6   0:15.64 Xorg
 2600 user      20   0  622556 142288  63940 S   9.3  3.6   0:02.05 plugin-con+
 
 1008 root      20   0  215624  62412  34868 R  [COLOR="#FF0000"]**90.3**[/COLOR]  1.6   0:18.36 Xorg
 2600 user      20   0  629468 152608  67732 S   7.6  3.8   0:02.28 plugin-con+
 
 1008 root      20   0  215624  62412  34868 S  [COLOR="#FF0000"]**91.3**[/COLOR]  1.6   0:21.11 Xorg
 2600 user      20   0  635124 159896  70276 S   6.0  4.0   0:02.46 plugin-con+
 
 1008 root      20   0  215756  62412  34868 R  [COLOR="#FF0000"]**90.6**[/COLOR]  1.6   0:23.84 Xorg
 2600 user      20   0  657372 169264  74052 S   6.6  4.3   0:02.66 plugin-con+
 
 1008 root      20   0  215756  62412  34868 R  [COLOR="#FF0000"]**92.6**[/COLOR]  1.6   0:26.63 Xorg
 2600 user      20   0  661980 176756  76580 S   5.0  4.4   0:02.81 plugin-con+
 
 1008 root      20   0  215756  62412  34868 R  [COLOR="#FF0000"]**92.0**[/COLOR]  1.6   0:29.40 Xorg
 2600 user      20   0  669660 185340  79108 S   5.3  4.7   0:02.97 plugin-con+
 
 1008 root      20   0  215756  62412  34868 R  [COLOR="#FF0000"]**94.9**[/COLOR]  1.6   0:32.26 Xorg
 2600 user      20   0  673012 189796  80396 S   5.0  4.8   0:03.12 plugin-con+
 
 1008 root      20   0  215896  62412  34868 R  [COLOR="#FF0000"]**94.9**[/COLOR]  1.6   0:35.12 Xorg
 2600 user      20   0  675316 192904  81652 S   8.6  4.9   0:03.38 plugin-con+
 
 1008 root      20   0  215896  62676  34868 R  [COLOR="#FF0000"]**93.0**[/COLOR]  1.6   0:37.92 Xorg
 2600 user      20   0  678876 198728  84164 S   7.0  5.0   0:03.59 plugin-con+

```

---

