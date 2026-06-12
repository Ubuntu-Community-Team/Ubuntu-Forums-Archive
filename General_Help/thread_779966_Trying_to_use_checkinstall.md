---
title: "Trying to use checkinstall"
date: 2008-05-03
forum: General Help
---

### Post by olavjunior on 2008-05-03
```
/home/junior/Skrivebord/homebank-3.8/install-sh -d /usr/local/share/locale
chmod: changing permissions of `/usr/local/share/locale': No such file or directory
make[1]: *** [install-data-yes] Error 1
make[1]: Leaving directory `/home/junior/Skrivebord/homebank-3.8/po'
make: *** [install-recursive] Error 1

```

This is the error I get trying to use checkinstall. I've tried it on two different sources, and the other one I just didn't care and did a regular make install, and that worked out fine!

But I would reallu like to get checkinstall working, so have you any ideas what's up?

---

### Post by happyhamster on 2008-05-03
Are you using hardy heron? Try running checkinstall with the --fstrans flag:

sudo checkinstall --fstrans=no

For some info on that flag see "man checkinstall" and:
[http://checkinstall.izto.org/cklist/msg00319.html](http://checkinstall.izto.org/cklist/msg00319.html)

Good luck.

---

### Post by olavjunior on 2008-05-04
Nice :)
I'm using Hardy yes, and this little trick did it :)

Thanks!

---

### Post by kripkenstein on 2008-06-20
I had the exact same problem, and happyhamster you have fixed it. Thank you!

Edit: typo

---

### Post by havok1977 on 2008-10-21
Been having the problem quite a lot lately using checkinstall for certain packages such as the 0.9 branch of vlc.

Thanks for sharing the wrokaround!

---

