---
title: "Problem with Muine"
date: 2005-04-23
forum: General Help
---

### Post by Paool on 2005-04-23
my Muine don't playing songs... :neutral: 



** Message: don't know how to handle application/x-id3

(muine:9003): libmuine-CRITICAL **: player_stop: assertion `IS_PLAYER (player)' failed

(muine:9003): GStreamer-WARNING **: push on peer of pad source:src but peer is not active

(muine:9003): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(muine:9003): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by ow50 on 2005-04-23
[QUOTE=Paool]** Message: don't know how to handle application/x-id3[/QUOTE]

I think I got this once. Reinstalling some packages with synaptic helped. You can try reinstalling libid3tag and libxine* or gstreamer*/libgstreamer* packages. Can't be more specific since I don't remember exactly what helped.

---

### Post by RickySilk on 2005-04-29
[QUOTE=ow50]I think I got this once. Reinstalling some packages with synaptic helped. You can try reinstalling libid3tag and libxine* or gstreamer*/libgstreamer* packages. Can't be more specific since I don't remember exactly what helped.[/QUOTE]


I'm having the same problem above and reinstalled all these items still same error. Anyone else dealt with this?

---

### Post by ryan[sg] on 2005-05-12
i was having that exact issue. silly me, it helps when you install the mad gstreamer plugin so it can play mp3s! works just fine now. no package reinstallation necessary :) perhaps that is what is wrong with your installations too?

- ryan

---

