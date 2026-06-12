---
title: "opera sluggishness"
date: 2007-05-31
forum: General Help
---

### Post by jetpig on 2007-05-31
i installed opera (apt-get install opera-static) on kubuntu 7.04 and it seems oddly sluggish.  i get one to two second lag when i try and change tabs for example.  any ideas?

specs:
a64 3800+
gig of ram
gf 8800 GTS
kubuntu 7.04

---

### Post by Colonel Kilkenny on 2007-05-31
You could try to start it from console and see if it prints out something odd.
Check also opera --debughelp and [http://my.opera.com/forums](http://my.opera.com/forums)

And maybe you could try shared version instead of opera-static. It worked for me on 64-bit Ubuntu.

---

### Post by zvacet on 2007-05-31
Download it from this page

[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by jetpig on 2007-05-31
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

that's what i got at the console

i've tried both the shared and the static, same issue.  gonna try the package from the website now.

---

### Post by jetpig on 2007-06-01
bump

---

### Post by Colonel Kilkenny on 2007-06-02
Those errors come because Opera cannot find Java. It shouldn't have anything to do with your  problem...

Maybe someone at my.opera.com/forums will be able to help. There is something wrong with current build of Opera as many people are complaining about similar problems.

---

### Post by der_joachim on 2007-06-02
I use the Opera version from the official Opera repository and it is waaaay faster than Firefox on my KDE rig.

Just paste the following  line in your /etc/apt/sources.list
```

deb http://deb.opera.com/opera testing non-free

```

Perhaps you should remove the old version from your system first.

---

### Post by Joseaa on 2007-06-13
Set the environment variable OPERA_NUM_XSHM=0 and see if it makes any difference.

---

