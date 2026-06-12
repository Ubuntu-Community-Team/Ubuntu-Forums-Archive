---
title: "ccsm segmentation fault 12.10"
date: 2012-11-05
forum: General Help
---

### Post by ArcherB on 2012-11-05
When I try to launch ccsm or ubuntu-tweak, I get a segmentation fault.

```
bryan@Phenom:~$ ccsm
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
Segmentation fault (core dumped)

```

and...

```
bryan@Phenom:~$ ubuntu-tweak
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
Segmentation fault (core dumped)
```

I don't know if it matters, but I have an ATI graphics adaptor, I'm using the default non-proprietary driver, but received the same results from trying the two restricted drivers that came with the system.  I have not tried the driver downloaded directly from ATI.

HELP!

---

### Post by mc4man on 2012-11-05
It would be worth mentioning what session you are using, unity (ubuntu), or Classic (gnome-fallback

And is this a fresh install or an upgrade from 12.04?

---

### Post by ArcherB on 2012-11-05
> **mc4man said:**
> It would be worth mentioning what session you are using, unity (ubuntu), or Classic (gnome-fallback

And is this a fresh install or an upgrade from 12.04?


Good questions.

This happens in any DE I've tried.  I've tried it in Gnome2, MATE, KDE and Unity.  I don't think it's DE related.

This is a fresh install with the home directory saved on a separate partition.  However, I created a brand new user and tried it there with the same results, so I don't think it's a settings issue.

EDIT:
I just tired in Classic Gnome and Classic Gnome with no effects... same result.  I even tried sudo cssm for good measure, no effect.

---

### Post by mc4man on 2012-11-06
>  However, I created a brand new user and tried it there with the same results, so I don't think it's a settings issue.
That would seem true..
Maybe open software sources & under the the updates tab enable the proposed repo, then update your sources.  There then could be a compiz update to compiz (1:0.9.8.4+bzr3407-0ubuntu1 (quantal-proposed). If so upgrade to, log out/in & see what happens with both your user account & the new one.

If it still segfaults you may find a .crash in /var/crash/ 
That could be used to file a bug report that would shed some light on the crash
r. click on the .crash > Report.... ( you need to have or set up a launchpad account to actually file

---

### Post by mlp68 on 2012-11-28
Not sure if this has meanwhile been resolved. 

See if you have the compizconfig-backend-kconfig package installed. If it is installed, remove it. 

It is not needed as far as I can tell. The segfault happens in one of the libraries of this package. 

Good luck,

    --  mlp

---

### Post by martinico on 2012-12-10
Many thanks mlp68, I got the same problems as ArcherB, and your solution works for me :) , simply remove the compizconfig-backend-kconfig package and now everything is ok.

---

### Post by prokennexusa on 2013-03-17
Many thanks mlp68, I got the same problems as ArcherB, and your solution works for me too:P , simply remove the compizconfig-backend-kconfig package:
 
```
sudo apt-get remove compizconfig-backend-kconfig
```

and now everything is ok.

---

