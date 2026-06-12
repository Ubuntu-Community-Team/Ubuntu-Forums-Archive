---
title: "Deja Dup fails restore"
date: 2014-04-18
forum: General Help
---

### Post by Teethdude on 2014-04-18
I wish I could figure out what was wrong. Up until a certain file, it will stop restoring. I tried several of my backups as well. Here's the error the Terminal spits out:
```
mike@mike-Laptop:~$ deja-dup --restore

** (deja-dup:3926): WARNING **: CommonUtils.vala:543: Invalid byte sequence in conversion input


(deja-dup:3926): Gtk-CRITICAL **: _gtk_widget_captured_event: assertion 'WIDGET_REALIZED_FOR_EVENT (widget, event)' failed

(deja-dup:3926): Gtk-CRITICAL **: _gtk_widget_captured_event: assertion 'WIDGET_REALIZED_FOR_EVENT (widget, event)' failed


```

Maybe there's a way to skip failed files?

Thank you for any support.

---

### Post by Teethdude on 2014-04-18
May have found a quick work-around by restoring missing files.

---

