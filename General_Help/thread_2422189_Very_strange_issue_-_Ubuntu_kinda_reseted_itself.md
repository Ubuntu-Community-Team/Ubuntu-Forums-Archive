---
title: "Very strange issue - Ubuntu kinda reseted itself"
date: 2019-07-03
forum: General Help
---

### Post by starwars-geek98 on 2019-07-03
Hello all,

Today I booted my machine, logged in as usual only to find out that ubuntu had reseted it self (kinda). What I mean, is that it messed my favourite apps in the sidebar and now it has what you find in a clean installation, I haven't got a second language (only english), a lot of the system is in english and not in my language, and now I can't see the other disks on my system, just the root heck it even installed thunderbird that I did not have installed (I chose the minimal install). My files are ok though. Yesterday I was installing gtk following the instuctions from their site but did not finish. But the system was well. I don't know what may hava happened... Anybody knows something?

System: Ubuntu 19.04
Kernel: Linux 5.0.0-20-generic

---

### Post by cruzer001 on 2019-07-03
> Yesterday I was installing
Packages will not install themselves.  Check to see what/when a package was installed.
```
grep " install " /var/log/dpkg.log
```

---

### Post by starwars-geek98 on 2019-07-03
Thanks for your reply,

I ran the command and gave me an expected log of installments as I did last night:
```

2019-07-03 01:50:50 install ninja-build:amd64 <none> 1.8.2-1
2019-07-03 01:50:51 install meson:all <none> 0.49.0-2ubuntu1
2019-07-03 01:56:48 install uuid-dev:amd64 <none> 2.33.1-0.1ubuntu2
2019-07-03 01:56:48 install libblkid-dev:amd64 <none> 2.33.1-0.1ubuntu2
2019-07-03 01:56:49 install libmount-dev:amd64 <none> 2.33.1-0.1ubuntu2
2019-07-03 02:13:44 install libjs-jquery:all <none> 3.3.1~dfsg-1
2019-07-03 02:13:45 install freetype2-doc:all <none> 2.9.1-3
2019-07-03 02:13:46 install javascript-common:all <none> 11
2019-07-03 02:13:46 install libcairo-script-interpreter2:amd64 <none> 1.16.0-4
2019-07-03 02:13:47 install libexpat1-dev:amd64 <none> 2.2.6-1ubuntu0.19.04
2019-07-03 02:13:47 install zlib1g-dev:amd64 <none> 1:1.2.11.dfsg-1ubuntu2
2019-07-03 02:13:48 install libpng-dev:amd64 <none> 1.6.36-6
2019-07-03 02:13:49 install libfreetype6-dev:amd64 <none> 2.9.1-3
2019-07-03 02:13:49 install libfontconfig1-dev:amd64 <none> 2.13.1-2ubuntu2
2019-07-03 02:13:50 install libxrender-dev:amd64 <none> 1:0.9.10-1
2019-07-03 02:13:51 install x11proto-xext-dev:all <none> 2018.4-4
2019-07-03 02:13:51 install libxext-dev:amd64 <none> 2:1.3.3-1
2019-07-03 02:13:52 install libpixman-1-dev:amd64 <none> 0.36.0-1
2019-07-03 02:13:52 install libxcb-render0-dev:amd64 <none> 1.13.1-2
2019-07-03 02:13:53 install libxcb-shm0-dev:amd64 <none> 1.13.1-2
2019-07-03 02:13:53 install libffi-dev:amd64 <none> 3.2.1-9
2019-07-03 02:13:54 install python3-lib2to3:all <none> 3.7.3-1ubuntu1
2019-07-03 02:13:55 install python3-distutils:all <none> 3.7.3-1ubuntu1
2019-07-03 02:13:55 install libglib2.0-dev-bin:amd64 <none> 2.60.4-0ubuntu0.19.04.1
2019-07-03 02:13:56 install libpcre16-3:amd64 <none> 2:8.39-12
2019-07-03 02:13:57 install libpcre32-3:amd64 <none> 2:8.39-12
2019-07-03 02:13:58 install libpcrecpp0v5:amd64 <none> 2:8.39-12
2019-07-03 02:13:58 install libpcre3-dev:amd64 <none> 2:8.39-12
2019-07-03 02:13:59 install libsepol1-dev:amd64 <none> 2.8-1
2019-07-03 02:13:59 install libselinux1-dev:amd64 <none> 2.8-1build2
2019-07-03 02:14:00 install libglib2.0-dev:amd64 <none> 2.60.4-0ubuntu0.19.04.1
2019-07-03 02:14:01 install libcairo2-dev:amd64 <none> 1.16.0-4
2019-07-03 02:14:01 install libpng-tools:amd64 <none> 1.6.36-6
2019-07-03 02:18:06 install libxft-dev:amd64 <none> 2.3.2-2
2019-07-03 02:21:06 install gir1.2-harfbuzz-0.0:amd64 <none> 2.3.1-1
2019-07-03 02:21:07 install icu-devtools:amd64 <none> 63.1-6
2019-07-03 02:21:08 install libgraphite2-dev:amd64 <none> 1.3.13-7
2019-07-03 02:21:08 install libharfbuzz-gobject0:amd64 <none> 2.3.1-1
2019-07-03 02:21:09 install libicu-dev:amd64 <none> 63.1-6
2019-07-03 02:21:11 install libharfbuzz-dev:amd64 <none> 2.3.1-1
2019-07-03 02:21:58 install libdatrie-dev:amd64 <none> 0.2.12-2
2019-07-03 02:21:59 install libthai-dev:amd64 <none> 0.1.28-2
2019-07-03 02:57:54 install libfribidi-dev:amd64 <none> 1.0.5-3.1
2019-07-03 02:59:46 install cmake-data:all <none> 3.13.4-1
2019-07-03 02:59:48 install libjsoncpp1:amd64 <none> 1.7.4-3
2019-07-03 02:59:50 install librhash0:amd64 <none> 1.3.8-1
2019-07-03 02:59:51 install libuv1:amd64 <none> 1.24.1-1
2019-07-03 02:59:51 install cmake:amd64 <none> 3.13.4-1

```
Thunderbird is nowhere to be seen, and all of these are packages that gtk wants in order to install it to your system, so I did just that. I don't see the reason for Ubuntu to reset itself...

---

### Post by cruzer001 on 2019-07-03
So looks like thunderbird has been there for a while.  Dig deeper just to find out.
```
zcat /var/log/dpkg.log.* | grep -i "installed" | grep thunderbird
```

---

### Post by cruzer001 on 2019-07-03
ps

using code tags

[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by starwars-geek98 on 2019-07-03
First of all, I ran this command but it gave me an error back BUT it seems that thunderbird was already in my system but I wasn't aware of it so sorry for the misleading info... My bad. Secondly, I did some research and it seems that by installing these libraries for gtk+ it broke Gnome. I even installed the keyboard-language and tidied up the icons in the dock to check and after restarting the system was back to the same state, it had resaulted back to def. It seems that it doesn't know where to store the settings and preferences, so it saves them in memory but ofcourse it'll be wiped after reboot. So, because I didn't want to mess it up even more I did a backup and formated. I must be more carefull the next time. Thank you for your help nonetheless!

---

