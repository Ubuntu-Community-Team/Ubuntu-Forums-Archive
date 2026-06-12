---
title: "cmaker version error"
date: 2021-11-24
forum: General Help
---

### Post by ikob211 on 2021-11-24
Hey, take a look at the following snippet.

Although the version is 2.8.12.2 it wont work. Is there a 0ubuntu3 subversion? Because there is no such in cmake.org 

```
The following packages have unmet dependencies:
cmake-curses-gui : Depends: cmake (= 2.8.12.2-0ubuntu3)
E: Unable to correct problems, you have held broken packages.
build have failed
ivan@ubuntu:/openairinterface5g/cmake_targets$ command cmake --versioncmake version 2.8.12.2
ivan@ubuntu:/openairinterface5g/cmake_targets$
```

Thank you, ignore the crossed line!

---

### Post by Frogs Hair on 2021-11-24
Welcome to the forum, please provide some information about your Ubuntu version and what exactly you are trying to install.

---

### Post by deadflowr on 2021-11-24
It's very old, like from 14.04 or so.
Also, the packages themselves are outdated from the last versions available for 14.04.
(Last version I see was 2.8.12.2-0ubuntu6, so it's the version that the system wants isn't even available if you try.)

>  Is there a 0ubuntu3 subversion? Because there is no such in cmake.org 
The extra string is Ubuntu build specific, and not anything cmake upstream cares about.


Is there any specific reason to use such an old release of Ubuntu?

---

### Post by ikob211 on 2021-11-29
The version of Ubuntu is 14.04, 
i am using such an old version because of the package incompatibility with the latest Ubuntu versions.
The packet Im trying to download is OpenAirSoftware5g located here...
[https://github.com/simula/openairinterface5g](https://github.com/simula/openairinterface5g)

Looking forward for your reply, Thank you

---

### Post by ikob211 on 2021-11-29
I fixed the issue just by reinstalling Ubuntu, I am not sure how did it work but well it did! thank you guys.

---

