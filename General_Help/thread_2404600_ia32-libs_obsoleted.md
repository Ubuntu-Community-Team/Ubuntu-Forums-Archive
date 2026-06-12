---
title: "ia32-libs obsoleted?"
date: 2018-10-25
forum: General Help
---

### Post by shanasman450 on 2018-10-25
I'm looking for any way to get this library. I'm trying to play MX Simulator on Ubuntu 18.04.1 (which I've done before by the way). I switched to Linux Mint 19 for a few weeks and, last night, came back to Ubuntu because Mint didn't play nice with the MX Sim and now this happens.

---

### Post by &amp;KyT$0P# on 2018-10-25
ia32-libs has been obsolete for a long time.  You need to determine which specific 32-bit libraries your program needs, then install those 32-bit libraries.

Installing 32-bit libraries is like installing any other package, except that you add [FONT=Courier New]:i386[/FONT] on the end of each package name.  So, for example, if the libraries packages were named [FONT=Courier New]<lib1>[/FONT] and [FONT=Courier New]<lib2>[/FONT], you would run this in Terminal -
```
sudo apt-get install <lib1>:i386 <lib2>:i386
```

---

