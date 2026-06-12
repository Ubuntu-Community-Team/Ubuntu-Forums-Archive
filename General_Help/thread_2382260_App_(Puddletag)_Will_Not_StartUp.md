---
title: "App (Puddletag) Will Not StartUp"
date: 2018-01-11
forum: General Help
---

### Post by jooge on 2018-01-11
Hi everyone,

When I try to start Puddletag (Audio Tag Editor) only the startup logo quickly appears then disappears and the actual app (GUI) does not appear. I uninstalled it and the reinstalled it from The Software Center but still no luck.

What can I do?

Thanks in advance

---

### Post by TheFu on 2018-01-11
To troubleshoot, open a terminal and start the program. What are the messages/warnings/info shown?
Are there any command line options for that program that support debug or "verbosity" (which is common).  
Does the manpage for the program provide any hints?

---

### Post by jooge on 2018-01-11
> **TheFu said:**
> To troubleshoot, open a terminal and start the program. What are the messages/warnings/info shown?
Are there any command line options for that program that support debug or "verbosity" (which is common).  
Does the manpage for the program provide any hints?

xxxx@xxxxx:~$ puddletag 1.0.5-0
puddletag Version: 1.0.5


(python:8056): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Locale: en_US
Traceback (most recent call last):
  File "/usr/bin/puddletag", line 350, in <module>
    win = MainWin()
  File "/usr/lib/pymodules/python2.7/puddlestuff/puddletag.py", line 368, in __init__
    self.restoreSettings()
  File "/usr/lib/pymodules/python2.7/puddlestuff/puddletag.py", line 635, in restoreSettings
    status['genres'] = genres.load_genres()
  File "/usr/lib/pymodules/python2.7/puddlestuff/genres.py", line 15, in load_genres
    open(filepath, 'r').readlines()]
  File "/usr/lib/python2.7/encodings/utf_8.py", line 16, in decode
    return codecs.utf_8_decode(input, errors, True)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 0-2: invalid continuation byte


^^THat is what I got when I ran the app from the terminal.

---

### Post by TheFu on 2018-01-12
So the issue is with ```

UnicodeDecodeError: 'utf8' codec can't decode bytes in position 0-2: invalid continuation byte
```
I'm guessing a corrupted file somewhere.  Take that error, do a web-search on it. Anything?  Appears from what I saw that there is a mix of character sets being used - utf8 vs something else.

And 

> Are there any command line options for that program that support debug or "verbosity" (which is common).
Does the manpage for the program provide any hints? 

---

### Post by Yellow Pasque on 2018-01-12
[https://github.com/keithgg/puddletag/issues/350](https://github.com/keithgg/puddletag/issues/350)

---

