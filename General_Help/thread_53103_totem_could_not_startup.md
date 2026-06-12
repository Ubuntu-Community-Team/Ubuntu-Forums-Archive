---
title: "totem could not startup"
date: 2005-07-30
forum: General Help
---

### Post by arlie on 2005-07-30
everytime i click totem i get this message: "totem could not startup". What's wrong with totem? pls help.

---

### Post by heimo on 2005-07-30
Could you run it from terminal and post the output? (hopefully some clear error messages) :)

---

### Post by arlie on 2005-07-31
[QUOTE=heimo]Could you run it from terminal and post the output? (hopefully some clear error messages) :)[/QUOTE]

Terminal output:

(totem:6808): Gdk-WARNING **: locale not supported by Xlib

---

### Post by heimo on 2005-07-31
Searching with that error message in Google revealed some information, but no obvious solution. You could try to change locale, but that probably won't fix it.
```
sudo dpkg-reconfigure locales
``` 

Do you have latest updates in your system?
```
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by stoneguy on 2005-08-01
There's a registration process for gstreamer that has to be done once for each user. Issue

     gst-register-0.8

from a terminal and totem should work.

---

### Post by arlie on 2005-08-02
[QUOTE=stoneguy]There's a registration process for gstreamer that has to be done once for each user. Issue

     gst-register-0.8

from a terminal and totem should work.[/QUOTE]
 I ran  gst-register-0.8 and this output:

root@jackal:~ # gst-register-0.8
Rebuilding global_registry (/var/lib/gstreamer/0.8/registry.xml) ...
Added plugin xwindowlistener with 0 features.
Added plugin jpeg with 5 features.
Added plugin hermescolorspace with 1 feature.
Added plugin gsm with 2 features.
Added plugin gnomevfs with 2 features.
Added plugin dvdreadsrc with 1 feature.
Added plugin dvdnavsrc with 1 feature.
Added plugin gst1394 with 1 feature.
Added plugin cdparanoia with 1 feature.
Added plugin y4menc with 1 feature.
Added plugin wavenc with 1 feature.
Added plugin volume with 1 feature.
Added plugin volenv with 1 feature.
Added plugin videotestsrc with 1 feature.
Added plugin videoscale with 1 feature.
Added plugin videorate with 1 feature.
Added plugin videomixer with 1 feature.
Added plugin gstvideofilter with 0 features.
Added plugin videodrop with 1 feature.
Added plugin videocrop with 1 feature.
Added plugin videobox with 1 feature.
Added plugin videobalance with 1 feature.
Added plugin vcdsrc with 1 feature.
Added plugin vbidec with 1 feature.
Added plugin video4linux2 with 2 features.
Added plugin video4linux with 5 features.
Added plugin udp with 2 features.
Added plugin typefindfunctions with 66 features.
Added plugin tta with 2 features.
Added plugin timeoverlay with 1 feature.
Added plugin textoverlay with 1 feature.
Added plugin gsttags with 1 feature.
Added plugin switch with 1 feature.
Added plugin subparse with 1 feature.
Added plugin stereo with 1 feature.
Added plugin speed with 1 feature.
Added plugin spectrum with 1 feature.
Added plugin snapshot with 1 feature.
Added plugin smpte with 1 feature.
Added plugin smooth with 1 feature.
Added plugin sine with 1 feature.
Added plugin silence with 1 feature.
Added plugin shout2send with 1 feature.
Added plugin rtjpeg with 2 features.
Added plugin rtp with 4 features.
Added plugin rfbsrc with 1 feature.
Added plugin games with 1 feature.
Added plugin png with 2 features.
Added plugin playondemand with 1 feature.
Added plugin playbin with 1 feature.
Added plugin passthrough with 1 feature.
Added plugin overlay with 1 feature.
Added plugin navigationtest with 1 feature.
Added plugin nassink with 1 feature.
Added plugin multipart with 2 features.
Added plugin gstmultifilesink with 1 feature.
Added plugin mulaw with 2 features.
Added plugin mpegaudioparse with 1 feature.
Added plugin mpegaudio with 1 feature.
Added plugin mpeg2sub with 1 feature.
Added plugin mpeg1videoparse with 1 feature.
Added plugin monoscope with 1 feature.
Added plugin median with 1 feature.
Added plugin level with 1 feature.
Added plugin ladspa with 0 features.
Added plugin interleave with 2 features.
Added plugin gconfelements with 2 features.
Added plugin gdkpixbuf with 2 features.
Added plugin gamma with 1 feature.
Added plugin filter with 3 features.
Added plugin ffmpegcolorspace with 1 feature.
Added plugin effectv with 8 features.
Added plugin efence with 1 feature.
Added plugin dvdlpcmdec with 1 feature.
Added plugin deinterlace with 1 feature.
Added plugin decodebin with 1 feature.
Added plugin debug with 5 features.
Added plugin colorspace with 1 feature.
Added plugin chart with 1 feature.
Added plugin cdplayer with 1 feature.
Added plugin auparse with 1 feature.
Added plugin autodetect with 2 features.
Added plugin audiorate with 1 feature.
Added plugin gstaudiofilter with 0 features.
Added plugin alphacolor with 1 feature.
Added plugin alpha with 1 feature.
Added plugin alaw with 2 features.
Added plugin ac3parse with 1 feature.
Added plugin gstvideo with 0 features.
Added plugin gstresample with 0 features.
Added plugin gstidct with 0 features.
Added plugin gstaudio with 0 features.
Added plugin gstspider with 2 features.
Added plugin gstindexers with 2 features.
Added plugin gstgetbits with 0 features.
Added plugin gstelements with 15 features.
Added plugin gstdataprotocol with 0 features.
Added plugin gstbytestream with 0 features.
Added plugin gstoptscheduler with 1 feature.
Added plugin gstoptomegascheduler with 1 feature.
Added plugin gstoptgthreadscheduler with 1 feature.
Added plugin gstfairgthreadscheduler with 1 feature.
Added plugin gstentryomegascheduler with 1 feature.
Added plugin gstentrygthreadscheduler with 1 feature.
Added plugin gstbasicomegascheduler with 1 feature.
Added plugin gstbasicgthreadscheduler with 1 feature.
Added plugin xvimagesink with 1 feature.
Added plugin ximagesink with 1 feature.
Added plugin vorbis with 4 features.
Added plugin theora with 2 features.
Added plugin speex with 2 features.
Added plugin sdlvideosink with 1 feature.
Added plugin flac with 3 features.
Added plugin dvdec with 1 feature.
Added plugin gstaf with 3 features.
Added plugin videoflip with 1 feature.
Added plugin tcp with 7 features.
Added plugin synaesthesia with 1 feature.
Added plugin smoothwave with 1 feature.
Added plugin rmdemux with 1 feature.
Added plugin qtdemux with 1 feature.
Added plugin mpegstream with 4 features.
Added plugin system_encode with 1 feature.
Added plugin modplug with 1 feature.
Added plugin mng with 2 features.
Added plugin mixmatrix with 1 feature.
Added plugin goom with 1 feature.
Added plugin flxdec with 1 feature.
Added plugin gstequalizer with 1 feature.
Added plugin dtsdec with 1 feature.
Added plugin cutter with 1 feature.
Added plugin audioscale with 1 feature.
Added plugin gstaudioconvert with 2 features.
Added plugin apetag with 1 feature.
Added plugin adder with 1 feature.
Added plugin alsa with 3 features.
Added plugin esdsink with 2 features.
Added plugin ossaudio with 3 features.
Added plugin riff with 0 features.
Added plugin wavparse with 1 feature.
Added plugin ogg with 5 features.
Added plugin matroska with 2 features.
Added plugin cdxaparse with 2 features.
Added plugin avi with 2 features.
Added plugin asf with 2 features.
Rebuilding user_registry (/root/.gstreamer-0.8/registry.xml) ...
Loaded 145 plugins with 285 features.

///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
I tried this:

root@jackal:~ # totem

and got this:

(totem:7270): Gdk-WARNING **: locale not supported by Xlib

(totem:7270): Gdk-WARNING **: cannot set locale modifiers
/root/.themes/eXperience 1.0/gtk-2.0/gtkrc:1378: Overlay image options specified without filename
/root/.themes/eXperience 1.0/gtk-2.0/gtkrc:1404: Overlay image options specified without filename

(totem:7270): Gtk-WARNING **: Unable to locate theme engine in module_path: "mgicchikn",

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): Gtk-WARNING **: Theme directory scalable/mimetypes of theme eXperienceCrystal has no size field


** (totem:7270): CRITICAL **: file cr-parser.c: line 2769 (cr_parser_new_from_buf): assertion `a_buf && a_len' failed

