---
title: "Pidgin beta 7 compile?"
date: 2007-05-01
forum: General Help
---

### Post by SnowPunk98 on 2007-05-01
I tried to install pidgin from source last night but after installing the GTK dev kit it said I needed libxml2 installed but it already was when I did ./configure. Anyone happen to know what I'm doing wrong or have a deb for the latest build of pidgin beta 7?

---

### Post by taurus on 2007-05-01
Maybe you need to the development package of libxml2, libxml2-dev.  Can you post the complete output when you run the configure file?

```
./configure
```

---

### Post by SnowPunk98 on 2007-05-01
```
You must have libxml2 >= 2.6.0 development headers installed to build.
```

but if I apt-get libxml2 it says its already installed.

---

### Post by taurus on 2007-05-01
Try the development package, libxml2-dev.

```
sudo aptitude update
sudo aptitude install libxml2-dev
```

---

### Post by SnowPunk98 on 2007-05-01
Alright ill give that a try when I get home.

---

### Post by zerwas on 2007-05-01
I made one yesterday. Menu item in GNOME will be automatically generated.

Please backup .gaim in ~ before installing.

[Pidgin 2.0.0 Beta7]("http://rapidshare.com/files/28813389/pidgin_2.0.0beta7-1_i386.deb.html")
I'd like to hear if it worked :-)

Best regards,
zerwas

---

### Post by Qew on 2007-05-01
Just follow [these instructions](https://help.ubuntu.com/community/CompileGaim), which should work for Pidgin like it should for Gaim (well, it did for me using Debian Etch and I have done it with Gaim in Xubuntu Dapper, so it should work fine). What you need are the build-essential meta package and checkinstall (unless you want to build a "proper" deb file using debuild, etc, but I'm not going to go into that here), and run "sudo apt-get build-dep gaim" (no quotes) in your console, which will pull in the necessary build files for Gaim/Pidgin. From there, your compilation should work, and you can use checkinstall to make the deb package.

---

### Post by SnowPunk98 on 2007-05-03
I got it compiled and installed from source and its basically working but I have no sound for some reason. Anyone else have this problem or did something go wrong for me?

---

