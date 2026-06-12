---
title: "Homebank"
date: 2007-01-09
forum: General Help
---

### Post by Yoeri on 2007-01-09
Can anybody give me advice on installing Homebank?
[http://homebank.free.fr/]("http://homebank.free.fr/")

When running configuration script I get errors on gtk+.

---

### Post by Sef on 2007-01-09
What are the errors you are getting?  Could you copy and paste them here?

---

### Post by Yoeri on 2007-01-09
I'll post them tonight since I am at work and don't have an Ubuntu box here... I think it's just a dependency/configuration problem. I am still new to Ubuntu and don't want to break something by playing around...

---

### Post by Yoeri on 2007-01-09
I get the following when running configure (on Edgy Eft):

```
checking for DEPS... configure: error: Package requirements (gtk+-2.0 >= 2.8 glib-2.0 >= 2.2) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Sef on 2007-01-10
> I think it's just a dependency/configuration problem.

Yes you are right.

These two are missing:

 > checking for DEPS... configure: error: Package requirements (gtk+-2.0 >= 2.8 glib-2.0 >= 2.2) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found

What version of Ubuntu are you using?

---

### Post by Yoeri on 2007-01-11
I am using "Edgy Eft"

---

### Post by Adri2000 on 2007-06-08
Hi Yoeri,
If you are still using edgy, here are .deb packages I backported from feisty: [http://adrishost.homeip.net/~adri2000/ubuntu/homebank_3.2.1-0ubuntu1~edgy0.1_i386.deb](http://adrishost.homeip.net/~adri2000/ubuntu/homebank_3.2.1-0ubuntu1~edgy0.1_i386.deb) [http://adrishost.homeip.net/~adri2000/ubuntu/homebank-data_3.2.1-0ubuntu1~edgy0.1_all.deb](http://adrishost.homeip.net/~adri2000/ubuntu/homebank-data_3.2.1-0ubuntu1~edgy0.1_all.deb)
If you have upgraded to feisty, then just sudo apt-get install homebank :)

---

