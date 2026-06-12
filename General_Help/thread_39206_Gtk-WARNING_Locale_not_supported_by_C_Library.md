---
title: "Gtk-WARNING Locale not supported by C Library ???"
date: 2005-06-03
forum: General Help
---

### Post by wbeck85 on 2005-06-03
A little while ago, I was fiddling with ubuntu, compiled a 2.6.11 vanilla kernel, and screwed a bunch of dependencies up while trying to update ndiswrapper using a deb file I found... Well i was required to update libc6 in order to get the new version of ndiswrapper. Installing that (using another deb which I should have just left alone) wasnt too hard. Anyway, i finally gave up trying to get my wifi card to work with the new kernel and switched back to the default hoary kernel. booted up and wireless worked fine..... However, synaptic kept giving me a broken packages warning because of the new libc6 and some related stuff and i could not apt-get anything new until I fixed these. FIxing these packaged was a pain because I had to remove a bunch of stuff and then reinstall it. However, I am finally dependency-hell free :)

However, everytime I try to run a program with the console, I get this error before the program opens. It is very annoying, I don't know if it affecting the programs, but I would like to fix it. Anyway, this is what I get:
```
wbeck85@ganganork:~$ evolution
(evolution:30611): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(evolution:30611): Gdk-WARNING **: locale not supported by C library
```

I get the Gtk-Warning every single time.

Any ideas?

---

