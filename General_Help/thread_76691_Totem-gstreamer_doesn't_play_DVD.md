---
title: "Totem-gstreamer doesn't play DVD"
date: 2005-10-15
forum: General Help
---

### Post by temcat on 2005-10-15
I was hoping that totem-gstreamer would start playing DVD after the final release, but alas, it still doesn't - with the same symptoms that I had starting from Colony 4 or so. Namely, it starts playing, but very-very slowly and nonlinearly, drop-down menus remain on the screen etc. Libdvdcss2 is installed, gstreamer-plugins-multiverse are installed.

Here's what I get in the console:

temcat@ubuntu:~$ totem dvd://

(totem:9940): Gdk-WARNING **: locale not supported by Xlib

(totem:9940): Gdk-WARNING **: cannot set locale modifiers

(totem:9940): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk _accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9940): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk _accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: CHUDO_REG
libdvdnav: DVD Serial Number: 417903FE
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/temcat/.dvdnav/CHUDO_REG.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4  5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000142
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001a8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00013158
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00013aee
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00013b3b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00015eb1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00015efe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00017d51
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00017d9e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003c1194
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003c11e1
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 0
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
No accelerated IMDCT transform found
temcat@ubuntu:~$

---

### Post by Toddy on 2005-10-15
Do you have DMA enabled on your DVD drive?  Also, I find that totem-xine is much better than totem-gstreamer.

---

### Post by temcat on 2005-10-16
[QUOTE=Toddy]Do you have DMA enabled on your DVD drive?  Also, I find that totem-xine is much better than totem-gstreamer.[/QUOTE]

Yes I have DMA enabled. Out of desperation, I tried to install Totem-xine - and yay, it worked! The point is, totem-xine ceased to work to me sometime before release, so I didn't even hope that it would return to a usable state soon :-)

---

