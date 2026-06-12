---
title: "Streaming from VLC"
date: 2008-03-30
forum: General Help
---

### Post by dimas869 on 2008-03-30
I am trying to stream music with VLC but when i create a music list from adding a directory doesnt work...so i only been able to stream one single song as a server...what do i have to do to make it work for a whole list?
thanks for the advise!


here the info from the terminal and i guess the main problem is the VLC failed to read directory to stream...dont know...
here:

VLC media player 0.8.6c Janus

** (.:11641): CRITICAL **: gtk_pizza_set_size: assertion `pizza != NULL' failed
[00000304] main private: creating httpd
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/dimas/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000299] main input error: refcount is 1, delaying again (id=299,type=-7)
[00000299] main input error: waited too long, cancelling destruction (id=299,type=-7)

---

