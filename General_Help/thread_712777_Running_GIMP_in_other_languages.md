---
title: "Running GIMP in other languages"
date: 2008-03-02
forum: General Help
---

### Post by raulih on 2008-03-02
I'm unable to run Gimp in other than the system default language. When trying I get following error:

```
$ LANG=fi gimp

(gimp:6921): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
```

I did run 

```
sudo dpkg-reconfigure locales
```

but it didn't change anything. Can someone help with this?

---

### Post by tekknokrat on 2008-03-12
you need to install ```
language-pack-gnome-fi
```

---

### Post by raulih on 2008-03-12
Didn't help. I think it's a question about some GTK language pack. Someone told to check this:

```
$ sudo dpkg-reconfigure locales
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  fi_FI.UTF-8... up-to-date
Generation complete.

```

It shows ok but doesn't help. First time i run this it did something to finnish pack, but didn¨t change anything in regard with GIMP.

---

### Post by tekknokrat on 2008-03-12
How does your locale file and output of # locale looks like?

---

### Post by raulih on 2008-03-13
```
$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

What do you mean by locale file?

---

