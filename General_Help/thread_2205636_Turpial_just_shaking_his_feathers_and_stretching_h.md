---
title: "Turpial just shaking his feathers and stretching his wings"
date: 2014-02-15
forum: General Help
---

### Post by dannyboy79 on 2014-02-15
I am looking for a twitter client and I am trying to use Trupial. I added the ppa and installed it. I launch it and it just says its shaking his feathers and stretching his wings and never finishes so I can add my twitter account. Anyone else have a solution? Here's teh terminal output from launching it.
```
DEBUG::Using gst as sound system
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/turpial/ui/qt/main.py", line 592, in after_core_initialized
    width, height = self.core.get_window_size()
  File "/usr/lib/python2.7/dist-packages/turpial/ui/qt/worker.py", line 509, in get_window_size
    config['Window']['size'] = "320,480"
KeyError: 'Window'
/usr/lib/python2.7/dist-packages/turpial/ui/qt/main.py:234: GtkWarning: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
  self.app.exec_()

```

---

