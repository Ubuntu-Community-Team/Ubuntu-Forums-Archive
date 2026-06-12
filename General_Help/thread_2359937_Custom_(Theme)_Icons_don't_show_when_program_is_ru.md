---
title: "Custom (Theme) Icons don't show when program is running"
date: 2017-04-29
forum: General Help
---

### Post by The Bright Side on 2017-04-29
Hey guys, I installed a cool icon theme (Buuf) and manually added some more icons that Buuf didn't have by default, like TeamViewer or Darktable, by putting the correctly named .pngs into the respective "apps" folder.

I noticed that all the program icons show up properly when I look for the programs in the "Applications" overview (running Gnome Shell), but once I run an app, its (often ugly) default icon shows up instead.

Check out the custom TeamViewer icon in the apps overview:
[http://pasteboard.co/qC26hkBk.png](http://pasteboard.co/qC26hkBk.png)

Now, check out the icon while TeamViewer is running (second to last):
[http://pasteboard.co/qD4TvyET.png](http://pasteboard.co/qD4TvyET.png)

Any idea how to make the custom icon appear also while an app is running?

---

### Post by Frogs Hair on 2017-04-29
You may have to change the icon in usr/share/applications. Right click the icon to enter properties , select the icon image , and follow the path to the icon you want to use.

---

### Post by The Bright Side on 2017-04-29
Thanks for the suggestion! I gave it a shot and then restarted Gnome Shell, but I'm still seeing the ugly default icon during execution.
[http://pasteboard.co/2GFKqwZA.png](http://pasteboard.co/2GFKqwZA.png)

---

### Post by Frogs Hair on 2017-04-29
Darktable has it's own images in the program file /pixmaps folder though I'm not sure why it defaults to those images. It follows the icon theme in use on my installation , but I haven't added any images to the icon set .

---

### Post by The Bright Side on 2017-04-30
> **Frogs Hair said:**
> Darktable has it's own images in the program file /pixmaps folder though I'm not sure why it defaults to those images. It follows the icon theme in use on my installation , but I haven't added any images to the icon set .

Oops, you're right, my bad. Darktable works! Affected apps include TeamViewer, MakeMKV, DVD-Audio Extractor (dvdae), mkvtoolnix. I'm wondering if these somehow have icons embedded in their executables and that overrides the theme settings? Just spitballin'.

I've had the same problem with other themes in the past, and the same programs. So I figure it's nothing we can really do much about, but I thought I'd post to see if anybody knows something :-)

---

### Post by Frogs Hair on 2017-04-30
Some applications store generic icons in usr/share/pixmaps also.

---

### Post by The Bright Side on 2017-04-30
Good thought! I checked but that's not it either, though. Thanks anyway!

---

