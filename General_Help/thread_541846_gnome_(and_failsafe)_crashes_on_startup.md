---
title: "gnome (and failsafe) crashes on startup"
date: 2007-09-03
forum: General Help
---

### Post by MustNotSleep on 2007-09-03
everything was working correctly.. the last system change i did (aside from installing programs with aptitude, which went smoothly) was changing my Gnome splash screen using gnome-splashscreen-manager, which shows up correctly and has been applied without problems.. but when i booted up at work, gnome gives me "your session has lasted less than 10 secs, etc", the same as failsafe-gnome.

here's my ~/.xsession-errors file:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ivan"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  	
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/ivant43:/tmp/.ICE-unix/7654

** (gnome-session:7654): WARNING **: Host name lookup failure on localhost.
Initializing gnome-mount extension
Initializing nautilus-open-terminal extension
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in Xorg.conf or XFree86.conf to use GSynaptics

(gnome-panel:7730): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24


Tracker version 0.6.0 Copyright (c) 2005-2006 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
xmodmap:  unable to open file '~/.xmodmaprc' for reading
xmodmap:  1 error encountered, aborting.
setting stopword list for language code en
Using stemmer for language english

Tracker configuration options :
Verbosity : ........................  1
Low memory mode : ..................  no
Indexing enabled : .................  yes
Watching enabled : .................  yes
File content indexing enabled : ....  yes
Thumbnailing enabled : .............  no
Evolution email indexing enabled : .  yes
Thunderbird email indexing enabled :  no
K-Mail indexing enabled : ..........  no

Tracker indexer parameters :
Indexer language code : ............  en
Minimum index word length : ........  3
Maximum index word length : ........  30
Stemmer enabled : ..................  yes
Setting watch directory roots to:
/home
/home/ivan
	
throttle level is 0
Using Sqlite version 3.3.13
Loading prepared queries...
File loaded in  0.250000 ms
initialising the indexer
Opening index /home/ivan/.cache/tracker/Files
Bucket count (max is 524288) is 81916 and Record Count is 81747
Preferred bucket count is 81747
loaded sql file sqlite-cache.sql

(evolution-alarm-notify:7752): GnomeUI-WARNING **: While connecting to session manager:
IO 		 occured opening connection.

(Tomboy:7753): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:7754): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
[DEBUG]: NoteManager created with note path "/home/ivan/.tomboy".
evolution-alarm-notify-Message: Setting timeout for 40648 1188864000 1188823352
evolution-alarm-notify-Message:  Mon Sep  3 20:00:00 2007

evolution-alarm-notify-Message:  Mon Sep  3 08:42:32 2007

Trying Plugin: Backlinks.dll ... BacklinksPlugin. [DEBUG]: Done.
Trying Plugin: Bugzilla.dll ... BugzillaPlugin. [DEBUG]: Done.
Trying Plugin: Evolution.dll ... EvolutionPlugin. [DEBUG]: Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. [DEBUG]: Done.
Trying Plugin: FixedWidth.dll ... FixedWidthPlugin. [DEBUG]: Done.
Trying Plugin: NoteOfTheDay.dll ... NoteOfTheDayPlugin. [DEBUG]: Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. [DEBUG]: Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. [DEBUG]: Done.
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!

