---
title: "error launching app with wine"
date: 2012-11-04
forum: General Help
---

### Post by Codeless on 2012-11-04
I went through this

[http://ubuntuforums.org/showthread.php?t=1180031](http://ubuntuforums.org/showthread.php?t=1180031)

installed the last stable version of wine

I then downloaded orbitdownloader.

The internet seems to hole the view this application runs fine with wine

if I click the newly created desktop item to launch the app I get 

The program orbitdm.exe has encountered a serious problem and needs to close. we are sorry for the inconvenience.

any suggestions for me?

---

### Post by grahammechanical on 2012-11-04
Did you install this application using the installer in wine? For some strange reason it is called Uninstall Wine Programs. But when the utility opens it become Add/Remove Programs and you get an Install button that will let you install just as if you were on Windows.

You can also try running this program in a terminal. Then you will error messages that may give you an idea of what is going wrong.

```
wine orbitdm.exe
```

This is how I found out that a program that I wanted to run in wine was failing to load because it needed Windows true type fonts.

Regards.

---

### Post by Mark Phelps on 2012-11-04
> **Codeless said:**
> The internet seems to hole the view this application runs fine with wine

Actually -- NO.  

IF you check the actual Wine HQ website page for that page you'll find (1) it hasn't been tested in over two years, and (2) it was only tested last with Debian -- NOT Ubuntu.

And (3) you'll see the the version just before the one tested two years ago was rated GARBAGE. So if the new version is anything like that, it's not going to run, regardless of what you do.

---

