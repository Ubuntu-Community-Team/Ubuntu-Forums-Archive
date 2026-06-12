---
title: "problems with pygtk (perhaps instalation)?"
date: 2007-02-25
forum: General Help
---

### Post by EarlGrey on 2007-02-25
Hello I have been googling for two hours but did not find a solution. I installed pygtk lib and I am trying to start with some easy script such as this:

```
import gtk
b = gtk.Button("Hello")
w = gtk.Window()
w.add(b)
w.show_all()
gtk.main()
```

When I try it from a python console, all is fine, but when I save it into a file and try to run that, I get a strange message:

```
Traceback (most recent call last):
  File "aaa.py", line 3, in ?
    import gtk
  File "/home/martin/python/gtk.py", line 11, in ?
    window = gtk.Window()
AttributeError: 'module' object has no attribute 'Window'
```

Anybody idea as to what to do? Thanks alot!! Could it perhaps be a wrong instalation?

---

