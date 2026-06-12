---
title: "Avant WIndow Manager"
date: 2007-10-16
forum: General Help
---

### Post by Guardian-Mage on 2007-10-16
I followed the exact instructions in [http://wiki.awn-project.org/index.php?title=InstallingFromSource](http://wiki.awn-project.org/index.php?title=InstallingFromSource)
and when I execute step 6a it comes up with a command-not-found error. I tried this with the root and the user prompt, neither work. I can't find the installation files either??? Not in usr/ that I can see. Help please

---

### Post by r-mo on 2007-10-16
It should have installed in /usr/local  this is the default location for apps you compile, assuming you didn't do ./autogen.sh --prefix=/usr in step 3.  

Did you get any errors in the last few lines when you ran make? (step 4)
Did you sudo on step 5 'make install'? Did you get any errors in the last few lines?

If you want to start over, go into the avant-window-navigator directory, where you downloaded the source code to (step 2)

commands
```

sudo make uninstall
make clean

```
that *should* give you a clean system
```
./autogen.sh && make
```
Check the page of output for error messages
```
sudo make install
```
Check for error messages

then try step 6 again.

---

