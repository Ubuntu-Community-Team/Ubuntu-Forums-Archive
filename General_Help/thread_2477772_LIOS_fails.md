---
title: "LIOS fails"
date: 2022-08-07
forum: General Help
---

### Post by blodgett2 on 2022-08-07
xubuntu 22.04

 Upgraded from LTS to current version Installed Lios GUI for Tesseract 5.2.0.21-g1520, Tesstrain from git clone and Cuneiform OCR from synaptic. LIOS will not launch.
 
  Launched lios from command line these errors were reported:

```
 /usr/lib/python3/dist-packages/lios/ui/gtk/text_view.py:21: PyGIWarning:  Gtk was imported without specifying a version first. Use  gi.require_version('Gtk', '4.0') before import to ensure that the right  version gets loaded.
  from gi.repository import Gtk

/usr/lib/python3/dist-packages/lios/ui/gtk/widget.py:24: PyGIWarning: Atk was imported without specifying a version first. Use gi.require_version('Atk', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Atk

File "/usr/lib/python3/dist-packages/gi/module.py", line 123, in __getattr__
    raise AttributeError("%r object has no attribute %r" % (
AttributeError: 'gi.repository.Gtk' object has no attribute 'HSeparator' 
```


 Any ideas?

---

### Post by &amp;KyT$0P# on 2022-08-07
Have you contacted the developers of that program about those errors?

---

### Post by norobro on 2022-08-08
Looks like the github version has been updated, try it in leiu of gitlab. [https://github.com/Nalin-x-Linux/lios-3/blob/master/lios/ui/gtk/text_view.py#L22](https://github.com/Nalin-x-Linux/lios-3/blob/master/lios/ui/gtk/text_view.py#L22)

If that doesn't fix it post back.

---

### Post by blodgett2 on 2022-08-09
Installed lios from github and got a different warning.

Gtk-WARNING **: 23:58:52.428: Cannot connect attribute  'text' for cell renderer class  'lios+ui+gtk+tree_view+CellRendererToggle' since attribute does not  exist


 Fixed by adding path to /usr/local/lib/python3.10/dist-packages/lios/ocr/ocr_engine_tesseract.py


 TESSDATA_POSSIBLE_PATHS


 left other paths intact and added:


 "/usr/share/tesseract-ocr/5/tessdata"


 Worked for me. Lios launched normally.

It seems that tesseract changed its file structure from v4 to v5 and lios was unaware of this.

Found the key to the fix [here]("https://github.com/Nalin-x-Linux/lios-3/commit/d40c7db5b08558e816a143817f75f513a521e543"). Don't know if the program is fully functional, but it does initialize now.

---

