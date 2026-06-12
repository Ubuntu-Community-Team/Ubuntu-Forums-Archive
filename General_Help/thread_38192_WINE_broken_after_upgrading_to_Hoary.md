---
title: "WINE broken after upgrading to Hoary"
date: 2005-05-30
forum: General Help
---

### Post by linuxNewb on 2005-05-30
Since upgrading to hoary, I receive the following when trying to use wine (everything worked great before dist-upgrade):

```


Invoking /usr/lib/wine/wine.bin C:\Program Files\Abobe\Photoshop 7.0\Photoshp.exe ...
/usr/lib/wine/wine.bin: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
Wine failed with return code 127


```

In an attempt to fix the problem I have: 
1. installed the xdialog...deb
2. reinstalled wine and winesetuptk

Still I get this error. Thanks in advance.

---

### Post by cutOff on 2005-05-30
How did you install wine??? Have you install wine-utils package??

Try to reinstall wine again

$ sudo apt-get install --reinstall wine

Hope this helps

---

### Post by linuxNewb on 2005-05-30
Thanks for your reply. Turns out that the ubuntu/universe repos are broken, or at least the wine package on that repo is broken, because following the instructions that I found on [http://www.winehq.org](http://www.winehq.org), in /etc/apt/sources.list I commented out

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

then added

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

then

sudo apt-get update
sudo apt-get remove wine
sudo apt-get install wine

now everything works again.

---

### Post by Stefan Koopmanschap on 2005-05-31
could this also be the cause of my [Crossover Office problem](http://ubuntuforums.org/showthread.php?t=38230)?

---

### Post by niels on 2005-05-31
I am considering installing Wine too, but is the packages still broken in the Ubuntu repos?

Niels

[QUOTE=linuxNewb]Thanks for your reply. Turns out that the ubuntu/universe repos are broken, or at least the wine package on that repo is broken, because following the instructions that I found on [http://www.winehq.org](http://www.winehq.org), in /etc/apt/sources.list I commented out

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

then added

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

then

sudo apt-get update
sudo apt-get remove wine
sudo apt-get install wine

now everything works again.[/QUOTE]

---

### Post by coriolan on 2005-05-31
I am a new Ubuntu user (just installed), After adding:
```
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/
```
to /etc/apt/source.list and running # sudo apt-get install wine
it complains:
[I]E: Malformed line 28 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
$ sudo vim /etc/apt/sources.list
$ sudo apt-get install wine
E: Malformed line 28 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
[/I]
Please advice a fool, what's wrong?

---

