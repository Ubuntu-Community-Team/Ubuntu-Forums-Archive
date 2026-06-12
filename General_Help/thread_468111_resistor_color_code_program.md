---
title: "resistor color code program?"
date: 2007-06-08
forum: General Help
---

### Post by K3WHO on 2007-06-08
Can anyone recommend a resistor color code program other than gResistor? I installed gResister and no matter what I do I can't get it to start.

If here's the error if anyone might know what I could do to get gResister to work.

```
osiris@nyssa:~$ gresistor

(gresistor:7126): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Warning gresistor unsupported locale setting
Traceback (most recent call last):
  File "/usr/bin/gresistor", line 26, in ?
    bindtextdomain(app_name, locale_dir)
  File "/usr/lib/python2.4/site-packages/SimpleGladeApp.py", line 56, in bindtextdomain
    __builtins__.__dict__["_"] = lambda x : x
AttributeError: 'dict' object has no attribute '__dict__'
osiris@nyssa:~$

```

---

### Post by AnRa on 2007-06-08
Maybe you find this useful:
[http://www.ese.upenn.edu/rca/calcjs.html](http://www.ese.upenn.edu/rca/calcjs.html)
[http://www.audionotekits.com/resistorcodes.html](http://www.audionotekits.com/resistorcodes.html)
[http://www.okaphone.nl/calc/resistor.shtml](http://www.okaphone.nl/calc/resistor.shtml)

---

