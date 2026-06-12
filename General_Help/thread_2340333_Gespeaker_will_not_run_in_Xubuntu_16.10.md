---
title: "Gespeaker will not run in Xubuntu 16.10"
date: 2016-10-17
forum: General Help
---

### Post by rattskjelke on 2016-10-17
I installed Gespeaker in Xubuntu 16.10 but it will not work.
If I try to run it from the menu nothing happens.
If I try to run it in a terminal I get:
```
$ gespeaker
loading available plugins...
Traceback (most recent call last):
  File "gespeaker.py", line 46, in <module>
    imp.load_module(name, file, pathname, description)
  File "/usr/share/gespeaker/plugins/plugin_dbus/__init__.py", line 28, in <module>
    import dbus
ImportError: No module named dbus
```

Same thing happens if I try to run "gespeaker --help".

Does anybody know how to fix this?

---

### Post by bashiergui on 2016-10-18
You are missing a module called dbus, which is a dependency for gespeaker. 
You can try to install the missing module following this: 
[http://stackoverflow.com/questions/37521162/how-solve-importerror-no-module-named-dbus](http://stackoverflow.com/questions/37521162/how-solve-importerror-no-module-named-dbus)

If you find another missing dependency (which you'll know because you'll get a new error when running gespeaker), then I recommend following the instructions to download the deb from the gespeaker website: [http://www.muflone.com/gespeaker/english/install.html](http://www.muflone.com/gespeaker/english/install.html)

---

### Post by rattskjelke on 2016-10-20
16.10 comes with dbus already installed.
I went back to Xubuntu 16.04.1 LTS and got the same error message. It also came with dbus installed.
I think I figured out gespeaker needs python-dbus so I installed that and it works now on 16.04.1 LTS.
I'm not going to reinstall 16.10 and verify if python-dbus fixes gesepaker there too.

---

