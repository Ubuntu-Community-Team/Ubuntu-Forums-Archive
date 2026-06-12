---
title: "openwengo"
date: 2005-09-06
forum: General Help
---

### Post by rwabel on 2005-09-06
there is just another "skype clone" called wengo. It's opensource and alpha deb files have been released. Check their [site]("http://www.openwengo.com")

But I get the following error
```
rwabel@RALPH:~$ sudo dpkg -i wengophone_0.950-i386.deb
(Reading database ... 104715 files and directories currently installed.)
Preparing to replace wengophone 0.950-1 (using wengophone_0.950-i386.deb) ...
Unpacking replacement wengophone ...
dpkg: dependency problems prevent configuration of wengophone:
 wengophone depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing wengophone (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wengophone
```

the problem is, that the libqt3 breezy package is named different.....the package is now installed, but broken. But it's working :-)

---

### Post by samba on 2005-10-16
See the installation wiki for Skype under Breezy to solve this problem: [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto) . You simply have to change the openwengo .deb file so that it depends on the new ubuntu package libqt3-mt rather than on the former libqt3c102-mt .

ciao :-)
vincent

---

### Post by rwabel on 2005-10-16
thanks a lot for the hint!

---

### Post by oskude on 2005-12-02
yeah,

i found this openwengo through another forum today, and i can hardly wait for osx version to come out so i can drop skype :)

ps. i dont have nothing against skype (the best that i found to work on all 3OS), but when theres an open source possibility, i choose that.
pss. and if openwengo doesnt work on win98se, i atlast have a "reason" to install ubuntu on my mothers PC ;)

---

### Post by easy_target on 2005-12-31
I installed openwengo (the deb version) but I cannot get my camera to work! I have a Logitech quickcam which I believe is correctly intalled since I can use amsn's webcam function. Anybody experiencing this?

---

