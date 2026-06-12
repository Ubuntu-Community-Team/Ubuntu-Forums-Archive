---
title: "Add Remove by Sudo?"
date: 2007-12-17
forum: General Help
---

### Post by gargo2000 on 2007-12-17
For awhile I couldn't figure why when I tried loading "Add / Remove" it would load about 60% and the window would disappear.  Finally I tried in terminal with Sudo command and it loaded.  Did I do something that changed this to a root command?  If so, how do I put it back without using sudo?

Thanks

---

### Post by aysiu on 2007-12-17
Don't use *sudo* for graphical applications.

To diagnose the window disappearing, instead of going to Applications > Add/Remove, paste this command in the terminal: ```
gksu gnome-app-install
``` If any error messages appear, paste them back here.

---

### Post by gargo2000 on 2007-12-17
I ran the command line above and this is what showed up in terminal

> 
warning: could not initiate dbus

** (gnome-app-install:9748): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:9748): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed


(disregard the smilies...LOL...I dont know how to remove them)

---

### Post by aysiu on 2007-12-17
Hm. I Googled your error message and got [this](http://ubuntuforums.org/showthread.php?t=458548).

Doesn't provide a lot of hope, though.

---

