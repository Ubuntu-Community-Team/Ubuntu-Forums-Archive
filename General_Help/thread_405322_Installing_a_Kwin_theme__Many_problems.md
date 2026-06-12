---
title: "Installing a Kwin theme?  Many problems"
date: 2007-04-09
forum: General Help
---

### Post by bg1256 on 2007-04-09
I have been trying to install several Kwin themes from kde-look.org on Kubuntu Dapper, and I have not been able to install any of them successfully.

I download the tarball, extract it to my home directory, open a terminal in that directory, then proceed with:

```
./configure
```

Which produces this error:

```
checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
```

I have searched in Adept for Qt 3 and installed anything that looks remotely relevant.

What am I missing or doing wrong?

Edit:

I got past the Qt dependency problem, only to find a new one:

When I run make, I get,

```
make[3]: *** [configdialog.lo] Error 1
make[3]: Leaving directory `/home/benjamin/Window Decorations/knifty-0.3.4/client/config'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/benjamin/Window Decorations/knifty-0.3.4/client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/benjamin/Window Decorations/knifty-0.3.4'
make: *** [all] Error 2

```

---

