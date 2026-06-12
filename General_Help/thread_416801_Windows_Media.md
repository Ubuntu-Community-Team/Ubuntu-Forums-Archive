---
title: "Windows Media"
date: 2007-04-21
forum: General Help
---

### Post by Harkainos on 2007-04-21
In your Opinion what is the best Linux Program to Run the Most Windows Type Programs?
(Including /mp3 files, etc)

---

### Post by Hairy_Palms on 2007-04-21
you mean what media player to use to play music, personally i use rhythmbox because it lets me use my multimedia keys and vlc to play videos

---

### Post by GuitarRocker2562 on 2007-04-21
Songbird is very nice!

---

### Post by orb9220 on 2007-04-21
Amarok in gnome is kinda bloated but is the best full featured music organizer,player,database for large music collections.

[http://amarok.kde.org/](http://amarok.kde.org/)

And you cannot run alot of windows programs in linux.

Wine and Cedga and Crossover Office will all run some programs.

---

### Post by Harkainos on 2007-04-21
I am referring specifically to .WMV/.WMA files - I would like the best one for those that is also able to play .mp3, etc.... files.

---

### Post by Delkster on 2007-04-21
> **Harkainos said:**
> I am referring specifically to .WMV/.WMA files - I would like the best one for those that is also able to play .mp3, etc.... files.

Many media player applications actually share a common player back-end. For example Rhythmbox and the default install of Totem, as well as Banshee, use the GStreamer multimedia framework, so they get their playback capabilities such as file format and codec support from GStreamer. Any of them will play both Windows Media and mp3 if the correct plugins are installed for GStreamer.

Likewise, Xine and (as far as I know) Amarok use the Xine player back-end and thus their media support depends on what kinds of plugins you have installed for Xine. There's also a version of Totem that uses the Xine back-end so you can replace the default install with the "totem-xine" package if it seems to work better for you.

GStreamer-based players will be able to play mp3 files if you have the package gstreamer0.10-plugins-ugly installed -- you can find it in Add/Remove Applications as "GStreamer extra plugins". For Windows Media files to play in GStreamer-based applications you'll probably need "GStreamer ffmpeg video plugin".

If you prefer one of the players with a Xine back-end, look for "Xine extra plugins" in Add/Remove Applications.

For music I use Rhythmbox (which is GStreamer-based), with all GStreamer plugins installed. For videos I've installed Totem with the Xine back-end (you can find it in Add/Remove Applications by searching for Totem) with the Xine extra codecs installed. Most stuff works nicely.

I'm using Gnome as my desktop environment (that is, old good Ubuntu), so if you use KDE (that comes with Kubuntu), you may want something different. The applications generally have counterparts in the KDE world, such as Kaffeine for videos and Amarok for music.

---

### Post by Harkainos on 2007-04-21
That is a great explaination. I will stick with the standard Ubuntu 6.10 (Gnome Based) Install and update the Gstreamer Apps. Thanks a million.

---

### Post by Delkster on 2007-04-22
> **Harkainos said:**
> That is a great explaination. I will stick with the standard Ubuntu 6.10 (Gnome Based) Install and update the Gstreamer Apps. Thanks a million.

I'm not sure if the ffmpeg components in 6.10 are recent enough to have native support for WMV 8 & 9. The ffmpeg components in the newly released Ubuntu 7.04 do support those formats, as far as I know, at least experimentally. WMA should work fine in either case.

If you have a Windows license, you can probably also use the Windows codecs for WMV. This should work with 6.10, too, but I've had better success at that with Xine-based players than with GStreamer ones.

---

### Post by ronmarley1 on 2007-04-22
> **orb9220 said:**
> Amarok in gnome is kinda bloated but is the best full featured music organizer,player,database for large music collections.

[http://amarok.kde.org/](http://amarok.kde.org/)
+1

---

### Post by hendoc on 2007-04-22
Amarok and Songbird both will handle all your wma needs. Songbird is just too cool, though.

---

### Post by mjitkop on 2007-04-22
Hello everybody,

I would like to see what Songbird can do. How do you get it? I can't find it in Synaptic. :confused:

Nevermind. I found the web site. Really cool.

---

