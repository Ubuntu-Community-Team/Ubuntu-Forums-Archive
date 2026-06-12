---
title: "[Q]OS X like unzip tool?"
date: 2013-08-13
forum: General Help
---

### Post by GabMus on 2013-08-13
Hello Ubuntu forums! I'd like to know if there is an unzip tool that acts like the OS X one: double click the .zip (or .tar.gz, .7z etc...) file and have it extracted inside the current directory. I am using file roller right now, but to extract a file directly I have to right click and choose "Extract here" in the menu, that isn't exactly as fast as I'd like it to be.
Thank you in advance!

---

### Post by tgalati4 on 2013-08-13
There is no way to change file roller's behavior.  It requires a click to select the destination directory.  This is helpful because if you unzip the source code for a package, you generally want to put it in a special, working directory, not simply dump it in the current location.  There are several zip utilities and you can write a script (or search for one) that you can associate with "Open with" in the file manager.

```
apropos zip
apt-cache search zip
```

So, although I agree with you the OS X extractor is convenient, the default flie roller behavior is by design.

---

