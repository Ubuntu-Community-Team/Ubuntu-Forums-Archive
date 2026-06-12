---
title: "How to change login screen image?"
date: 2021-08-16
forum: General Help
---

### Post by VanillaMozilla on 2021-08-16
Ubuntu 18.04
I would like to display a different image besides the default beaver on the login screen.  Since at least the last version I have used lightdm, but with version 18.04 I can't change the image.

I tried installing slick-greeter and adding the file name to the configuration file(s).  Here is a record of the results:
=======================================================================

```
$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm

$ cat /usr/share/lightdm/lightdm.conf.d/50-slick-greeter.conf
[Seat:*]
greeter-session=slick-greeter
[Greeter]
background="file:///usr/share/backgrounds/Icy_Grass_by_Raymond_Lavoie.jpg"

[I also tried background=/usr/share/backgrounds/Icy_Grass_by_Raymond_Lavoie.jpg ]

$ cat /etc/lightdm/slick-greeter.conf
[Greeter]
background=/usr/share/backgrounds/Icy_Grass_by_Raymond_Lavoie.jpg
```

```
$ slick-greeter --test-mode
```
shows an entirely different picture, which suggests that slick-greeter is not displaying the login screen at all.

So here are the lightdm configuration files (spaces added for legibility):
```
:$ grep -H greeter /usr/share/lightdm/lightdm.conf.d/*
/usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf:        greeter-wrapper=/usr/lib/lightdm/lightdm-greeter-session
/usr/share/lightdm/lightdm.conf.d/50-slick-greeter.conf:              greeter-session=slick-greeter
/usr/share/lightdm/lightdm.conf.d/50-slick-greeter.conf~:           greeter-session=slick-greeter
/usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf:             greeter-session=unity-greeter
```

And just for good measure:
```
$ cat 50-slick-greeter.conf
[Seat:*]
greeter-session=slick-greeter
[Greeter]
background="file:///usr/share/backgrounds/Icy_Grass_by_Raymond_Lavoie.jpg"
```

Suggestions?

---

