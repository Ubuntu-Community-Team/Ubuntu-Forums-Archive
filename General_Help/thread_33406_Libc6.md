---
title: "Libc6"
date: 2005-05-10
forum: General Help
---

### Post by DaBlade on 2005-05-10
Lately every app I try to install with apt, I get this cursed error message. Same with synaptic. Make it go away! Please! I'm starting to see it in my dreams  ](*,)  :shock: 

Lol just kidding. But can someone help me get this annoying thing away? I tried build-deps, I tried installing dev packages, I tried all kinds of things, but it still appears.
I just selected a random package to demonstrate it.

The following packages have unmet dependencies:
  xvidcap: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

---

### Post by ringding on 2005-05-19
I have same issue...wish someone would help!!!!!!

---

### Post by kiddyfurby on 2005-05-19
you can manually download the package and use dpkg -i to install it
or apt-get -t [hoary] [package]

these will allow u to install packages that requires new libc

---

### Post by ringding on 2005-05-20
Might help....  I had issues with libc6.

[Here](http://www.ubuntuforums.org/showthread.php?t=35561)

---

### Post by Fab on 2005-05-20
[QUOTE=DaBlade]Lately every app I try to install with apt, I get this cursed error message. Same with synaptic. Make it go away! Please! I'm starting to see it in my dreams  ](*,)  :shock: 

Lol just kidding. But can someone help me get this annoying thing away? I tried build-deps, I tried installing dev packages, I tried all kinds of things, but it still appears.
I just selected a random package to demonstrate it.

The following packages have unmet dependencies:
  xvidcap: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages[/QUOTE]
 i think you have marillat repos enabled, which sometimes depend on the new libc6 (and also offer it)
you should disable the marillat repos except for upgrading marillat packages

---

