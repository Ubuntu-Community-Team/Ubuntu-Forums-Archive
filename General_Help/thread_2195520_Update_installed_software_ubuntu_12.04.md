---
title: "Update installed software ubuntu 12.04"
date: 2013-12-24
forum: General Help
---

### Post by wegmarsno on 2013-12-24
Hello all,I use Ubuntu 12.04 LTS and I'm sure I've seen on forums,somewhere,that software I have installed can be safely updated leaving 12.04 "intact"and able to update security issues,kernels for 12.04,etc.,as before.  As usual,I cannot find what I want,maybe I should have went to specsavers!

My question!  what is the code for updating software,for example,"stellarium" and other software leaving 12.04 system as before and able to update and function as before software updates. Thanks and Merry Xmas to all.

---

### Post by Bashing-om on 2013-12-24
wegmarsno; Hi !

One does not selectively update any particular application. The operating system is a whole entity inter dependent on all things installed. Trying to do as you say, one will run into all kinds of dependency issues.
One should update the system as a whole:
issue the terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
is the terminal means to do so.
This will :
> 
and other software leaving 12.04 system as before and able to update and function as before software updates.

keep your system stable and up-to-date. There is the hazard of proprietary drivers that you may have installed as well as some 3rd party PPAs that you may have installed that WILL break when the system is updated. These applications that you might have installed out side of the system's ability to see is a condition you are expected to know how to deal with. Such as (re-)installing the drivers and such when broke. This situation is by definition outside the package manager's sphere of influence.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by wegmarsno on 2013-12-25
Hi Bashing-om,  Thanks for your very quick reply.   Without doubt I should have visited "specsavers."  I would have sworn that I had seen somewhere,that provided any software,such as my example Stellarium,was installed via the software manager/centre,and using 12.04 LTS,it and any other applications installed by the same method could be updated to latest versions leaving the system "unharmed."  The only application I have installed that was was not already in the repositories was "Ubuntu Tweak" and it did install via the software manager/centre.  Anyhow,you have enlightened me. Thanks again for your help and Happy festive season and New Year to You and Yours,wegmarsno.

---