(update-notifier:7745): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```
this could be either an xmodmap problem (which i use to swap my Caps Lock with Super, and incidentally the swap works even with that error), but i don't know why it can't open xmodmap, but i think the problem is in that weird Gtk widget, that has -9 width.. i tried resetting my gnome panels and removing and adding new ones, but i still get the error..

not sure what it is.. is there a way of resetting the minimum of gnome settings so i can boot without problems again? i remember i deleted ~/.gnome2 in the past, but that just wrecked my whole profile, and i wouldn't want to do it again..

any suggestions are appreciated.. TIA!

---

### Post by MustNotSleep on 2007-09-03
i attempted resetting the gnome settings by renaming .gnome, .gnome2, .gconf, .gconfd and .gnome2_private.. i logged back in, and the session still restarts.. ?

i also attempted to modify /etc/X11/Xsession.d/80ubuntu-modmap and pointed it to ~/.xmodmaprc, but i still get the "could not load" error, even though the modifier works correctly.. besides, i'm not even sure that's the reason Gnome keeps crashing..

help!

//EDIT: here's an updated .xsession-errors file, showing some kind of memory corruption in gnome-session on line 27.. wth?

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ivan"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
SESSION_MANAGER=local/ivant43:/tmp/.ICE-unix/10739

** (gnome-session:10739): WARNING **: Host name lookup failure on localhost.
Initializing gnome-mount extension
Initializing nautilus-open-terminal extension

** (gsynaptics-init:10834): WARNING **: Using synclient


Tracker version 0.6.0 Copyright (c) 2005-2006 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...

** (trackerd:10864): WARNING **: Tracker daemon is already running - exiting
xmodmap:  unable to open file '~/.xmodmaprc' for reading
xmodmap:  1 error encountered, aborting.

(gnome-panel:10818): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24
*** glibc detected *** /usr/bin/gnome-session: malloc(): memory corruption (fast): 0x082a1a68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb761e6fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb761f60e]
/lib/tls/i686/cmov/libc.so.6(realloc+0x146)[0xb76210d6]
/usr/lib/libglib-2.0.so.0(g_realloc+0x3b)[0xb773518b]
/usr/lib/libglib-2.0.so.0[0xb774985c]
/usr/lib/libglib-2.0.so.0(g_string_sized_new+0x3d)[0xb774a37d]
/usr/lib/libglib-2.0.so.0(g_string_new+0x35)[0xb774a3c5]
/usr/lib/libglib-2.0.so.0(g_log_default_handler+0x82)[0xb77370a2]
/usr/lib/libglib-2.0.so.0(g_logv+0x2e5)[0xb7736525]
/usr/lib/libglib-2.0.so.0(g_log+0x29)[0xb7736749]
/usr/lib/libglib-2.0.so.0(g_assert_warning+0x76)[0xb77367c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x3c6)[0xb772e036]
/usr/lib/libglib-2.0.so.0[0xb7730dcf]
/usr/lib/libglib-2.0.so.0(g_main_context_iteration+0x65)[0xb7731335]
/usr/bin/gnome-session[0x8055789]
/usr/lib/libglib-2.0.so.0[0xb775740d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb772ddf2]
/usr/lib/libglib-2.0.so.0[0xb7730dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7731179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c66044]
/usr/bin/gnome-session(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75cbebc]
/usr/bin/gnome-session[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:07 696708     /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:07 696708     /usr/bin/gnome-session
08069000-082c1000 rw-p 08069000 00:00 0          [heap]
b4700000-b4721000 rw-p b4700000 00:00 0 
b4721000-b4800000 ---p b4721000 00:00 0 
b48f4000-b48ff000 r-xp 00000000 08:07 388689     /lib/libgcc_s.so.1
b48ff000-b4900000 rw-p 0000a000 08:07 388689     /lib/libgcc_s.so.1
b4900000-b4902000 r-xp 00000000 08:07 388696     /lib/libnss_mdns4.so.2
b4902000-b4903000 rw-p 00001000 08:07 388696     /lib/libnss_mdns4.so.2
b4903000-b4907000 r-xp 00000000 08:07 422128     /lib/tls/i686/cmov/libnss_dns-2.5.so
b4907000-b4909000 rw-p 00003000 08:07 422128     /lib/tls/i686/cmov/libnss_dns-2.5.so
b491d000-b491e000 ---p b491d000 00:00 0 
b491e000-b511e000 rw-p b491e000 00:00 0 
b511e000-b519b000 r--p 00000000 08:07 97532      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b519b000-b519d000 r-xp 00000000 08:07 32904      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b519d000-b519e000 rw-p 00001000 08:07 32904      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b519e000-b51a1000 r--s 00000000 08:07 686894     /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b51a1000-b51a3000 r--s 00000000 08:07 686893     /var/cache/fontconfig/603b2eb47209ddb3c5269b217a306167-x86.cache-2
b51a3000-b51a9000 r--s 00000000 08:07 680446     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b51a9000-b51ac000 r--s 00000000 08:07 680444     /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b51ac000-b51ad000 r--s 00000000 08:07 686890     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b51ad000-b51b0000 r--s 00000000 08:07 686889     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b51b0000-b51b1000 r--s 00000000 08:07 686888     /var/cache/fontconfig/6edd069ccec3ba28096b368c434fa861-x86.cache-2
b51b1000-b51b2000 r--s 00000000 08:07 686887     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b51b2000-b51b3000 r--s 00000000 08:07 686886     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b51b3000-b51b7000 r--s 00000000 08:07 680437     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b51b7000-b51d2000 r--s 00000000 08:07 686884     /var/cache/fontconfig/4ca92cf76c0cf3dfa7f011127eff595d-x86.cache-2
b51d2000-b51ee000 r--s 00000000 08:07 686882     /var/cache/fontconfig/6abf76b0b4cc7192703d8431ac929b75-x86.cache-2
b51ee000-b520c000 r--s 00000000 08:07 686881     /var/cache/fontconfig/f408d08d2fce062ab660f628db78bf96-x86.cache-2
b520c000-b520d000 r--s 00000000 08:07 686880     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b520d000-b520f000 r--s 00000000 08:07 686878     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b520f000-b5211000 r--s 00000000 08:07 686877     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b5211000-b5212000 r--s 00000000 08:07 686870     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5212000-b5213000 r--s 00000000 08:07 686869     /var/cache/fontconfig/a8d35ba226d862df35f7c320f882e11a-x86.cache-2
b5213000-b5215000 r--s 00000000 08:07 686868     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b5215000-b521b000 r--s 00000000 08:07 686867     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b521b000-b521d000 r--s 00000000 08:07 686866     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b521d000-b521f000 r--s 00000000 08:07 686865     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b521f000-b5227000 r--s 00000000 08:07 686864     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5227000-b522d000 r--s 00000000 08:07 686863     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b522d000-b522e000 r--s 00000000 08:07 686862     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b522e000-b5245000 r--s 00000000 08:07 686861     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5245000-b5247000 r--s 00000000 08:07 686860     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5247000-b524d000 r--s 00000000 08:07 686859     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b524d000-b5251000 r--s 00000000 08:07 686858     /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b5251000-b5254000 r--s 00000000 08:07 686857     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b5254000-b5258000 r--s 00000000 08:07 686856     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5258000-b525e000 r--s 00000000 08:07 680412     /var/cache/fontconfig/cabbd14511b9e8a55e92af97fb3a0461-x86.cache-2
b525e000-b5265000 r--s 00000000 08:07 680409     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5265000-b5266000 r--s 00000000 08:07 680404     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b5266000-b5267000 r--s 00000000 08:07 686922     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b5267000-b5268000 r--s 00000000 08:07 680401     /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b5268000-b5269000 r--s 00000000 08:07 686920     /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b5269000-b526a000 r--s 00000000 08:07 686919     /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b526a000-b526d000 r--s 00000000 08:07 686918     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b526d000-b5271000 r--s 00000000 08:07 686917     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b5271000-b527a000 r--s 00000000 08:07 686916     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b527a000-b527c000 r--s 00000000 08:07 686915     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b527c000-b527d000 r--s 00000000 08:07 686914     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b527d000-b527f000 r--s 00000000 08:07 686913     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b527f000-b5280000 r--s 00000000 08:07 686912     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b5280000-b5285000 r--s 00000000 08:07 686911     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b5285000-b5289000 r--s 00000000 08:07 686910     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b5289000-b528e000 r--s 00000000 08:07 686909     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b528e000-b5291000 r--s 00000000 08:07 686908     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b5291000-b5292000 r--s 00000000 08:07 686907     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b5292000-b5294000 r--s 00000000 08:07 686906     /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b5294000-b5296000 r--s 00000000 08:07 686905     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b5296000-b529c000 r--s 00000000 08:07 686904     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b529c000-b52a2000 r--s 00000000 08:07 686903     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b52a2000-b52ab000 r--s 00000000 08:07 686901     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b52ab000-b52b1000 r--s 00000000 08:07 686900     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b52b1000-b52b5000 r--s 00000000 08:07 686899     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b52b5000-b52ba000 r--s 00000000 08:07 680459     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b52ba000-b52c0000 r--s 00000000 08:07 680455     /var/cache/fontconfig/1e88f1f1e0efe03f58dd40df4dd7a0ea-x86.cache-2
b52c0000-b63b8000 r--p 00000000 08:07 162908     /usr/share/icons/crystalsvg/icon-theme.cache
b63b8000-b6a5f000 r--p 00000000 08:07 168358     /usr/share/icons/gnome/icon-theme.cache
b6a5f000-b6cb6000 r--p 00000000 08:07 167072     /usr/share/icons/Tango/icon-theme.cache
b6cb6000-b6cc1000 r-xp 00000000 08:07 746056     /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b6cc1000-b6cc2000 rw-p 0000b000 08:07 746056     /usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so
b6cc2000-b6d22000 rw-s 00000000 00:08 8585228    /SYSV00000000 (deleted)
b6d22000-b6d8e000 rw-p b6d22000 00:00 0 
b6d8e000-b6d95000 r-xp 00000000 08:07 697730     /usr/lib/libfam.so.0.0.0
b6d95000-b6d96000 rw-p 00006000 08:07 697730     /usr/lib/libfam.so.0.0.0
b6d96000-b6d9c000 r-xp 00000000 08:07 388635     /lib/libacl.so.1.1.0
b6d9c000-b6d9d000 rw-p 00005000 08:07 388635     /lib/libacl.so.1.1.0
b6d9d000-b6da0000 r-xp 00000000 08:07 388639     /lib/libattr.so.1.1.0
b6da0000-b6da1000 rw-p 00002000 08:07 388639     /lib/libattr.so.1.1.0
b6da1000-b6da3000 r-xp 00000000 08:07 388697     /lib/libnss_mdns4_minimal.so.2
b6da3000-b6da4000 rw-p 00001000 08:07 388697     /lib/libnss_mdns4_minimal.so.2
b6da4000-b6dab000 r--s 00000000 08:07 680452     /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6dab000-b6db0000 r--p 00000000 08:07 713468     /usr/local/share/icons/hicolor/icon-theme.cache
b6db0000-b6db4000 r-xp 00000000 08:07 746087     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6db4000-b6db5000 rw-p 00003000 08:07 746087     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6db5000-b6dc1000 r-xp 00000000 08:07 746010     /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc1000-b6dc2000 rw-p 0000b000 08:07 746010     /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6dc2000-b6dc3000 r-xp 00000000 08:07 713798     /usr/lib/gconv/ISO8859-1.so
b6dc3000-b6dc5000 rw-p 00000000 08:07 713798     /usr/lib/gconv/ISO8859-1.so
b6dc5000-b6e00000 r--p 00000000 08:07 761947     /usr/lib/locale/en_US.utf8/LC_CTYPE
b6e00000-b6ed7000 r--p 00000000 08:07 761946     /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ed7000-b6ee0000 r-xp 00000000 08:07 422130     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee0000-b6ee2000 rw-p 00008000 08:07 422130     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ee2000-b6eea000 r-xp 00000000 08:07 422134     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eea000-b6eec000 rw-p 00007000 08:07 422134     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6eec000-b6ef3000 r-xp 00000000 08:07 422126     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef3000-b6ef5000 rw-p 00006000 08:07 422126     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ef5000-b6ef8000 rw-p b6ef5000 00:00 0 
b6ef8000-b6f2e000 r-xp 00000000 08:07 388726     /lib/libsepol.so.1
b6f2e000-b6f2f000 rw-p 00035000 08:07 388726     /lib/libsepol.so.1
b6f2f000-b6f39000 rw-p b6f2f000 00:00 0 
b6f39000-b6f3c000 r-xp 00000000 08:07 697883     /usr/lib/libgpg-error.so.0.3.0
b6f3c000-b6f3d000 rw-p 00002000 08:07 697883     /usr/lib/libgpg-error.so.0.3.0
b6f3d000-b6f8c000 r-xp 00000000 08:07 697771     /usr/lib/libgcrypt.so.11.2.2
b6f8c000-b6f8e000 rw-p 0004e000 08:07 697771     /usr/lib/libgcrypt.so.11.2.2
b6f8e000-b6f8f000 rw-p b6f8e000 00:00 0 
b6f8f000-b6fa3000 r-xp 00000000 08:07 698227     /usr/lib/libtasn1.so.3.0.6
b6fa3000-b6fa4000 rw-p 00013000 08:07 698227     /usr/lib/libtasn1.so.3.0.6
b6fa4000-b6fa6000 r-xp 00000000 08:07 422147     /lib/tls/i686/cmov/libutil-2.5.so
b6fa6000-b6fa8000 rw-p 00001000 08:07 422147     /lib/tls/i686/cmov/libutil-2.5.so
b6fa8000-b6fbc000 r-xp 00000000 08:07 388725     /lib/libselinux.so.1
b6fbc000-b6fbe000 rw-p 00013000 08:07 388725     /lib/libselinux.so.1
b6fbe000-b6fcd000 r-xp 00000000 08:07 422141     /lib/tls/i686/cmov/libresolv-2.5.so
b6fcd000-b6fcf000 rw-p 0000f000 08:07 422141     /lib/tls/i686/cmov/libresolv-2.5.so
b6fcf000-b6fd1000 rw-p b6fcf000 00:00 0 
b6fd1000-b6fdf000 r-xp 00000000 08:07 697609     /usr/lib/libavahi-client.so.3.2.2
b6fdf000-b6fe0000 rw-p 0000e000 08:07 697609     /usr/lib/libavahi-client.so.3.2.2
b6fe0000-b6fe1000 rw-p b6fe0000 00:00 0 
b6fe1000-b6feb000 r-xp 00000000 08:07 697611     /usr/lib/libavahi-common.so.3.4.3
b6feb000-b6fec000 rw-p 00009000 08:07 697611     /usr/lib/libavahi-common.so.3.4.3
b6fec000-b6fee000 r-xp 00000000 08:07 697615     /usr/lib/libavahi-glib.so.1.0.1
b6fee000-b6fef000 rw-p 00001000 08:07 697615     /usr/lib/libavahi-glib.so.1.0.1
b6fef000-b7059000 r-xp 00000000 08:07 697879     /usr/lib/libgnutls.so.13.0.9
b7059000-b705f000 rw-p 0006a000 08:07 697879     /usr/lib/libgnutls.so.13.0.9
b705f000-b7081000 r-xp 00000000 08:07 697805     /usr/lib/libpng12.so.0.15.0
b7081000-b7082000 rw-p 00021000 08:07 697805     /usr/lib/libpng12.so.0.15.0
b7082000-b70a0000 r-xp 00000000 08:07 697726     /usr/lib/libexpat.so.1.0.0
b70a0000-b70a2000 rw-p 0001d000 08:07 697726     /usr/lib/libexpat.so.1.0.0
b70a2000-b70a3000 rw-p b70a2000 00:00 0 
b70a3000-b710f000 r-xp 00000000 08:07 700098     /usr/lib/libfreetype.so.6.3.16
b710f000-b7113000 rw-p 0006b000 08:07 700098     /usr/lib/libfreetype.so.6.3.16
b7113000-b7126000 r-xp 00000000 08:07 698285     /usr/lib/libz.so.1.2.3
b7126000-b7127000 rw-p 00012000 08:07 698285     /usr/lib/libz.so.1.2.3
b7127000-b713a000 r-xp 00000000 08:07 422124     /lib/tls/i686/cmov/libnsl-2.5.so
b713a000-b713c000 rw-p 00012000 08:07 422124     /lib/tls/i686/cmov/libnsl-2.5.so
b713c000-b713e000 rw-p b713c000 00:00 0 
b713e000-b7142000 r-xp 00000000 08:07 697516     /usr/lib/libORBitCosNaming-2.so.0.1.0
b7142000-b7143000 rw-p 00003000 08:07 697516     /usr/lib/libORBitCosNaming-2.so.0.1.0
b7143000-b7144000 rw-p b7143000 00:00 0 
b7144000-b7148000 r-xp 00000000 08:07 697541     /usr/lib/libXdmcp.so.6.0.0
b7148000-b7149000 rw-p 00003000 08:07 697541     /usr/lib/libXdmcp.so.6.0.0
b7149000-b7167000 r-xp 00000000 08:07 698008     /usr/lib/libjpeg.so.62.0.0
b7167000-b7168000 rw-p 0001d000 08:07 698008     /usr/lib/libjpeg.so.62.0.0
b7168000-b7170000 r-xp 00000000 08:07 698217     /usr/lib/libstartup-notification-1.so.0.0.0
b7170000-b7171000 rw-p 00007000 08:07 698217     /usr/lib/libstartup-notification-1.so.0.0.0
b7171000-b7172000 rw-p b7171000 00:00 0 
b7172000-b7179000 r-xp 00000000 08:07 422143     /lib/tls/i686/cmov/librt-2.5.so
b7179000-b717b000 rw-p 00006000 08:07 422143     /lib/tls/i686/cmov/librt-2.5.so
b717b000-b717f000 r-xp 00000000 08:07 697837     /usr/lib/libgthread-2.0.so.0.1200.11
b717f000-b7180000 rw-p 00003000 08:07 697837     /usr/lib/libgthread-2.0.so.0.1200.11
b7180000-b7182000 r-xp 00000000 08:07 422119     /lib/tls/i686/cmov/libdl-2.5.so
b7182000-b7184000 rw-p 00001000 08:07 422119     /lib/tls/i686/cmov/libdl-2.5.so
b7184000-b7186000 r-xp 00000000 08:07 697827     /usr/lib/libgmodule-2.0.so.0.1200.11
b7186000-b7187000 rw-p 00002000 08:07 697827     /usr/lib/libgmodule-2.0.so.0.1200.11
b7187000-b71dd000 r-xp 00000000 08:07 697871     /usr/lib/libgnomevfs-2.so.0.1800.1
b71dd000-b71e0000 rw-p 00055000 08:07 697871     /usr/lib/libgnomevfs-2.so.0.1800.1
b71e0000-b7254000 r-xp 00000000 08:07 697550     /usr/lib/libcairo.so.2.11.5
b7254000-b7256000 rw-p 00074000 08:07 697550     /usr/lib/libcairo.so.2.11.5
b7256000-b7257000 rw-p b7256000 00:00 0 
b7257000-b725b000 r-xp 00000000 08:07 697547     /usr/lib/libXfixes.so.3.1.0
b725b000-b725c000 rw-p 00003000 08:07 697547     /usr/lib/libXfixes.so.3.1.0
b725c000-b7264000 r-xp 00000000 08:07 697537     /usr/lib/libXcursor.so.1.0.2
b7264000-b7265000 rw-p 00007000 08:07 697537     /usr/lib/libXcursor.so.1.0.2
b7265000-b726c000 r-xp 00000000 08:07 697553     /usr/lib/libXi.so.6.0.0
b726c000-b726d000 rw-p 00006000 08:07 697553     /usr/lib/libXi.so.6.0.0
b726d000-b726f000 r-xp 00000000 08:07 697555     /usr/lib/libXinerama.so.1.0.0
b726f000-b7270000 rw-p 00001000 08:07 697555     /usr/lib/libXinerama.so.1.0.0
b7270000-b7277000 r-xp 00000000 08:07 697567     /usr/lib/libXrender.so.1.3.0
b7277000-b7278000 rw-p 00006000 08:07 697567     /usr/lib/libXrender.so.1.3.0
b7278000-b7285000 r-xp 00000000 08:07 697545     /usr/lib/libXext.so.6.4.0
b7285000-b7286000 rw-p 0000d000 08:07 697545     /usr/lib/libXext.so.6.4.0
b7286000-b7287000 rw-p b7286000 00:00 0 
b7287000-b72aa000 r-xp 00000000 08:07 697732     /usr/lib/libfontconfig.so.1.2.0
b72aa000-b72b2000 rw-p 00023000 08:07 697732     /usr/lib/libfontconfig.so.1.2.0
b72b2000-b72b9000 r-xp 00000000 08:07 1165880    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72b9000-b72ba000 rw-p 00007000 08:07 1165880    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72ba000-b72e4000 r-xp 00000000 08:07 1165881    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72e4000-b72e5000 rw-p 0002a000 08:07 1165881    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72e5000-b72f9000 r-xp 00000000 08:07 700195     /usr/lib/libart_lgpl_2.so.2.3.17
b72f9000-b72fa000 rw-p 00013000 08:07 700195     /usr/lib/libart_lgpl_2.so.2.3.17
b72fa000-b7301000 r-xp 00000000 08:07 388715     /lib/libpopt.so.0.0.0
b7301000-b7302000 rw-p 00006000 08:07 388715     /lib/libpopt.so.0.0.0
b7302000-b732b000 r-xp 00000000 08:07 697853     /usr/lib/libgnomecanvas-2.so.0.1400.0
b732b000-b732c000 rw-p 00029000 08:07 697853     /usr/lib/libgnomecanvas-2.so.0.1400.0
b732c000-b732d000 rw-p b732c000 00:00 0 
b732d000-b7388000 r-xp 00000000 08:07 697630     /usr/lib/libbonoboui-2.so.0.0.0
b7388000-b738b000 rw-p 0005a000 08:07 697630     /usr/lib/libbonoboui-2.so.0.0.0
b738b000-b74a2000 r-xp 00000000 08:07 698279     /usr/lib/libxml2.so.2.6.27
b74a2000-b74a8000 rw-p 00116000 08:07 698279     /usr/lib/libxml2.so.2.6.27
b74a8000-b7568000 r-xp 00000000 08:07 697595     /usr/lib/libasound.so.2.0.0
b7568000-b756d000 rw-p 000bf000 08:07 697595     /usr/lib/libasound.so.2.0.0
b756d000-b7592000 r-xp 00000000 08:07 422121     /lib/tls/i686/cmov/libm-2.5.so
b7592000-b7594000 rw-p 00024000 08:07 422121     /lib/tls/i686/cmov/libm-2.5.so
b7594000-b75b4000 r-xp 00000000 08:07 697607     /usr/lib/libaudiofile.so.0.0.2
b75b4000-b75b6000 rw-p 00020000 08:07 697607     /usr/lib/libaudiofile.so.0.0.2
b75b6000-b76f1000 r-xp 00000000 08:07 422113     /lib/tls/i686/cmov/libc-2.5.so
b76f1000-b76f2000 r--p 0013b000 08:07 422113     /lib/tls/i686/cmov/libc-2.5.so
b76f2000-b76f4000 rw-p 0013c000 08:07 422113     /lib/tls/i686/cmov/libc-2.5.so
b76f4000-b76f8000 rw-p b76f4000 00:00 0 
b76f8000-b76ff000 r-xp 00000000 08:07 388746     /lib/libwrap.so.0.7.6
b76ff000-b7700000 rw-p 00007000 08:07 388746     /lib/libwrap.so.0.7.6
b7700000-b7794000 r-xp 00000000 08:07 696385     /usr/lib/libglib-2.0.so.0.1200.11
b7794000-b7795000 rw-p 00093000 08:07 696385     /usr/lib/libglib-2.0.so.0.1200.11
b7795000-b77a1000 r-xp 00000000 08:07 697843     /usr/lib/libgnome-keyring.so.0.0.1
b77a1000-b77a2000 rw-p 0000b000 08:07 697843     /usr/lib/libgnome-keyring.so.0.0.1
b77a2000-b77db000 r-xp 00000000 08:07 697593     /usr/lib/libgobject-2.0.so.0.1200.11
b77db000-b77dc000 rw-p 00039000 08:07 697593     /usr/lib/libgobject-2.0.so.0.1200.11
b77dc000-b780e000 r-xp 00000000 08:07 697001     /usr/lib/libdbus-1.so.3.2.0
b780e000-b780f000 rw-p 00031000 08:07 697001     /usr/lib/libdbus-1.so.3.2.0
b780f000-b7829000 r-xp 00000000 08:07 697670     /usr/lib/libdbus-glib-1.so.2.1.0
b7829000-b782a000 rw-p 0001a000 08:07 697670     /usr/lib/libdbus-glib-1.so.2.1.0
b782a000-b782b000 rw-p b782a000 00:00 0 
b782b000-b783e000 r-xp 00000000 08:07 422139     /lib/tls/i686/cmov/libpthread-2.5.so
b783e000-b7840000 rw-p 00013000 08:07 422139     /lib/tls/i686/cmov/libpthread-2.5.so
b7840000-b7842000 rw-p b7840000 00:00 0 
b7842000-b788b000 r-xp 00000000 08:07 697512     /usr/lib/libORBit-2.so.0.1.0
b788b000-b7895000 rw-p 00048000 08:07 697512     /usr/lib/libORBit-2.so.0.1.0
b7895000-b78c4000 r-xp 00000000 08:07 697769     /usr/lib/libgconf-2.so.4.1.2
b78c4000-b78c7000 rw-p 0002e000 08:07 697769     /usr/lib/libgconf-2.so.4.1.2
b78c7000-b78da000 r-xp 00000000 08:07 697628     /usr/lib/libbonobo-activation.so.4.0.0
b78da000-b78dc000 rw-p 00013000 08:07 697628     /usr/lib/libbonobo-activation.so.4.0.0
b78dc000-b792e000 r-xp 00000000 08:07 697626     /usr/lib/libbonobo-2.so.0.0.0
b792e000-b7938000 rw-p 00051000 08:07 697626     /usr/lib/libbonobo-2.so.0.0.0
b7938000-b7939000 rw-p b7938000 00:00 0 
b7939000-b7a26000 r-xp 00000000 08:07 697524     /usr/lib/libX11.so.6.2.0
b7a26000-b7a2a000 rw-p 000ed000 08:07 697524     /usr/lib/libX11.so.6.2.0
b7a2a000-b7a66000 r-xp 00000000 08:07 1165827    /usr/lib/libpango-1.0.so.0.1600.2
b7a66000-b7a68000 rw-p 0003b000 08:07 1165827    /usr/lib/libpango-1.0.so.0.1600.2
b7a68000-b7a6d000 r-xp 00000000 08:07 697565     /usr/lib/libXrandr.so.2.1.0
b7a6d000-b7a6e000 rw-p 00005000 08:07 697565     /usr/lib/libXrandr.so.2.1.0
b7a6e000-b7a84000 r-xp 00000000 08:07 697791     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a84000-b7a85000 rw-p 00015000 08:07 697791     /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a85000-b7a9e000 r-xp 00000000 08:07 697601     /usr/lib/libatk-1.0.so.0.1809.1
b7a9e000-b7aa0000 rw-p 00018000 08:07 697601     /usr/lib/libatk-1.0.so.0.1809.1
b7aa0000-b7b23000 r-xp 00000000 08:07 697789     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b23000-b7b26000 rw-p 00083000 08:07 697789     /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b26000-b7b27000 rw-p b7b26000 00:00 0 
b7b27000-b7e78000 r-xp 00000000 08:07 697938     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e78000-b7e7e000 rw-p 00351000 08:07 697938     /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e7e000-b7e7f000 rw-p b7e7e000 00:00 0 
b7e7f000-b7e93000 r-xp 00000000 08:07 697839     /usr/lib/libgnome-2.so.0.1800.0
b7e93000-b7e94000 rw-p 00014000 08:07 697839     /usr/lib/libgnome-2.so.0.1800.0
b7e94000-b7ea9000 r-xp 00000000 08:07 697502     /usr/lib/libICE.so.6.3.0
b7ea9000-b7eab000 rw-p 00014000 08:07 697502     /usr/lib/libICE.so.6.3.0
b7eab000-b7eac000 rw-p b7eab000 00:00 0 
b7eac000-b7eb4000 r-xp 00000000 08:07 697520     /usr/lib/libSM.so.6.0.0
b7eb4000-b7eb5000 rw-p 00007000 08:07 697520     /usr/lib/libSM.so.6.0.0
b7eb5000-b7f3f000 r-xp 00000000 08:07 697869     /usr/lib/libgnomeui-2.so.0.1788.4
b7f3f000-b7f43000 rw-p 00089000 08:07 697869     /usr/lib/libgnomeui-2.so.0.1788.4
b7f43000-b7f57000 r-xp 00000000 08:07 697841     /usr/lib/libgnome-desktop-2.so.2.3.5
b7f57000-b7f58000 rw-p 00014000 08:07 697841     /usr/lib/libgnome-desktop-2.so.2.3.5
b7f58000-b7f59000 rw-p b7f58000 00:00 0 
b7f59000-b7f62000 r-xp 00000000 08:07 697717     /usr/lib/libesd.so.0.2.36
b7f62000-b7f63000 rw-p 00009000 08:07 697717     /usr/lib/libesd.so.0.2.36
b7f63000-b7f65000 r-xp 00000000 08:07 697530     /usr/lib/libXau.so.6.0.0
b7f65000-b7f66000 rw-p 00001000 08:07 697530     /usr/lib/libXau.so.6.0.0
b7f66000-b7f67000 r--s 00000000 08:07 686902     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f67000-b7f68000 r--s 00000000 08:07 680414     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b7f68000-b7f69000 r--s 00000000 08:07 680458     /var/cache/fontconfig/023b7efb2321b24388359937898d2ff9-x86.cache-2
b7f69000-b7f6a000 r--p 00000000 08:07 761952     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f6a000-b7f6b000 r--p 00000000 08:07 761955     /usr/lib/locale/en_US.utf8/LC_TIME
b7f6b000-b7f6c000 r--p 00000000 08:07 761950     /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f6c000-b7f6d000 r--p 00000000 08:07 761956     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f6d000-b7f6e000 r--p 00000000 08:07 761953     /usr/lib/locale/en_US.utf8/LC_PAPER
b7f6e000-b7f6f000 r--p 00000000 08:07 761951     /usr/lib/locale/en_US.utf8/LC_NAME
b7f6f000-b7f70000 r--p 00000000 08:07 761945     /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f70000-b7f71000 r--p 00000000 08:07 761954     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f71000-b7f72000 r--p 00000000 08:07 761949     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f72000-b7f79000 r--s 00000000 08:07 713857     /usr/lib/gconv/gconv-modules.cache
b7f79000-b7f7a000 r--p 00000000 08:07 761948     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f7a000-b7f7c000 rw-p b7f7a000 00:00 0 
b7f7c000-b7f95000 r-xp 00000000 08:07 388614     /lib/ld-2.5.so
b7f95000-b7f97000 rw-p 00019000 08:07 388614     /lib/ld-2.5.so
bfd7c000-bfd92000 rw-p bfd7c000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(evolution-alarm-notify:10837): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 32243 1188864000 1188831757
evolution-alarm-notify-Message:  Mon Sep  3 20:00:00 2007

evolution-alarm-notify-Message:  Mon Sep  3 11:02:37 2007


(gnome-power-manager:10839): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
alarm-notify.c:368 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:304 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:243 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1875 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Mon Sep  3 20:00:00 2007
 
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/ivan/.evolution/calendar/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/ivan/.evolution/calendar/local/system - Calendar Open Async... 0x80b27a0
alarm-notify.c:220 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:456 (alarm_notify_add_calendar) contacts:/// - Calendar Open Async... 0x80c1a70
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/ivan/.evolution/tasks/local/system 
alarm-notify.c:456 (alarm_notify_add_calendar) file:///home/ivan/.evolution/tasks/local/system - Calendar Open Async... 0x80c65d0
alarm-notify.c:220 (load_calendars) - Loading Calendar file:///home/ivan/.evolution/me
(update-notifier:10832): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
```

