---
title: "How to manually scan for usb audio device?"
date: 2013-01-30
forum: General Help
---

### Post by Chiel92 on 2013-01-30
Hi,

Sometimes my m-Audio Fasttrack Pro usb soundcard doens't get recognized.  That is, it's not listed in the PulseAudio Volume Control, and no sound comes through. However, running ```
lsusb
``` gives me a list in which the soundcard is included.

How can I make the audio system aware of the usb soundcard?

PS: I currently 'solve' it by either rebooting, or keeping plugging and unplugging the usb connection till it's recognized. But this is annoying to do every time. :)

---

### Post by omeomi on 2013-01-30
Have you tried restarting pulseaudio after plugging the usb soundcard in?
```
pulseaudio -k
```

---

### Post by Chiel92 on 2013-01-30
> **omeomi said:**
> Have you tried restarting pulseaudio after plugging the usb soundcard in?
```
pulseaudio -k
```

Thanks for your reply!
I tried that, but it doesn't work.

---

### Post by Chiel92 on 2013-02-18
bump

---

### Post by slickymaster on 2013-02-18
To see what's currently connected on your USB ports use:
```
lsusb | more
```

But I don't think that this is what you're looking for regarding the issue you appear to be dealing with.

Regarding specifically your issue, I think that this thread [Create your own udev rules to control removable devices]("http://ubuntuforums.org/showthread.php?t=168221"), will probably be of great assistance.

---

