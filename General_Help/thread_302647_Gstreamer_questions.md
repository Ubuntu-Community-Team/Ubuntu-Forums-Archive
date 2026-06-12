---
title: "Gstreamer questions"
date: 2006-11-18
forum: General Help
---

### Post by brottman on 2006-11-18
What is the difference between these 2 packages, and do I want both, or one or the other?

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse


Also -- what is the gstreamer0.8 in synaptic for? Is it old versions?

---

### Post by bettlebrox on 2006-11-19
U can do "apt-cache show" and the package name to see the description for each.

But, the only difference appears to be:

Description: GStreamer plugins from the "bad" set (Multiverse Variant)  GStreamer is a streaming media framework, ...

Description: GStreamer plugins from the "bad" set
 GStreamer is a streaming media framework, ...

Which implies some difference! What you can do is download each package and look at the contents (use dpkg and the -c flag).

---

### Post by David Corrales on 2006-11-19
The multiverse version probably has some more codecs. Just install both :)

---

### Post by neomi on 2007-02-22
multiverse means that the package comes with copyright or legal issues

---

