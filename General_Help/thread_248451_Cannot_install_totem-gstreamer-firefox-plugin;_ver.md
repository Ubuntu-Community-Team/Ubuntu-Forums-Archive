---
title: "Cannot install totem-gstreamer-firefox-plugin; version mismatch"
date: 2006-09-01
forum: General Help
---

### Post by viciouslime on 2006-09-01
totem-gstreamer-firefox-plugin:
  Depends: totem-gstreamer (=1.4.1-0ubuntu4) but 1.4.3-0ubuntu1 is to be installed

Why is this? I noticed it about a month ago and thought totem-gstreamer must have just been update and it would be a day or so before the firefox plugin reflected the change, but it is still the case... any way around it?

---

### Post by tommcd on 2006-09-01
I get the same thing. I think it is because it depends on an older version of totem-gstreamer (1.41) than what is currently available (1.43) and the newer version of the firefox-plugin is not available yet. Just install mplayer and the mplayer plugin. They work well.
edit: I think you can revert back to the old version of gstreamer (1.41) if you really want the plugin.

---

### Post by KillerKiwi on 2006-09-01
Update your package info ctrl-r in synaptic

---

### Post by viciouslime on 2006-09-01
> **KillerKiwi said:**
> Update your package info ctrl-r in synaptic

It is up to date. Where do i find the mplayer plugin? What's it called?

EDIT: Found it, mozilla-mplayer

---

