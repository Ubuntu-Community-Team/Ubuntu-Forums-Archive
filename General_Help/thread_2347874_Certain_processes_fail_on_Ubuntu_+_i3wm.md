---
title: "Certain processes fail on Ubuntu + i3wm"
date: 2016-12-29
forum: General Help
---

### Post by tepedicabo on 2016-12-29
Hi,

I've installed i3 version 4.11 over Ubuntu 16.04.1, and have begun to customize it. Certain programs give similar-looking error messages when I run them (although I'm not certain they're related). For example, nm-applet gives

```
angus@angus-ThinkPad-X1-Carbon-4th:~$ nm-applet 

(nm-applet:3343): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed


```

and dunst gives

```
angus@angus-ThinkPad-X1-Carbon-4th:~$ dunst

(process:30057): GLib-CRITICAL **: g_variant_unref: assertion 'value->ref_count > 0' failed


```

Does anyone know what's going on?

Thanks

---

