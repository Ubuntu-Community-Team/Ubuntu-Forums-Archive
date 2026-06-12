---
title: "help needed in ubuntu 8.04"
date: 2008-05-26
forum: General Help
---

### Post by damansandhu on 2008-05-26
hi,
i have installed ubuntu 8.04 and i need to install many things in it.

first of all i need display drivers , i have nvidia 9600 GT 
then i need cool audio players like xmms in ubuntu , i am unable to install xmms though terminal it says

daman@project-overkill:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

then i need some cool themes and desktop backgrounds.

---

### Post by damansandhu on 2008-05-26
also tell me some more cool multimedia applications :)

---

### Post by signseeker on 2008-05-26
> **damansandhu said:**
> hi,
i have installed ubuntu 8.04 and i need to install many things in it.

first of all i need display drivers , i have nvidia 9600 GT 
then i need cool audio players like xmms in ubuntu , i am unable to install xmms though terminal it says

daman@project-overkill:~$ sudo apt-get install xmms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

then i need some cool themes and desktop backgrounds.

From what I understand the latest nvidia drivers dont fully support the 9 series cards - but I could be wrong.

Themes from - themes.freshmeat.org

---

### Post by signseeker on 2008-05-26
> **damansandhu said:**
> also tell me some more cool multimedia applications :)

try [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Nepherte on 2008-05-26
The latest beta driver from nvidia adds support for your 9600GT:
[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

---

### Post by damansandhu on 2008-05-26
is it possible to install drivers through envy??

---

### Post by strabes on 2008-05-26
I strongly recommend against using envy. Please use the drivers in the ubuntu repositories. What, if anything, is in the System > Administration > Hardware Drivers window?

---

### Post by damansandhu on 2008-05-26
i think ubuntu repositeries dont have my graphic card model in the list

---

