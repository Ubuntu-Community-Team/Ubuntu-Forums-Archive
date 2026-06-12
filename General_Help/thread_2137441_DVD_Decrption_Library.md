---
title: "DVD Decrption Library"
date: 2013-04-20
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-04-20
Hello,

I recenly tried to play a DVD on my Laptop; I believe the title was Chronicles Of Narnia, which is a Disney film; and Movie Player gave me a message that the disc was encrypted.  I couldn't rip it either.  It also stated that I needed to install a decryption library to read the disc.

Can anyone tell me which encryption library or libraries I should install to read this disc.

I've already installed DumpHD, which did not help.

Thanks Hannibal

---

### Post by btindie on 2013-04-20
Take a look at [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by diesch on 2013-04-20
Run
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
to install *libdvdcss*. Note that it may be illegal in your country.

---

