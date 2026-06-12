---
title: "DVDs *stop* working after libdvdcss2 is installed"
date: 2005-07-18
forum: General Help
---

### Post by SenatorK on 2005-07-18
So I been having troubles getting DVDs to work on my system. Every player I've tried seems to lockup when starting to play the DVD. However, I was able to play parts of DVDs if the libdvdcss2 library wasn't installed. As soon as I installed it, Totem would lockup when trying to play the DVD and VLC would do the same. (See log below)

Totem would obviously stop playing once it got to an encrypted track, but what could be causing the system to go nuts when calling the library? I've had it sit for over 30 minutes with no result. I'm a new 1.6ghrz laptop if that makes a difference. Any ideas?


VLC Output with libdvdcss2 installed. VLC will lock after the last entry.

[00000001] main vlc warning: could not open plugins cache file /home/kevin/.vlc/cache/plugins-04041e.dat for reading
[00000001] main vlc warning: config file /home/kevin/.vlc/vlcrc does not exist yet
[00000001] main vlc warning: config file /home/kevin/.vlc/vlcrc does not exist yet
[00000001] main vlc warning: could not open plugins cache file /home/kevin/.vlc/cache/plugins-04041e.dat for reading
[00000001] main vlc warning: config file /home/kevin/.vlc/vlcrc does not exist yet
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdnav: DVD Title: LEBOWSKI
libdvdnav: DVD Serial Number: 25974AD0
libdvdnav: DVD Title (Alternative): LEBOWSKI
libdvdnav: Unable to find map file '/home/kevin/.dvdnav/LEBOWSKI.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000139

---

### Post by Chandon on 2005-07-23
I seem to be having this problem as well.

When trying to play a DVD, Xine freezes at libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000178 - exactly the same problem that SenatorK is getting (I'm assuming the different address is due to my use of a different test DVD).

Another strong indicator that there's something wrong here, as opposed to it just taking a while, is the fact that it's (Xine, libdvdcss2, anything) not using any CPU time.

---

### Post by c0rderr0y on 2005-08-22
Where you guys able to fix this? I too am having this problem....

---

### Post by arnieboy on 2005-08-23
[QUOTE=c0rderr0y]Where you guys able to fix this? I too am having this problem....[/QUOTE]
do a ```
sudo apt-get install libdvdread3
```
and tell me how the dvd's go boys.
also do a ```
sudo apt-get install libdvdcss2
```
The"2" is crucial

---

