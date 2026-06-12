---
title: "Rhythmbox podcast feed not playing"
date: 2014-12-22
forum: General Help
---

### Post by beep3 on 2014-12-22
I encountered an odd error using Ubuntu 14.04 and Rhythmbox 3.0.2.

I've added a couple of podcast feeds which work fine. However, I now got a feed that refuses to play. The feed I'm trying to add is [http://radiobox2.omroep.nl/rss/ug/programme/2465.rss](http://radiobox2.omroep.nl/rss/ug/programme/2465.rss).

The feed is added but it only shows the last episode of the programme (it should show the 20 most recent episodes). When I try to play the episode Rhythmbox briefly shows the feed's logo before showing the text "Not Playing".

I suspect the problem is that Rhythmbox is trying to play an image file rather than the MP3. When I look at the properties of the episode the source of the feed is [http://radiobox2.omroep.nl/image/file/130257/NooitMeerSlapen.jpg](http://radiobox2.omroep.nl/image/file/130257/NooitMeerSlapen.jpg) (note the *.jpg* extention). Episodes of other podcasts (ones that are working) show either an MP3 or OGG file as the source.

I've checked if the RSS feed is valid (it is).

Has anyone suggestions as to how I can get the podcast feed working please?

---

### Post by beep3 on 2014-12-23
I solved this by installing [Quod Libet]("https://code.google.com/p/quodlibet/"). I've been using it for a couple of hours and so far so good. Feeds and internet radio works a treat; it's got a nice file browser and it plays everything I throw at it...

Any suggestions for the problems with Rhythmbox would still be welcome. It doesn't show any errors in the terminal when trying to use the podcast feed but it does show some errors when the programme is first launched:

```
(rhythmbox:8653): Gtk-CRITICAL **: gtk_css_provider_load_from_path: assertion 'path != NULL' failed
(rhythmbox:8653): GLib-GObject-CRITICAL **: object SoupServer 0x1bad160 finalized while still in-construction
(rhythmbox:8653): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.
```

Doesn't mean anything to me...

---

