---
title: "Bunch of jpegs to movie (not DVD) with fade?"
date: 2006-08-03
forum: General Help
---

### Post by stuporglue on 2006-08-03
I need to make a bunch of video clips from folders of jpegs that will be playable on any computer (Win/OSX/Lin) with typical software installed. The videos need to have audio along with them. 

Since this is a repetitive process, I'd prefer a command line or at least a scriptable program. :-)

I'd like the movie to fade between each picture as well. The fade can be a cross fade (picture-->picture) or picture-->black-->picture. 

What are my file format options and program options? 

Thank you

---

### Post by zxee on 2006-08-03
I like this for authoring [http://tovid.berlios.de/en/index.html](http://tovid.berlios.de/en/index.html)
I'm not an expert though. As to the multi platform compatibility that depends on what's installed by default doesn't it? Mac OS X will generally play most standard formats. I don't about windows-for video.

---

### Post by stuporglue on 2006-08-03
> As to the multi platform compatibility that depends on what's installed by default doesn't it?

Correct. So, it'd need to be a format that QuickTime (installed on most Macs) and WMP (installed on most Windows) both can play. Maybe mpg (MPEG-1) files or some type of AVI? Maybe I'll just include VLC on the disks I give away.

Tovid might be helpfull -- it can make VCDs, which are essentially MPEG-1 files, I think. 

Thank you

---

### Post by orb9220 on 2006-08-03
dvd-slideshow

tools to create dvd slideshow with menus
dvd-slideshow
 This is the main script. It generates a DVD-compatible MPEG2 video file
with audio from a text file input listing of pictures and effects.

dvd-menu
Creates a simple DVD menu with buttons that link to MPEG2 files generated
with dvd-slideshow or ones that you have created yourself.

kmediafactory

template based DVD authoring tool for KDE.
kMediaFactory is an easy to use template based DVD authoring tool. You can
quickly create DVD menus for home videos and TV recordings in three simple
steps.

couple in sysnaptic

---

### Post by stuporglue on 2006-08-03
> dvd-slideshow

tools to create dvd slideshow with menus
dvd-slideshow
This is the main script. It generates a DVD-compatible MPEG2 video file
with audio from a text file input listing of pictures and effects.

Despite the title saying "(not DVD)", this is what I ended up using. I put the jpegs in a folder and use dir2slideshow to create a dvd-slideshow config file. I then run dvd-slideshow which creates a VOB file (MPEG2 video). Now, not everyone has an MPEG2 player on their computer, and the file is larger than I want, so I run it through ffmpeg to get the size and quality I want in MPEG-1 format. 

```
ffmpeg -i ~/Desktop/mymov/My_slideshow.vob -b 1024 -s 600x600  ~/Desktop/mymov/slide4.mpg
```
-b <bitrate> 
-s <size> 
-i <input file>

Bit of a work arround, the the transitions are nice, and it does work. :-)

---

