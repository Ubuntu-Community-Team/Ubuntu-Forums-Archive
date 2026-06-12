---
title: "Pidgin OTR anyone?"
date: 2007-05-08
forum: General Help
---

### Post by mahy on 2007-05-08
Hi y'all,

anybody uses Pidgin 2.0 with OTR? I compiled Pidgin and made it into a deb package using checkinstall. Then i tried gaim-otr, but it refused to compile:

```
checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 gaim >= 1.0... configure: error: glib
./configure: line 19502: exit: gtk: numeric argument required
./configure: line 19502: exit: gtk: numeric argument required

```

I guess it's because it looks for Gaim, not Pidgin. So i downloaded an unofficial pidgin-otr from [http://www.cyberdyne.org/~icebrkr/2007/05/04/unofficial-off-the-record-otr-port-to-pidgin-2-beta-7/](http://www.cyberdyne.org/~icebrkr/2007/05/04/unofficial-off-the-record-otr-port-to-pidgin-2-beta-7/)

That one compiled, was installed, and even works, but the OTR configuration is inaccessible. (the 'configure plugin' button is greyed out)

Ideas, anyone? TIA

---

### Post by mahy on 2007-05-09
Oh, don't bother, that guy just released another version of his unofficial pidgin-otr. I made it into a package using checkinstall and now it works in its entirety...

---

### Post by asymmetric on 2007-06-19
it's strange cause neither of those 2 versions works for me.. i'm not using checkinstall, i use dh_make instead, and i always receive the same problem.. 

btw, i guess it's not whining about gaim, i think glib's the problem..

---

### Post by kevdog on 2007-07-11
Yea Im getting the same error too -- cant get this dang otr package compiled no matter what I do!

```
checking for glib-2.0 >= 2.4 gtk+-2.0 >= 2.4 pidgin >= 1.0... configure: error: glib
./configure: line 20902: exit: gtk: numeric argument required
./configure: line 20902: exit: gtk: numeric argument required
```

---

