---
title: "Aptitude wants to remove packages"
date: 2006-11-03
forum: General Help
---

### Post by prs on 2006-11-03
I'm running edgy for amd64 and I have a habit of executing ***sudo aptitude install*** to see if there are any installed packages that are broken.

At the moment there aren't any broken packages, but instead aptitude wants to remove packages that, at least to me, looks ok and are ones that I have actively chosen to install. Nothing indicates that the packages have been replaced or anything like that.

This is the output:

```
prs@kain:~$ sudo aptitude install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  autoconf automake1.4 autotools-dev cabextract dict-freedict-eng-swe 
  dict-freedict-swe-eng fglrx-control fglrx-kernel-source genius gparted 
  hugin inkscape libboost-thread1.33.1 libcairomm-1.0-1 libglibmm-2.4-1c2a 
  libgmp3c2 libgtkmm-2.4-1c2a libmpfr1 libpano12-0 m4 msttcorefonts 
  myspell-de-de myspell-fi myspell-sv-se ntp ntp-server ntp-simple 
  ttf-khmeros ttf-mph-2b-damase xorg-driver-fglrx-dev 
0 packages upgraded, 0 newly installed, 30 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 96.0MB will be freed.
Do you want to continue? [Y/n/?]
```

Question is, why is it that aptitude wants to remove the packages? I see no logic in it...

---

### Post by mark_g on 2006-11-03
When you remove a program, aptitude will also want to remove it's dependencies, whereas apt-get will not. So the packages are the dependencies of programs you removed. For installing, some people find aptitude better, because it handles the dependencies a bit better. For removing however, I'd personally stick with apt-get.

You might want to read this for a comparison:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by prs on 2006-11-03
Ok, that makes some sense. Although I'm intrigued as to why ntp gets in the line of fire for aptitude. 

Well, well - I just have to keep myself from pressing yes on the question above and it'll work out nicely :)

---

