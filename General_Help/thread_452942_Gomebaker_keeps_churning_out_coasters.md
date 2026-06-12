---
title: "Gomebaker keeps churning out coasters"
date: 2007-05-23
forum: General Help
---

### Post by pormogo on 2007-05-23
I can't seem to find out why it keeps doing this. The output just says that the write failed. When starting gnomebaker I get the following error

```
(process:28792): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
```

I am currently burning a DVD data disc at 2x while running gnomebaker through strace to see if anything pops up. Anyone have any ideas off the top of their heads?

---

