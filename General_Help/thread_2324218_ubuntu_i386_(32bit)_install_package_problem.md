---
title: "ubuntu i386 (32bit) install package problem"
date: 2016-05-11
forum: General Help
---

### Post by iPenny6 on 2016-05-11
Good day geltman


I am a new user in linux ,so i got some problem here


Make a list below and let people easy to think






1.Use MPBR and external hard disk


2.External hard disk install ubuntu 
(Ubuntu 14.04.4 LTS (Trusty Tahr) 
[https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwiL67qZvtPMAhWDlZQKHZwgD3UQFggbMAA&url=http%3A%2F%2Fcdimage.ubuntu.com%2Freleases%2F14.04%2Frelease%2F&usg=AFQjCNHRv4JPq-gjSnIh63C0ndmub4IzFw](https://www.google.com.tw/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwiL67qZvtPMAhWDlZQKHZwgD3UQFggbMAA&url=http%3A%2F%2Fcdimage.ubuntu.com%2Freleases%2F14.04%2Frelease%2F&usg=AFQjCNHRv4JPq-gjSnIh63C0ndmub4IzFw))




3.develop ARM embedded system request


so here is the question 

code:
```
sudo apt-get install git gnupg flex bison gperf build-essential zip curl libc6-dev libncurses5-dev x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386
```

result:
```
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]zip is already the newest version.[/FONT]
[FONT=arial]curl is already the newest version.[/FONT]
[FONT=arial]curl set to manually installed.[/FONT]
[FONT=arial]gnupg is already the newest version.[/FONT]
[FONT=arial]libc6-dev is already the newest version.[/FONT]
[FONT=arial]libc6-dev set to manually installed.[/FONT]
[FONT=arial]Some packages could not be installed. This may mean that you have[/FONT]
[FONT=arial]requested an impossible situation or if you are using the unstable[/FONT]
[FONT=arial]distribution that some required packages have not yet been created[/FONT]
[FONT=arial]or been moved out of Incoming.[/FONT]
[FONT=arial]The following information may help to resolve the situation:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The following packages have unmet dependencies:[/FONT]
[FONT=arial] build-essential : Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed[/FONT]
[FONT=arial] gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed[/FONT]
[FONT=arial]                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed[/FONT]
[FONT=arial] libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.6)[/FONT]
[FONT=arial]                        Recommends: libgl1-mesa-dri:i386 (>= 7.2)[/FONT]
[FONT=arial] unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed[/FONT]
[FONT=arial]                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed[/FONT]
[FONT=arial]E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/FONT]
```

here i try some action 
[http://ubuntuforums.org/showthread.php?t=2268104&page=2](http://ubuntuforums.org/showthread.php?t=2268104&page=2)

but still got same result,so anyone could help me this problem,thanks a lot!

---

### Post by ian-weisser on 2016-05-12
1) What PPAs and other non-Ubuntu software do you have installed? That is what normally causes the error message.

2) Uninstall the non-Ubuntu software; disable the sources. Ensure you have only Ubuntu Trusty and Trusty-Security and Trusty-Updates sources active.

3) Refresh your package database withthe changes sources (sudo apt update)

4) Try your install again.

---

