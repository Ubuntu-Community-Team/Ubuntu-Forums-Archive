---
title: "mp3/gstreamer help"
date: 2006-08-04
forum: General Help
---

### Post by Andrew07 on 2006-08-04
Okay, so I just installed Ubuntu today. Install worked fine, but I found out I can't play my mp3's on the built in player. I did a search on the forums and found that I need gstreamer0.10-plugins-ugly. 

So, I downloaded the plugin.. went to install and got the following error:

Dependency is not satisfiable: liblame0

Something I'm doing wrong, or is there something else I need?

---

### Post by croak77 on 2006-08-04
Go here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by 3rdalbum on 2006-08-05
I think croak meant [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Because you need to enable the Universe and Multiverse repositories.

Also, you should install gstreamer0.10-plugins-good, gstreamer0.10-plugins-bad, and gstreamer0.10-plugins-ugly (yes, the good, the bad, and the ugly) for full format support.

---

### Post by deanlinkous on 2006-08-05
Doesn't ubuntu have the fluendo gstreamer mp3 plugin?

---

### Post by Skia_42 on 2006-08-05
> **3rdalbum said:**
> I think croak meant [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Because you need to enable the Universe and Multiverse repositories.

Also, you should install gstreamer0.10-plugins-good, gstreamer0.10-plugins-bad, and gstreamer0.10-plugins-ugly (yes, the good, the bad, and the ugly) for full format support.

Croak provided the correct link, it describes what plugins you need in order to play mp3 files and the repositories that have to be enabled. personally I am a fan of Automatix, it installs all of the required plugins and handles other things such as media players and dvd codecs.

---

### Post by deanlinkous on 2006-08-05
[http://packages.ubuntulinux.org/dapper/libs/gstreamer0.10-fluendo-mp3](http://packages.ubuntulinux.org/dapper/libs/gstreamer0.10-fluendo-mp3)

I really need to learn more about ubuntu I guess. What is the "universe" is it the non-supportted software or something?

---

