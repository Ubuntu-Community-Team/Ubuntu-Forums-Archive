---
title: "ld.so problem with /usr/local/lib"
date: 2007-02-25
forum: General Help
---

### Post by iamleeg on 2007-02-25
Hi all,

libraries which are in /usr/local/lib do not get found by the dynamic linker.  I've added a file /etc/ld.so.conf.d/local containing "/usr/local/lib", which is readable by everyone, and have run "sudo ldconfig" on numerous occasions.  But still the libraries aren't found :-/.  I've had to add /usr/local/lib to $LD_LIBRARY_PATH to get the libs loaded, but that shouldn't be necessary....what's up?

Thanks,
iamleeg.  For we are many.

---

### Post by po0f on 2007-02-25
iamleeg,

```
[font="Courier New"]$ cat /etc/ld.so.conf
include /etc/ld.so.conf.d/*.conf
/usr/local/lib[/font]
```

Maybe try renaming your file /etc/ld.so.conf.d/local.conf?  I see a file in there that is not named like this, but maybe it'll work.

You could also try just explicitly adding /usr/local/lib in /etc/ld.so.conf like I did.  I don't have any problems with locally installed libraries not being found.  ;)

---

### Post by iamleeg on 2007-02-26
> **po0f said:**
> iamleeg,

Maybe try renaming your file /etc/ld.so.conf.d/local.conf?  I see a file in there that is not named like this, but maybe it'll work.

You could also try just explicitly adding /usr/local/lib in /etc/ld.so.conf like I did.  I don't have any problems with locally installed libraries not being found.  ;)

Ah thanks po0f, I'd noticed that other file and not added a ".conf" extension to my own ;-).  I've just hacked /etc/ld.so.conf to include /etc/ld.so.conf.d/*, and now it works wonderously.

Thanks again!  :-D

---

