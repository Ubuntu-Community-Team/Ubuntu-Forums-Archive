---
title: "Radio Tuner Apps"
date: 2008-02-24
forum: General Help
---

### Post by The Avatar of Time on 2008-02-24
Hello, I have a tv/radio tuner card and was just wondering what app anyone would recommend for listening to the radio with it? I use Fluxbox. I would prefer a terminal based app but it doesnt matter that much. Recording radio would be nice but I don't care much about that either. Just want something small that works well. Thanks!

---

### Post by kostkon on 2008-02-24
> **The Avatar of Time said:**
> Hello, I have a tv/radio tuner card and was just wondering what app anyone would recommend for listening to the radio with it? I use Fluxbox. I would prefer a terminal based app but it doesnt matter that much. Recording radio would be nice but I don't care much about that either. Just want something small that works well. Thanks!

[*Gnomeradio*]("http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/") is the best radio tuner application. It is in the repositories so you can easily install it.

---

### Post by The Avatar of Time on 2008-02-24
Okay, thank you. I installed gnomeradio. When I first tried to launch it it said it could not open /dev/radio so I created /dev/radio then it would open. However now it doesn't pick up any stations (no static either but I don't know if it should do that or not, kinda acts like it has no sound). When I try to make a preset as soon as I enter the name and click to change that station it crashes. Here is what happens if I launch it from terminal:

```
william@Imladris:~$ gnomeradio

(process:13289): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
VIDIOCGAUDIO: Inappropriate ioctl for device
VIDIOCSAUDIO: Inappropriate ioctl for device
lirc_init: No such file or directory
gnomeradio-Message: Could not start lirc!

##And here is what happens as soon as I try to create a preset station##

gnomeradio-ERROR **: file prefs.c: line 417 (name_cell_edited_cb): assertion failed: (mom_ps < g_list_length(menuitems))
aborting...
Aborted (core dumped)
william@Imladris:~$ 

```

Thanks for any help.

---

### Post by harold4 on 2008-02-24
[options]("http://www.exploits.org/v4l/")

---

### Post by jtrindle on 2008-04-23
> **The Avatar of Time said:**
> Okay, thank you. I installed gnomeradio. When I first tried to launch it it said it could not open /dev/radio so I created /dev/radio then it would open. However now it doesn't pick up any stations (no static either but I don't know if it should do that or not, kinda acts like it has no sound). When I try to make a preset as soon as I enter the name and click to change that station it crashes.

Thanks for any help.

Handy help:
[http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/](http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/)

Under preferences you can set the name of your actual radio device (mine is /dev/radio0).  What do you mean you "created" /dev/radio?

My gnomeradio crashes when I try to edit the name of the station, too, so my presets are "unnamed".  If anyone can point me to the XML file to edit or another work-around that would be great.

---

### Post by Bristol Rogue on 2008-04-24
> **jtrindle said:**
> Handy help:
[http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/](http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/)

Under preferences you can set the name of your actual radio device (mine is /dev/radio0).  What do you mean you "created" /dev/radio?

My gnomeradio crashes when I try to edit the name of the station, too, so my presets are "unnamed".  If anyone can point me to the XML file to edit or another work-around that would be great.

Ive got a very similar problem with gnomeradio.  My program version is 1.7-2, hohever the help file is for 1.0, which probably doesn't help.  I found that I had only /dev/radio0 so have managed to change the radio device appropriately, however I can no longer change the station name without crashing gnomeradio.

My suspicion is that neither of us have either the correct file to store the changes in or the correct pointer.

A solution would be brill, but has anyone got one?

Should we go back a version or two, any recommendations on that score please?

:confused:

---

### Post by d90 on 2008-05-10
same problem :S

---

