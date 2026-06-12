---
title: "Desktop Effects Could Not be Enabled"
date: 2008-06-07
forum: General Help
---

### Post by Ajsplace on 2008-06-07
This is my first time posting and I am very new to Ubuntu. I am trying to use the amazing visual effects of Compiz-Fusion. However every time i attempt to change my visual effects settings in preferences I get a message saying "desktop effects could not be enabled". Please help. Here are the results of Compiz-Check.

Code:

Gathering information about your system...

Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: ATI Technologies Inc RC410 [Radeon Xpress 200M]
Driver in use: fglrx
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [FAIL]
Checking for non power of two support... [FAIL]
Checking for composite extension... [ OK ]
Checking for FBConfig... [FAIL]
Checking for hardware/setup problems.../usr/bin/fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
/usr/bin/fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
./compiz-check: line 418: [: 800: unary operator expected
./compiz-check: line 418: [: 1280: unary operator expected
[ OK ]

At least one check had to be skipped:
Error: Unable to detect fglrx driver version in use.
Ajsplace is online now Report Post   	Edit/Delete Message

---

### Post by Forlong on 2008-06-07
Please do not [cross post]("http://ubuntuforums.org/showthread.php?p=5134928#post5134928").

---

### Post by Rocket2DMn on 2008-06-07
I don't think your card is compatible with the fglrx drivers, so you should remove them.  Did you use EnvyNG to install them, or did you download the binaries from ATI's website?
You can try
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then reset xorg.conf with
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Now that you are using the open source "ati" drivers, you can follow this guide to enable desktop effects - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Post back if you have problems.

---

### Post by Ajsplace on 2008-06-08
Than alot. I will try that. You all have been very responsive to help requests. This forum is great.

---

### Post by akshayas1986 on 2008-06-15
I had the same issue too. Just reinstalled the nVidia driver and everything worked fine for me.

---

