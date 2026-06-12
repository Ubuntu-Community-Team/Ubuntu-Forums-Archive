---
title: "Thunderbird Segmentation Fault"
date: 2007-12-10
forum: General Help
---

### Post by stinkytofu on 2007-12-10
Today, for some reason, my Thunderbird installation on Kubuntu simply stopped working. When I try to run Thunderbird, I receive the following error:

thunderbird
(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap

(Gecko:6634): Gdk-WARNING **: gdk_window_set_back_pixmap(): pixmap must have a colormap
Segmentation fault (core dumped)

Any idea what may be wrong? I have tried uninstalling and reinstalling, but still get the same error.

Phil

---

### Post by Lostincyberspace on 2007-12-10
I believe you need the gtk repositorys.

---

### Post by Partyboi2 on 2007-12-11
You could try what this person did
> Well I finally solved this problem! The solution lies in the configuration of GTK in a Kde environment. Apparently the 2 don't get along.
FYI soloution is go: System Settings --> Personal --> Appearance --> GTK Styles and fonts --> go to GTK Styles box and select "Use another style" I chose "Raleigh" and it fixed the problemActual  page
[http://ubuntuforums.org/archive/index.php/t-196805.html](http://ubuntuforums.org/archive/index.php/t-196805.html)

---

