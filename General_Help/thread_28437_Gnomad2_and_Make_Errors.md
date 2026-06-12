---
title: "Gnomad2 and Make Errors"
date: 2005-04-20
forum: General Help
---

### Post by globalspace on 2005-04-20
hi all,
i'm try to compile from sources Gnomad2 for my Creative Zen Micro because the deb packages from Synaptic doesn't found my zen which is attached to usb  :neutral: 

i have no ./configure errors ...
when i do make this is the strange error :

> massi@Pc-Massi:~/gnomad2-2.6.3$ make
Making all in src
make[1]: Entering directory `/home/massi/gnomad2-2.6.3/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.6.3\" -DPACKAGE_STRING=\"gnomad2\ 2.6.3\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.6.3\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -DXTHREADS -DORBIT2=1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libgnomeui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c: In function `display_njberror':
jukebox.c:89: warning: assignment makes pointer from integer without a cast
jukebox.c: In function `jukebox_get_idstring':
jukebox.c:117: error: structure has no member named `njbid'
jukebox.c: In function `jukebox_get_firmware':
jukebox.c:135: error: structure has no member named `njbid'
jukebox.c:141: error: structure has no member named `njbid'
jukebox.c:141: error: structure has no member named `njbid'
jukebox.c:141: error: structure has no member named `njbid'
jukebox.c: In function `jukebox_get_prodname':
jukebox.c:155: error: structure has no member named `njbid'
jukebox.c: In function `jukebox_get_power':
jukebox.c:166: error: structure has no member named `njbid'
jukebox.c: In function `jukebox_discover':
jukebox.c:334: error: `NJB_DEVICE_NJBZENMICRO' undeclared (first use in this function)
jukebox.c:334: error: (Each undeclared identifier is reported only once
jukebox.c:334: error: for each function it appears in.)
jukebox.c:337: error: `NJB_DEVICE_DELLDJ2' undeclared (first use in this function)
jukebox.c:340: error: `NJB_DEVICE_POCKETDJ' undeclared (first use in this function)
jukebox.c: In function `build_playlist_list':
jukebox.c:414: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:429: warning: assignment from incompatible pointer type
jukebox.c:431: error: structure has no member named `name'
jukebox.c:432: error: structure has no member named `plid'
jukebox.c: In function `create_tree_structure':
jukebox.c:441: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:445: warning: assignment from incompatible pointer type
jukebox.c:446: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:446: error: `track' undeclared (first use in this function)
jukebox.c:455: error: structure has no member named `name'
jukebox.c:456: error: structure has no member named `plid'
jukebox.c: In function `add_to_playlist':
jukebox.c:571: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:571: error: `pl_track' undeclared (first use in this function)
jukebox.c:572: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:579: warning: assignment from incompatible pointer type
jukebox.c:581: error: structure has no member named `plid'
jukebox.c:607: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c: In function `scan_thread':
jukebox.c:774: error: `njb_songid_t' undeclared (first use in this function)
jukebox.c:774: error: `songtag' undeclared (first use in this function)
jukebox.c:775: error: `njb_datafile_t' undeclared (first use in this function)
jukebox.c:775: error: `datatag' undeclared (first use in this function)
jukebox.c:817: error: `njb_songid_frame_t' undeclared (first use in this function)
jukebox.c:817: error: `frame' undeclared (first use in this function)
jukebox.c:857: error: `FR_FOLDER' undeclared (first use in this function)
jukebox.c: In function `hd2jb_thread':
jukebox.c:1123: error: `njb_songid_t' undeclared (first use in this function)
jukebox.c:1123: error: `songid' undeclared (first use in this function)
jukebox.c:1124: error: `njb_songid_frame_t' undeclared (first use in this function)
jukebox.c:1124: error: `frame' undeclared (first use in this function)
jukebox.c:1174: warning: passing arg 4 of `NJB_Send_Track' from incompatible pointer type
jukebox.c:1174: warning: passing arg 6 of `NJB_Send_Track' from incompatible pointer type
jukebox.c:1174: error: too few arguments to function `NJB_Send_Track'
jukebox.c:1186: warning: passing arg 4 of `NJB_Send_Track' from incompatible pointer type
jukebox.c:1186: warning: passing arg 6 of `NJB_Send_Track' from incompatible pointer type
jukebox.c:1186: error: too few arguments to function `NJB_Send_Track'
jukebox.c: In function `hd2jb_data_thread':
jukebox.c:1266: warning: passing arg 4 of `NJB_Send_File' from incompatible pointer type
jukebox.c:1266: error: too many arguments to function `NJB_Send_File'
jukebox.c: In function `remove_tracks_from_playlists':
jukebox.c:1310: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1316: warning: assignment from incompatible pointer type
jukebox.c:1317: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:1317: error: `track' undeclared (first use in this function)
jukebox.c:1335: error: structure has no member named `first'
jukebox.c:1339: error: structure has no member named `ntracks'
jukebox.c:1340: error: structure has no member named `_state'
jukebox.c:1346: error: structure has no member named `_state'
jukebox.c:1347: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c: In function `jukebox_set_metadata':
jukebox.c:1443: error: `njb_songid_t' undeclared (first use in this function)
jukebox.c:1443: error: `songid' undeclared (first use in this function)
jukebox.c:1444: error: `njb_songid_frame_t' undeclared (first use in this function)
jukebox.c:1444: error: `frame' undeclared (first use in this function)
jukebox.c:1500: error: too few arguments to function `NJB_Replace_Track_Tag'
jukebox.c: In function `jukebox_create_playlist':
jukebox.c:1531: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1536: warning: assignment makes pointer from integer without a cast
jukebox.c:1546: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c:1553: error: structure has no member named `plid'
jukebox.c: In function `jukebox_rename_playlist':
jukebox.c:1579: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1584: warning: assignment from incompatible pointer type
jukebox.c:1586: error: structure has no member named `plid'
jukebox.c:1598: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c: In function `jukebox_randomize_playlist':
jukebox.c:1643: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1649: warning: assignment from incompatible pointer type
jukebox.c:1651: error: structure has no member named `plid'
jukebox.c:1660: error: structure has no member named `ntracks'
jukebox.c:1662: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:1662: error: `current' undeclared (first use in this function)
jukebox.c:1662: error: structure has no member named `first'
jukebox.c:1663: error: `prev' undeclared (first use in this function)
jukebox.c:1668: error: structure has no member named `ntracks'
jukebox.c:1679: error: structure has no member named `ntracks'
jukebox.c:1681: error: structure has no member named `ntracks'
jukebox.c:1690: error: structure has no member named `ntracks'
jukebox.c:1692: error: syntax error before ')' token
jukebox.c:1701: error: structure has no member named `first'
jukebox.c:1702: error: structure has no member named `last'
jukebox.c:1705: error: structure has no member named `_state'
jukebox.c:1706: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c:1708: error: structure has no member named `plid'
jukebox.c: In function `jukebox_delete_track_from_playlist':
jukebox.c:1731: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1737: warning: assignment from incompatible pointer type
jukebox.c:1739: error: structure has no member named `plid'
jukebox.c:1749: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:1749: error: `track' undeclared (first use in this function)
jukebox.c:1760: error: structure has no member named `first'
jukebox.c:1764: error: structure has no member named `ntracks'
jukebox.c:1765: error: structure has no member named `_state'
jukebox.c:1769: error: structure has no member named `_state'
jukebox.c:1771: warning: passing arg 2 of `NJB_Update_Playlist' from incompatible pointer type
jukebox.c:1773: error: structure has no member named `plid'
jukebox.c: In function `jukebox_get_playlist_for_play':
jukebox.c:1878: error: `njb_playlist_t' undeclared (first use in this function)
jukebox.c:1883: warning: assignment from incompatible pointer type
jukebox.c:1884: error: structure has no member named `plid'
jukebox.c:1893: error: `njb_playlist_track_t' undeclared (first use in this function)
jukebox.c:1893: error: `track' undeclared (first use in this function)
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/massi/gnomad2-2.6.3/src'
make: *** [all-recursive] Error 1 


help please ... 
i don't know what to do  :-?

---

### Post by TravisNewman on 2005-04-21
[QUOTE=globalspace]hi all,
i'm try to compile from sources Gnomad2 for my Creative Zen Micro because the deb packages from Synaptic doesn't found my zen which is attached to usb :neutral: 

i have no ./configure errors ...
when i do make this is the strange error :

 


help please ... 
i don't know what to do  :-?[/QUOTE]
 A hint-- you don't need to compile from source, you just need to configure it-- it doesn't do that for you, unfortunately.

[http://gnomad2.sourceforge.net/?section=article]("http://gnomad2.sourceforge.net/?section=article")

the part that is important here is this part:
[b] cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ; cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /etc/hotplug/usb/nomadjukebox

[/b]The only thing is you DO need to download the souce for libnjb, but only for the nomad.usermap

---

### Post by globalspace on 2005-04-21
> **panickedthumb]A hint-- you don't need to compile from source, you just need to configure it-- it doesn't do that for you, unfortunately.

[http://gnomad2.sourceforge.net/?section=article]("http://gnomad2.sourceforge.net/?section=article")

the part that is important here is this part:
[b] cat nomad.usermap >> /etc/hotplug/usb/usb.usermap  said:**
> The only thing is you DO need to download the souce for libnjb, but only for the nomad.usermap


thanks a lot now i know what to do ...
i've done all with success but when i start gnomad2 i got this error :

> massi@Pc-Massi:~/gnomad2-2.6.3$ gnomad2
gnomad2: error while loading shared libraries: libnjb-2.0.so: cannot open shared object file: No such file or directory 

 :-?

EDIT :

i've searched libnjb-2.0.so and it is in /usr/local/lib/
i know that i must do something like Export Path ? ... well i don't know why to do .. and WHAT to do  :grin: 
sorry ! :D


EDIT2:
maybe i've done something good ... or not  :roll: 
i've done :

> 
massi@Pc-Massi:~/gnomad2-2.6.3$ export LD_LIBRARY_PATH=/usr/local/lib/


and now i can start gnome2 without error ..
but gnomad can't find my zen attached on usb :(

---

### Post by globalspace on 2005-04-21
**YUPPIE !!!!** 

sorry but i must do another post ...

ok ALL OK ! the previous error was because i forgot to uninstall the gnomad2.deb installed with synaptic !

now all is ok ... 

all work , gnomad2 recognise my zen ... BUT if i don't want the error :

> gnomad2: error while loading shared libraries: libnjb-2.0.so: cannot open shared object file: No such file or directory 

i must do every time i want to start gnomad2 

> export LD_LIBRARY_PATH=/usr/local/lib/ 

how can i do ?  :-?

---

