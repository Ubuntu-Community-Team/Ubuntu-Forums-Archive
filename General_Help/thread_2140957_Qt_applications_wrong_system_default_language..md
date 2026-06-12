---
title: "Qt applications wrong system default language."
date: 2013-05-01
forum: General Help
---

### Post by richierich1986 on 2013-05-01
I have Ubuntu 13.04 AMD64 on my desktop PC and everything was peachy
until I noticed something odd that I've never had happen before:

I live in the Netherlands, so my localization is Dutch, but because of practicality 
(e.g. tutorials and instructions from other users), my system language is English US.

This has always worked well for me over the past 8 years and every
application I installed has always used the correct system language.

After installing Clementine and Bitcoin, both Qt applications, I noticed
that the language they use is Dutch, which is my localization but not,
like I mentioned before, my system default language, which is English US.
This has never happened before, when using previous versions of Ubuntu.

Does anyone know what causes this and if I can change this setting?
I am well aware I can change this per app, but I want this Qt setting to be
used system-wide. An OCD thing, I'm afraid...

Bitcoin was installed from it's own PPA, but Clementine from the
Ubuntu main repository.


Thanks in advance,

Richard.

---

### Post by Carlinhos on 2013-06-27
I'm having the exact same issue on Xubuntu 13.04, Qt applications' menus are in Portuguese even though I set English as the system language. I have also not experienced this on previous versions. Help?

---

### Post by Götz on 2013-08-21
I had the same problem after a fresh Kubuntu 13.04 installation. The installer sets the locales based on the geographical location supplied by the user.

You can see the current locales with:
```

locale

```

It seems that Qt checks the LC_NUMERIC variable to set the language, but it also works with LC_ALL, change both in  */etc/default/locale*  to the desired local, for example "en_US.UTF-8":
```

LC_NUMERIC="en_US.UTF-8"
LC_ALL="en_US.UTF-8"

```

After saving the changes, run:
```

sudo locale-gen

```
to update the locales. It is necessary to log-out and log-in again.

More information: [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

