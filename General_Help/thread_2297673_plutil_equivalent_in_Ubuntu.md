---
title: "plutil equivalent in Ubuntu?"
date: 2015-10-05
forum: General Help
---

### Post by tim135 on 2015-10-05
[COLOR=#111111][FONT=Ubuntu]I've been using [/FONT][/COLOR]plutil[COLOR=#111111][FONT=Ubuntu] (built-in in OSX) to read plists. However, I'm unable to find that on Linux's [/FONT][/COLOR]apt-get[COLOR=#111111][FONT=Ubuntu]. Does anyone have an idea which package [/FONT][/COLOR]plutil[COLOR=#111111][FONT=Ubuntu] is in? I'm currently using Ubuntu Server 14.04.3.[/FONT][/COLOR]

---

### Post by coldraven on 2015-10-06
I searched in Synaptic for "plist" and found these. I'm not sure if they are what you want. I'm running Ubuntu 14.04 64bit.
> libplist1
libplist is a library for reading and writing the Apple binary and XML
property lists format. It's part of the libimobiledevice stack, providing
access to iDevices (iPod, iPhone, iPad ...).

> libplist-utils
This package containt tools to convert Apple property list files from binary
to XML and vice-versa. It's part of the libimobiledevice stack, providing
access to iDevices (iPod, iPhone, iPad ...).

> libplist-doc
This package contains the documentation.


If you are working with images then Exiftool will also read plist files.

---

### Post by NoBugs! on 2015-10-23
I used the Python biplist library, and it works well and is easy to integrate into your scripts.

```
sudo easy_install biplist
```

---

