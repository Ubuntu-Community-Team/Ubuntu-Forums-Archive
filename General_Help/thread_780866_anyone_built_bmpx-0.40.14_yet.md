---
title: "anyone built bmpx-0.40.14 yet?"
date: 2008-05-03
forum: General Help
---

### Post by NullHead on 2008-05-03
I can't seem to get it to build. It always fails with an error 02. ./configure doesn't complain about any missing dependencies ... I'm out of ideas.

Anyone???

---

### Post by NullHead on 2008-05-04
BUMP

Has **anybody**built bmpx 0.40.14 yet?

---

### Post by Zach_the_Lizard on 2008-05-04
Make sure you have all of the dependencies. I went to their website and they had this list

> 
Build Dependencies

These dependencies are for the 0.40.x versions!
Package	Minimal Version	Comment
boost	1.33.1	with filesystem, regex and iostreams extensions
glibmm	2.10.0	
gtkmm	2.10.0	 
libglademm	2.6.0	
cairomm	0.6.0	
libsexymm	0.1.9	
dbus	1.0.0	with dbus-glib
taglib	1.4		
gstreamer	0.10.14	and plugins (base, good, etc)
sqlite	3.3.11	
libofa	0.9.3	
libsoup	2.2.100	
librsvg	2.14	
cdparanoia		except on solaris
libcdio	0.70	only on solaris
libasound/alsa-lib	1.0.9	only on linux
startup-notification	0.8	optional
hal	0.5.8.1	optional
libmodplug	0.7	optional
libsidplay	1.x	optional


NOTE All these packages are most likely provided by your operating system, although they may not be of the required version (especially GLib, and possibly GStreamer). We recommend that you look to them before attempting to install the dependencies from source.

NOTE For more information about BMP and GStreamer please see BMPx and GStreamer

On Ubuntu Feisty, try (if the list is incomplete, please edit the wiki and complete it!):

sudo apt-get install libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-iostreams-dev libdbus-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev gstreamer0.10-ffmpeg gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad libtag1-dev libgtkmm-2.4-dev libglademm-2.4-dev libstartup-notification0-dev libasound2-dev libcdparanoia0-dev libsoup2.2-dev libsqlite3-dev librsvg2-dev libsexymm-dev libofa0-dev libdbus-glib-1-dev gettext 


If this doesn't work, I guess make sure you have set the right flags with ./configure.

---

### Post by NullHead on 2008-05-05
That worked! Thanks.

---

