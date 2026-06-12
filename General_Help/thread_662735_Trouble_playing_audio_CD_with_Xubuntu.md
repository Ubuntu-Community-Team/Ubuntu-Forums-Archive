---
title: "Trouble playing audio CD with Xubuntu"
date: 2008-01-09
forum: General Help
---

### Post by luisito on 2008-01-09
I have Xubuntu in my older laptop. I replaced Totem-xine with Totem-gsreamer because it gives me a better result with the movies that my digital camera produces. The problem is that I cannot play audio CDs. I must say that I never tried with Totem-xine, but I am not going back there anyway.

Here is a more detailed description of the problem:

When I insert an audio CD, Totem launches and gives the error message:"location not found".

I can reproduce the same behaviour by running from the command line: totem cdda:
and I can see in the console the slightly more detailed error message: 
** Message: Error: Invalid URI "cdda:".

If I run totem cdda:// I get the error message (same if I run sudo totem cdda://):
** Message: Error: Could not open CD device for reading.

I am not sure what the right command line should be. So I also tried totem cdda:///dev/sda0 and got:
** Message: Missing plugin: gstreamer|0.10|totem|Audio CD source|urisource-cdda (Audio CD source)
no application found
** Message: No installation candidate for missing plugins found.
** Message: Error: A Audio CD source plugin is required to play this stream, but not installed.
gstplaybasebin.c(1604): gen_source_element (): /play:
No URI handler for cdda

** Message: Missing plugin: gstreamer|0.10|totem|Audio CD source|urisource-cdda (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

If I run mplayer cdda:// the cd plays (it's a bit cranky though). I want to make this computer usable to my mother so I want it to play in some program with a gui (preferably totem).

The problem looks very much to me like I am missing some package. I installed every gstreamer codec package I could see including:
gnome-media
gstreamer0.10-plugins-base
libgstreamer-plugins-base0.10-0
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gnomevfs
gstreamer0.10-gnonlin
gstreamer0.10-pitfdll

Also these are installed
cdparanoia
cdda2wav
libcdparanoia0
libcdio6

---

### Post by andrew.46 on 2008-03-04
Hi,

 I have the same problem with xfce. I can suggest a temporary fix for one problem though:

> **luisito said:**
> 

If I run mplayer cdda:// the cd plays (it's a bit cranky though).

```
$ mplayer -cache 10000 cdda://

```

        Andrew

---

### Post by cschoen on 2008-06-28
I am having the exact same problem. I can use VLC to play my 
CDs without a problem. I would very much like to use Totem for playing Audio CDs because I have very limited hard disk space and it appears that gstreamer must stay if I want to keep the desktop package installed for future upgrades.

I, too, have all of those packages installed as well as the latest version of libcdio (7). It strikes me as odd that Totem recognizes the CD (the option "Play Disc 'Audio Disc'" shows in the "Movie" menu but is grayed out. I've tried the "Open Location..." option and it says it is Playing but I hear nothing and the track timer does not move.

If anyone could help shed some light on this problem I would be so very grateful. You would help me make my old laptop computing experience much more efficient! Please don't hesitate to request more information about my software/hardware if it is needed to help diagnose the problem.

Thanks

---

