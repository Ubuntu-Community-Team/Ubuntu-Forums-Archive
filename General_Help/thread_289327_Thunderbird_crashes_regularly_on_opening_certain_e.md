---
title: "Thunderbird crashes regularly on opening certain emails"
date: 2006-10-30
forum: General Help
---

### Post by veraction on 2006-10-30
Occasionally, I get an email which causes Thunderbird to completely crash any time I try to view it. Thus far, all of these crash-causing messages have had attachments, but the attachments weren't special at all. In fact, for one of these messages, the only attachment has the exact same md5sum as the attachment from another message which works fine.

Console:
```

ezenu@smallbox:~$ mozilla-thunderbird
GTK Accessibility Module initialized
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1
(Gecko:8055): GLib-GObject-WARNING **: gsignal.c:1017: unable to lookup signal "activate" of unloaded type `MaiAtkObject'

(Gecko:8055): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `signal_id > 0' failed

** (Gecko:8055): CRITICAL **: eazel_engine_image_render: assertion `width > 0' failed
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  8055 Segmentation fault      "$prog" ${1+"$@"}
ezenu@smallbox:~$ 

```

I suppose I should submit a bug report? I'm not sure how,where,etc.

---

### Post by veraction on 2006-11-19
I discovered that the problem was with the Crux theme. After switching, it works fine for me.

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795](https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795)

---

