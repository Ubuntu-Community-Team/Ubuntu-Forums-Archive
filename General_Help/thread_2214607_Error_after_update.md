---
title: "Error after update"
date: 2014-04-02
forum: General Help
---

### Post by BlackoutWorm on 2014-04-02
Hello. Most apps have stopped working now.
For instance, dconf-editor is giving me this error:
```
(dconf-editor:5434): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referencedSegmentation fault

```
And gnome tweak tool gives me:
```
(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:56:16: Not using units is deprecated. Assuming 'px'.

(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:115:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:116:12: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:138:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:140:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:269:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:271:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:469:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:469:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:487:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:561:21: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:578:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:591:19: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:602:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:611:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:619:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:627:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:635:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:667:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:693:21: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:695:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:696:19: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:705:21: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:714:11: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:812:19: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:812:21: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:812:23: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1169:11: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1236:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1237:15: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1383:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1384:11: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1384:13: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1384:15: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1384:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1391:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1391:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1391:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1400:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1400:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1400:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1401:11: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1437:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1437:23: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1443:19: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1443:21: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1444:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:54:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:54:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:65:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:65:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:91:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:91:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:107:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: gnome-panel.css:107:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:8:15: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:8:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:14:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:22:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:42:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:42:20: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:42:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:60:17: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:60:19: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:62:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:86:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: nautilus.css:86:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: unity.css:8:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: unity.css:20:16: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: unity.css:20:18: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: unity.css:20:22: Not using units is deprecated. Assuming 'px'.


(gnome-tweak-tool:6041): Gtk-WARNING **: Theme parsing error: unity.css:21:18: Not using units is deprecated. Assuming 'px'.
WARNING : Testing for expected AutostartCondition failed: Got (None)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gtweak/utils.py", line 160, in uses_autostart_condition
    return asc.split(" ", 1)[0] == autostart_type
AttributeError: 'NoneType' object has no attribute 'split'
INFO    : GSettings missing key org.gnome.nautilus.desktop (key computer-icon-visible)
INFO    : GSettings missing key org.gnome.settings-daemon.plugins.power (key lid-close-suspend-with-external-monitor)
INFO    : GSettings missing key org.gnome.settings-daemon.plugins.power (key lid-close-battery-action)
INFO    : GSettings missing key org.gnome.settings-daemon.plugins.power (key lid-close-ac-action)


(gnome-tweak-tool:6041): Gtk-WARNING **: Style property "border-top-left-radius" is not gettable
/usr/lib/python2.7/dist-packages/gtweak/tweakview.py:86: Warning: /tmp/buildd/glib2.0-2.36.4/./gobject/gtype.c:4239: type id `0' is invalid
  self._main_window.show_all()
/usr/lib/python2.7/dist-packages/gtweak/tweakview.py:86: Warning: can't peek value table for type `<invalid>' which is not currently referenced
  self._main_window.show_all()
Segmentation fault



```

Any idea? Please help.

---

### Post by claracc on 2014-04-02
Most information is needed.

What ubuntu release, what desktop?, what update have been made, when?, also it would be useful to know hardware specs.

---

### Post by BlackoutWorm on 2014-04-02
> **claracc said:**
> Most information is needed.

What ubuntu release, what desktop?, what update have been made, when?, also it would be useful to know hardware specs.
I fixed it. It was a problem with the gtk theme.
So not related to the update.
Thanks for you help.

---

