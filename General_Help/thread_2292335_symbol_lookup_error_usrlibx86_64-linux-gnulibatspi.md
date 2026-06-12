---
title: "symbol lookup error: /usr/lib/x86_64-linux-gnu/libatspi.so.0: undefined symbol:"
date: 2015-08-27
forum: General Help
---

### Post by ankit22 on 2015-08-27
Hello everyone,

Yesterday, I cross compiled glib-2.44.1 for arm and everything was working fine. Today when I logged into the system and tried to open gedit I got the following error:

```

$ gedit
gedit: symbol lookup error: /usr/lib/x86_64-linux-gnu/libatspi.so.0: undefined symbol: g_intern_static_string

```

Then I tried opening firefox and again got a similar error
```

firefox 
XPCOMGlueLoad error for file /usr/lib/firefox/libxul.so:
/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins
Couldn't load XPCOM.

```

So, if anyone can help me out here, I will be very thankful.

Regards,
Ankit

---

### Post by ankit22 on 2015-08-27
Never mind, I figured out that the cross compiled libraries in usr/local/lib were taking precedence over usr/lib so I renamed them and now everything is fine. Next time I will make sure that before cross compiling anything I give a prefix.

---

