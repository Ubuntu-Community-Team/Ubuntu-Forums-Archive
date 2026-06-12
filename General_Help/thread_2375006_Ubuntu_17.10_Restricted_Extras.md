---
title: "Ubuntu 17.10 Restricted Extras?"
date: 2017-10-21
forum: General Help
---

### Post by Ice-Tea on 2017-10-21
[https://en.wikipedia.org/wiki/Ubuntu-restricted-extras](https://en.wikipedia.org/wiki/Ubuntu-restricted-extras)

Is the contents of the package still the same for 17.10 or has it changed?

I wondered if the contents could be installed manually without Flashplayer or IcedTea? 

Thanks

---

### Post by Impavidus on 2017-10-21
According to [this]("https://packages.ubuntu.com/artful/ubuntu-restricted-extras") and [this]("https://packages.ubuntu.com/artful/ubuntu-restricted-addons"), the ubuntu-restricted-extras package doesn't contain anything itself (it's a meta package), but pulls in some dependencies. The exact packaging has changed a bit compared to the list on wikipedia and icedtea is no longer included. The dependencies containing the actual extras are just recommended, not required, so you can skip some if you prefer. Or you can install some of those packages directly, skipping the meta package.

---

### Post by Ice-Tea on 2017-10-21
Thanks Impavidus , looks like the things i didn't want have already been removed. :)

Any idea if i need the codecs if i install Gnome-MPV?

I'm guessing the GStreamer would be needed for webpages?

---

### Post by Impavidus on 2017-10-21
Of all dependencies of ubuntu-restricted-extras, I only have gstreamer1.0-libav (required by many other packages) and the flash player, and the latter I keep disabled except for the rare video on the web that's still only available in flash. But I don't think that's enough to play a dvd on my laptop (I haven't tried since my latest install). I don't know about gnome-mpv, but if you haven't installed all codecs you need, you'll notice soon enough.

---

