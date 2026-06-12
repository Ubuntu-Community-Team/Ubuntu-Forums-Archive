---
title: "Error installing libgtk2.0-dev"
date: 2008-03-18
forum: General Help
---

### Post by unutbu on 2008-03-18
After spending years merrily frying in rpm dependency hell like a piece of low-sodium thin-sliced bacon stuck on the devil's sombrero, I was finally peeled off, kicking and screaming into the enlightened world of apt. Where the birds sing and the sun shines. So bright... so very very bright. Ouch! It's hot down here. No, is it true? I'm in apt-get hell!

```

farmer:~% sudo apt-get install libgtk2.0-dev
[...]
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

farmer:~% sudo apt-get -f install libpango1.0-dev
[...]
The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed
E: Broken packages

farmer:~% dpkg --status libpango1.0-0
[...]
Package: libpango1.0-0
Status: install ok installed
Version: 1.18.3-0ubuntu1

```

What is the best way install libgtk2.0-dev in this situation?

---