---

### Post by MustNotSleep on 2007-09-03
well, i guess i fixed it (but not solved it) myself..

i had to clear out my /tmp for the gnome to reset its settings again, and now i'm in the process of copying back the settings i couldn't live without and can't remember how i set them up, carefully checking i don't break stuff again in the process..

out of curiosity, why did this happen? this is the second time my Gnome session got corruputed, and its the second time the only way i found i could fix it was by deleting the gnome settings and starting from scratch.. this shouldn't be happening on a stable Ubuntu release (Feisty Fawn)..

//EDIT: given the public request for this thread, i'm forced to keep you all updated..

the culprit was definitely the splash screen i set using gnome-splashscreen-manager. immediately after setting only that and restarting X, my gnome session broke again with the same error.. the file in question is ~/.gconf/apps/gnome-session/options/%gconf.xml . after resetting it, everything is back to normal. for some reason, and i doubt gnome-splashscreen-manager is to blame here, the image i was trying to set doesn't work, **even though it's displayed normally when booting Gnome**, and it leads to some kind of error..

i attach the image in question..

i'll try setting another image with gnome-splashscreen-manager and see if it works..

//EDIT2: yup, it was that particular image.. gnome-splash.png in /usr/share/pixmaps/splash/ works correctly when set with gnome-splashscreen-manager.. so i guess this thread is solved.. if only i'd find what's the deal with that image.....

---