** (totem:7270): CRITICAL **: file cr-parser.c: line 2826 (cr_parser_set_sac_handler): assertion `a_this' failed

(totem:7270): librsvg-WARNING **: Error setting CSS SAC handler


** (totem:7270): CRITICAL **: file cr-parser.c: line 4382 (cr_parser_destroy): assertion `a_this && PRIVATE (a_this)' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): GLib-CRITICAL **: g_key_file_add_group: assertion `g_key_file_lookup_group_node (key_file, group_name) == NULL' failed

(totem:7270): Gtk-WARNING **: Theme directory scalable/mimetypes of theme eXperienceCrystal has no size field

---

### Post by swordfish on 2005-08-02
god.. not a meeeee tooo
forgive me..
 error was::Failed to open; reason unknown
 so i  gst register  0.8 also
here is return

Added plugin xwindowlistener with 0 features.
Added plugin swfdec with 1 feature.
Added plugin jpeg with 5 features.
Added plugin hermescolorspace with 1 feature.
Added plugin gsm with 2 features.
Added plugin gnomevfs with 2 features.
Added plugin dvdreadsrc with 1 feature.
Added plugin dvdnavsrc with 1 feature.
Added plugin gst1394 with 1 feature.
Added plugin cdparanoia with 1 feature.
Added plugin y4menc with 1 feature.
Added plugin wavenc with 1 feature.
Added plugin volume with 1 feature.
Added plugin volenv with 1 feature.
Added plugin videotestsrc with 1 feature.
Added plugin videoscale with 1 feature.
Added plugin videorate with 1 feature.
Added plugin videomixer with 1 feature.
Added plugin gstvideofilter with 0 features.
Added plugin videodrop with 1 feature.
Added plugin videocrop with 1 feature.
Added plugin videobox with 1 feature.
Added plugin videobalance with 1 feature.
Added plugin vcdsrc with 1 feature.
Added plugin vbidec with 1 feature.
Added plugin video4linux2 with 2 features.
Added plugin video4linux with 4 features.
Added plugin udp with 2 features.
Added plugin typefindfunctions with 49 features.
Added plugin timeoverlay with 1 feature.
Added plugin textoverlay with 1 feature.
Added plugin gsttags with 1 feature.
Added plugin synaesthesia with 1 feature.
Added plugin switch with 1 feature.
Added plugin stereo with 1 feature.
Added plugin speed with 1 feature.
Added plugin spectrum with 1 feature.
Added plugin snapshot with 1 feature.
Added plugin smpte with 1 feature.
Added plugin smoothwave with 1 feature.
Added plugin smooth with 1 feature.
Added plugin sine with 1 feature.
Added plugin silence with 1 feature.
Added plugin rtjpeg with 2 features.
Added plugin rtp with 4 features.
Added plugin png with 2 features.
Added plugin playondemand with 1 feature.
Added plugin playbin with 1 feature.
Added plugin passthrough with 1 feature.
Added plugin overlay with 1 feature.
Added plugin navigationtest with 1 feature.
Added plugin nassink with 1 feature.
Added plugin multipart with 2 features.
Added plugin gstmultifilesink with 1 feature.
Added plugin mulaw with 2 features.
Added plugin mpegaudioparse with 1 feature.
Added plugin mpegaudio with 1 feature.
Added plugin mpeg2sub with 1 feature.
Added plugin mpeg1videoparse with 1 feature.
Added plugin monoscope with 1 feature.
Added plugin median with 1 feature.
Added plugin level with 1 feature.
Added plugin ladspa with 0 features.
Added plugin interleave with 2 features.
Added plugin goom with 1 feature.
Added plugin gdkpixbuf with 2 features.
Added plugin gamma with 1 feature.
Added plugin filter with 3 features.
Added plugin ffmpegcolorspace with 1 feature.
Added plugin effectv with 8 features.
Added plugin efence with 1 feature.
Added plugin deinterlace with 1 feature.
Added plugin decodebin with 1 feature.
Added plugin debug with 5 features.
Added plugin colorspace with 1 feature.
Added plugin chart with 1 feature.
Added plugin cdplayer with 1 feature.
Added plugin auparse with 1 feature.
Added plugin audiorate with 1 feature.
Added plugin gstaudiofilter with 0 features.
Added plugin gstaudioconvert with 2 features.
Added plugin alphacolor with 1 feature.
Added plugin alpha with 1 feature.
Added plugin alaw with 2 features.
Added plugin ac3parse with 1 feature.
Added plugin alsa with 3 features.
Added plugin gstvideo with 0 features.
Added plugin gstresample with 0 features.
Added plugin gstidct with 0 features.
Added plugin gstaudio with 0 features.
Added plugin gstspider with 2 features.
Added plugin gstindexers with 2 features.
Added plugin gstgetbits with 0 features.
Added plugin gstelements with 15 features.
Added plugin gstdataprotocol with 0 features.
Added plugin gstbytestream with 0 features.
Added plugin gstoptscheduler with 1 feature.
Added plugin gstoptomegascheduler with 1 feature.
Added plugin gstoptgthreadscheduler with 1 feature.
Added plugin gstentryomegascheduler with 1 feature.
Added plugin gstentrygthreadscheduler with 1 feature.
Added plugin gstbasicomegascheduler with 1 feature.
Added plugin gstbasicgthreadscheduler with 1 feature.
Added plugin xvimagesink with 1 feature.
Added plugin ximagesink with 1 feature.
Added plugin vorbis with 4 features.
Added plugin theora with 2 features.
Added plugin speex with 2 features.
Added plugin sdlvideosink with 1 feature.
Added plugin flac with 3 features.
Added plugin dvdec with 1 feature.
Added plugin gstaf with 3 features.
Added plugin videoflip with 1 feature.
Added plugin tcp with 7 features.
Added plugin rmdemux with 1 feature.
Added plugin qtdemux with 1 feature.
Added plugin ogg with 2 features.
Added plugin mpegstream with 4 features.
Added plugin system_encode with 1 feature.
Added plugin modplug with 1 feature.
Added plugin mixmatrix with 1 feature.
Added plugin flxdec with 1 feature.
Added plugin dtsdec with 1 feature.
Added plugin cutter with 1 feature.
Added plugin audioscale with 1 feature.
Added plugin adder with 1 feature.
Added plugin esdsink with 2 features.
Added plugin ossaudio with 3 features.
Added plugin riff with 0 features.
Added plugin wavparse with 1 feature.
Added plugin matroska with 2 features.
Added plugin cdxaparse with 1 feature.
Added plugin avi with 2 features.
Added plugin asf with 2 features.
Rebuilding user_registry (/home/greg/.gstreamer-0.8/registry.xml) ...
Loaded 134 plugins with 248 features.
greg@ubuntukt7a:~ $

---

### Post by humina on 2005-09-16
the output of my locale -a command still lists C as the first locale :(

```
 $ locale -a
C
en_US
en_US.iso88591
en_US.utf8
POSIX
```

I still get the locale error, saying that locale C is not supported.

---

### Post by reedlaw on 2005-11-04
I am getting the same error but from Gimp.  Every time I open Gimp and create a new document Gimp crashes.

---

### Post by ManongTenchi on 2005-11-17
I'm also getting the same type of error in VLC, and many other things i run in the terminal:



[B]perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_CTYPE to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_MESSAGES to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory
[/B]


I get a error message box in VLC saying:
**Cannot set locale to "**


I haven't been able to find out much else about this.

---

