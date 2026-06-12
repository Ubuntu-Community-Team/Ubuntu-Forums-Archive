---
title: "Watching a Backed up DVD on HD?"
date: 2005-10-31
forum: General Help
---

### Post by RSX311 on 2005-10-31
I Backed up a DVD Movie to my HD and it has all the .vob files and everything.  How do I watch the movie?  I can open up each .vob file and watch the movie but how do I open the Directory as a movie in Totem/Xine/VLC?  None of them have options to open a directory to play like a DVD with menus and all.  In windows powerDVD allows you to do this, just wondering if Linux allows you to do this so I don't have to burn it to a DVD.

Thanks

---

### Post by toorima on 2005-10-31
vlc play dirs, file - open dir 
or ctl+E

---

### Post by maruchan on 2005-10-31
VLC, baby, VLC. Plays .vobs directly even.

---

### Post by RSX311 on 2005-10-31
I tried using VLC to open a dir and VLC just crashes.  So I ran VLC in a terminal and opened a dir and it spit out these errors.  Anybody have any ideas how to fix it?

```
rsx@synergy:~/downloads$ vlc
VLC media player 0.8.4-svn20040920 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/rsx/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
libdvdnav: Language 'en' not found, using '\uffff\uffff' instead
libdvdnav: Menu Languages available: \uffff\uffff
Segmentation fault

```

---

