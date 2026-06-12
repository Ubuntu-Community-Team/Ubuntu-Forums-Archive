---
title: "Request help building DVDStyler"
date: 2016-12-13
forum: General Help
---

### Post by m9ke2 on 2016-12-13
I would greatly appreciate some help building DVDStyler.  

I have successfully downloaded and extracted DVDStyler-3.0.2.tar.bz2 into a work directory I made for this purpose.

Running:
```
m9ke@mycomputer:~/work_dir/DVDStyler-3.0.2$ ./configure
```

I hit a couple of uninstalled dependencies which I think I was able to satisfy.  I say 'I think.." because the filenames in the errors reported did not precisely correspond to the files I found and installed.   But I think they were okay because after installing each of these, terminal did not report any further unmet dependencies -- untill I hit the next one.

Terminal now reports:
```
checking for wxWidgets static library... nochecking for wxWidgets media... no
configure: error: 
    wxWidgets media library (libwx_gtk2u_media) is missing.
```

I can't find a file either using synaptic or apt that looks like a good match for the file reported as missing (libwx_gtk2u_media)

Any assistance would be much appreciated!
m9ke

---

### Post by kc1di on 2016-12-14
Depending upon the version of ubuntu-mate your using - gtk2 may not be installed.  they are moving to gtk3 libraries. 
do a search for libgtk2.0-common, libgtk2.0-bin and libgtk2.0-0  or something like that is installed. 
lib_gtk2u_media is part of libwxgtk2.8-0  so make sure that is installed also. 
good luck

---

### Post by SeijiSensei on 2016-12-14
Since DVDStyler is in the repositories, you might be able to get all the correct dependencies installed with

```
sudo apt-get build-dep dvdstyler
```

---

### Post by m9ke2 on 2016-12-14
Thanks kc1di.   I will try those searches.

---

### Post by m9ke2 on 2016-12-14
SeljiSensi, Thank you for your reply.  If in fact DVDStyler is in the repos, then I don't need to build it myself.  

Before embarking on building it myself, i checked Synaptic for DVDStyler and tried to install via apt-get.  Neither found DVDStyler. 

  Leads me to think I may not have added a needed repo.

Do you know which repo DVDStyler is in?

---

### Post by mc4man on 2016-12-14
Your missing in 16.04  would be libwxgtk-media3.0-dev but what's not available at all would be libwxsvg-dev
So you might as well use a ppa, I had/have one for dvdstyler, ( I'm going to remove it shortly...),  but it really was because one that usually had dvdstyler builds was very slow getting it together for 16.04 
That's been taken care of so you might as well use it either to get dvdstyler or to get the missing libwxsvg-dev for a self build  - 
[https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/dvdstyler)

---

### Post by m9ke2 on 2016-12-14
mc4man, Thank you for sharing your ppa.  I successfully got dvdstyler there, without having to build it myself.

Much appreciated!

---

### Post by mc4man on 2016-12-14
> **m9ke2 said:**
> mc4man, Thank you for sharing your ppa.  I successfully got dvdstyler there, without having to build it myself.

Much appreciated!
Just to clarify, the ppa I gave  you isn't mine, it's one that has done dvdstyler for a  while. 16.04 dropped wxsvg & consequently dvdstyler which may  of lead to the delay of 16.04 builds in that ppa. In the interm I put  up a ppa to provide dvdstyler & test that it & wxsvg would work in 16.04. 
At this point the linked ppa would be users best option for dvdstyler in 16.04 and maybe  later releases.
 Maybe down the road  there is a usable snap version,  who knows..

---

