---
title: "Why gstreamer?"
date: 2005-11-01
forum: General Help
---

### Post by trash-can on 2005-11-01
I'm not sure i understand why Gnome/ubuntu made choice to stick with gstreamer, i mean if it is so good, why then the first thing average ubuntu user does is install totem-xine?!
Could someone please explain this! Wouldn't it be better to just use xine backend in Gnome?

---

### Post by frenkel on 2005-11-01
It's still in development. Version 1.0 will really rock, as the design is just awesome, I think.
And why Ubuntu uses it by default? Because Gnome uses it by default, simple as that.

---

### Post by RAOF on 2005-11-01
That, and it is really, really easy for the devs to ship only free codecs, and still make it possible for people to add the non-free/patent encumbered codecs easily.  There was some discussion about using totem-xine by default, and the result was that it was a PITA to split the good codecs out from the bad.

As an added bonus, I've never really had a problem with gstreamer.  Aren't I lucky :cool:

---

### Post by trash-can on 2005-11-01
Well, it is just that yesterday i spent couple of hours trying to figure out how to get totem-gstreamer play some of the avi movies, but with no luck. I found gstreamer-pitdll plugin which is ment to be able to load win32 codecs. Unfortunately it supports only a couple of win32 codecs. After all the effort i just installed totem-xine. totem-gstreamer failed to play sound in some of the videos, also there were some other problems playing a couple of videos. Ok, I admit that gstreamer works in say 80% cases, but that is not good enough for me :(

---

### Post by frenkel on 2005-11-01
[QUOTE=trash-can].... Ok, I admit that gstreamer works in say 80% cases, but that is not good enough for me :([/QUOTE]
Not _yet_ good enough for you, as I said, the version 1.0 is going to rock ;)

---

### Post by shenki on 2005-11-01
[QUOTE=trash-can]gstreamer works in say 80% cases, but that is not good enough for me :([/QUOTE]

version 0.8 = 80% of cases

a conicidence? i think not :)

---

### Post by frenkel on 2005-11-01
[QUOTE=shenki]version 0.8 = 80% of cases

a conicidence? i think not :)[/QUOTE]
LOOOL :D

---

### Post by trash-can on 2005-11-01
Ok, I admit that mentioning number "80%" was spontanious and I actually did not make any calculations :D, it would had been better if I said that it worked in most of the cases :)

---

### Post by Michael Matthews on 2005-11-01
totem won't even start on my system (5.10). :( 

$ totem

(totem:10129): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gt k_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:10129): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gt k_accel_group_from_accel_closure (accel_closure) != NULL' failed
totem: symbol lookup error: /usr/lib/gstreamer-0.8/libgstgoom.so: undefined symb ol: gst_adapter_new

---

