---
title: "Error Terminal opening with soft ware center"
date: 2012-12-06
forum: General Help
---

### Post by dieselglock on 2012-12-06
Hello,

What does this error mean

2012-12-06 19:59:36,174 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-12-06 19:59:36,274 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:34:20: Not using units is deprecated. Assuming 'px'.

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:34:22: Not using units is deprecated. Assuming 'px'.

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:56:20: Not using units is deprecated. Assuming 'px'.

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:56:22: Not using units is deprecated. Assuming 'px'.

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:60:20: Not using units is deprecated. Assuming 'px'.

(software-center:3208): Gtk-WARNING **: Theme parsing error: softwarecenter.css:60:22: Not using units is deprecated. Assuming 'px'.
2012-12-06 19:59:37,804 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-12-06 19:59:38,255 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-12-06 19:59:39,076 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.op

:-(

Please help

---

### Post by Impavidus on 2012-12-07
They're all INFOs and WARNINGs, no ERRORs. It appears the file describing your software centre window is not completely following the specifications expected by GTK, which draws the window. I wouldn't worry about those messages, many programs produce warnings like that. Your software centre is working fine.

---

### Post by dieselglock on 2012-12-07
Thank you for answering my question.

---

