---
title: "Mate desktop + ubuntu 14.04, no bluetooth applet"
date: 2014-05-22
forum: General Help
---

### Post by bluepicaso2 on 2014-05-22
hello there,
SO i am using mate desktop, and i dont see any bluetooth applet at all.
tried 
```
sudo apt-get install mate-bluetooth
```
got 
```
Package mate-bluetooth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mate-bluetooth' has no installation candidate
```

then tried 
```
 sudo apt-get install libmatebluetoot
```
got
```
E: Package 'mate-bluetooth' has no installation candidate
harpreet@thecodingbox:~$ sudo apt-get install libmatebluetooth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libmatebluetooth


```

Please help thank you

---

### Post by mohegan on 2014-06-09
Mate 1.8 uses **blueman** now : [http://mate-desktop.org/blog/2014-03-11-mate-desktop-singing-the-bluez/]("http://http://mate-desktop.org/blog/2014-03-11-mate-desktop-singing-the-bluez/").
It's not perfect. If you prefer, you can install the mate-bluetooth package 1.6.

---

