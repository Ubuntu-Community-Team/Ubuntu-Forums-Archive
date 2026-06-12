---
title: "Trying to compile  uget"
date: 2020-10-18
forum: General Help
---

### Post by mringer on 2020-10-18
Lubuntu 16.04  Trying to install   uget-2.2.3     from sourceforge. 

 configure  prints this error:

```


checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: Package requirements (gtk+-3.0 >= 3.4) were not met:

No package 'gtk+-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

AFAIK there is no such package. What I have is

libgtk-3-0
libgtk-3-bin
libgtk-3-common

all latest. 

please, how can I fix? If I set the env. vars, what should I set them to?
I think the likeliest cause is that the package names are wrong in configure
or maybe in configure.ac . The relevant-I-think lines of this file are:

```
PKG_CHECK_MODULES(GTK, gtk+-3.0 >= 3.4)
PKG_CHECK_EXISTS([glib-2.0],
	PKG_CHECK_MODULES(GLIB, glib-2.0)
		PKG_CHECK_MODULES(LIBCRYPTO, libcrypto)
  PKG_CHECK_MODULES(LIBNOTIFY, libnotify)
	PKG_CHECK_EXISTS([appindicator3-0.1],
	PKG_CHECK_MODULES(APP_INDICATOR, appindicator3-0.1)
  PKG_CHECK_EXISTS([gstreamer-1.0],
  PKG_CHECK_MODULES(GSTREAMER, gstreamer-1.0)
  PKG_CHECK_MODULES(GSTREAMER, gstreamer-0.10)
  PKG_CHECK_MODULES(LIBPWMD, [libpwmd-8.0 >= 8.3.0])
```

BTW it is a very clumsy bit of programming that configure stops on the first
missing dependency. It ought to check them all.

Please any advice?

---

### Post by guiverc on 2020-10-18
I'm not sure if you're aware of it, but Lubuntu 16.04 is EOL or *end-of-life*.

If you note the [Lubuntu 16.04.5 release notes]("https://lubuntu.me/xenial-5-released/")

> Please note that this is the final point release in the 16.04 series, and is only supported until April 2019.

or a [Ubuntu 16.04.5 release notice]("http://fridge.ubuntu.com/2018/08/02/ubuntu-16-04-5-lts-released/")

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, Ubuntu Base, and Ubuntu Kylin. All the  remaining flavours will be supported for 3 years.

If you're off-line it won't be a concern, but please be aware only packages from 'main' are now getting security fixes, and it maybe worthwhile considering moving to a later 18.04 LTS release (or better yet to 20.04 LTS).

---

### Post by norobro on 2020-10-18
The pkg-config (.pc) files are in the  development packages with the headers.

In this instance you need: [https://packages.ubuntu.com/xenial/libgtk-3-dev](https://packages.ubuntu.com/xenial/libgtk-3-dev)

---

### Post by mringer on 2020-10-19
Thank you who replied.

> **norobro said:**
> 
(cut)
In this instance you need: [https://packages.ubuntu.com/xenial/libgtk-3-dev](https://packages.ubuntu.com/xenial/libgtk-3-dev)

I installed this. Then  configure  asked for  libnotify   

Again, there is no such package & I guessed that the actual package was   libnotify-dev  .  

Now configure  is asking for  gstreamer-0.10  

Again, there is no such package. But now there are ~~20 packages called   gstreamer0.10(something)

If I get past this,  configure  will then ask for   libpwmd  which also does not exist

please what are the actual names of the packages that I need?

---

### Post by sisco311 on 2020-10-19
libgstreamer1.0-dev

I would try:
```
sudo apt build-dep uget
```to install all the build dependencies of uget.

---

### Post by mringer on 2020-10-20
> **sisco311 said:**
> 

```
sudo apt build-dep uget
```to install all the build dependencies of uget.

Thank you, this worked. But on the subject of things having silly names: this program is 
not  uget  but  uget-gtk  & the manpage ditto.

---

