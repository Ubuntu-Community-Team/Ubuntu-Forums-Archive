---
title: "help installing 32 bit flash on 64 bit ubuntu"
date: 2008-01-03
forum: General Help
---

### Post by fiddilydee on 2008-01-03
I am trying to do this with help from this thread: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

These are the steps
1. Download the script.
2. Right click on the tar.gz and select "Extract Here"
3. Close all browsers.
4. Inside the folder that extracts is a "GetFlash" file, double click on it.
5. Select "Run in Terminal"

This opens script editor and I do not see such a button.

---

### Post by ~LoKe on 2008-01-03
Paste this into the terminal and follow the on screen instructions.
```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
```

---

