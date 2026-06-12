---
title: "AutoHotKey hotstring attempt"
date: 2008-01-23
forum: General Help
---

### Post by peabody on 2008-01-23
Since there has been so much talk about the lack of gui based text-replacement programs for Linux, I sat down and coded up a prototype of something that has some potential.  It's a python script that can expand abbreviations from anywhere, in any program in X.  Only catch is you need to hit a shortcut key by default to start it, and it doesn't echo the abbreviations to the screen (you basically hit a shortcut key, type a sequence, and if it's a known sequence, a stream of characters is sent to your current window, otherwise input returns to the window).

Right now the shortcut key has been hardcoded to f6 mostly because on my system other shortcut keys were taken.  If f6 is taken on your system, you might receive a 'BadAccess' error if you try to run the script.

**The script requires that both the python-xlib and xmacro packages are installed**

The script is very preliminary.  Anyone with programming skills: I'd love all the feedback you can provide.  Feel free to commandeer the script and add pygtk guis, etc, etc.

URL: [http://peabody.weeman.org/autokey.py](http://peabody.weeman.org/autokey.py)

---

### Post by peabody on 2008-01-25
Sorry for a double post, but I've made some major progress on this thing...I've managed to program hotstring functionality like that in AutoHotKey (well, proof of concept-wise anyway).

It's still rough as heck, I recommend that only experienced users look at it for now.  There is a video on the new url though.

[http://peabody.weeman.org/autokey.html](http://peabody.weeman.org/autokey.html)

---

