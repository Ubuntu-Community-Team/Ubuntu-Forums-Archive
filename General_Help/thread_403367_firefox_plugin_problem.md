---
title: "firefox plugin problem"
date: 2007-04-06
forum: General Help
---

### Post by chr1831 on 2007-04-06
i installed my favorite ftp program (fireftp) it is a firefox plugin from [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/) but when i launch it the plugin starts to load but then it crashes no warnings no nothing please help me

[edit]
i ran firefox in the konsole and then loaded the fireftp plugin and here it the output
[debug]
chris@localhost:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(firefox-bin:7021): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' failed

(firefox-bin:7021): Gdk-CRITICAL **: gdk_window_is_viewable: assertion `window != NULL' failed

(firefox-bin:7021): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)
[/debug][/edit]

-Chris

---

### Post by aysiu on 2007-04-07
So you get that warning only after having installed FireFTP?

---

### Post by chr1831 on 2007-04-07
no when i try to launch the fireftp

---

