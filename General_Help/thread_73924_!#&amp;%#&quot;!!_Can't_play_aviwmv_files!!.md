---
title: "!#&amp;%#&quot;!! Can't play avi/wmv files!!"
date: 2005-10-10
forum: General Help
---

### Post by Panthios on 2005-10-10
Hi.

First, I have just reinstalled Kubuntu cause I couldn't play avi/wmv files wich normally require w32codecs.
And yes, I HAVE installed the w32codecs but still no go.
I even tried to download the codecs from mplayer's homepage.

Xine says something about media is scrambled.

I don't have libdvdcss2 wich I think is the one missing, but here is the problem:
libdvdcss2: Afhængigheder: libc6 (>= 2.3.2.ds1-21) men 2.3.2.ds1-20ubuntu13 er installeret, og den er tilbageholdt.

(It's danish, but it says that a older version of libc6 is installed)

HELP!?? Since I've just reinstalled everything and duing EVERYTHING by the book, and it still won't work I possible can't be the only one with this problem!

Please help.

---

### Post by Zelut on 2005-10-10
well to install libdvdcss you can run the script found here:

/usr/share/doc/libdvdread3/examples/install-css.sh

that may help with that missing package... try it & see what else we need to do

---

### Post by Panthios on 2005-10-10
[QUOTE=kuyaedz]well to install libdvdcss you can run the script found here:

/usr/share/doc/libdvdread3/examples/install-css.sh

that may help with that missing package... try it & see what else we need to do[/QUOTE]

Hi, the script worked great. Libdvdcss is now installed, but Xine gives same error. I have no clue .,.....

---

### Post by Panthios on 2005-10-10
No body else with this problem?
Would be a bit wicked if others could just install Hoary, add the repo's, install codecs and the watch movies, but I can't! :confused: :confused:

---

### Post by Perfect Storm on 2005-10-10
You can get libdvdcss2 here: [http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)

and you got?:
gstreamer0.8-plugins
gstreamer0.8-lame
gstreamer0.8-ffmpeg
w32codecs
libdivx4linux
lame
sox
ffmpeg
mjpegtools
vorbis-tools

---

### Post by nocturn on 2005-10-11
[QUOTE=Panthios]Hi, the script worked great. Libdvdcss is now installed, but Xine gives same error. I have no clue .,.....[/QUOTE]

dvdcss only works on CSS encrypted streams (typically on a DVD).
I think the file you are trying to view is an encrypted WMV file and AFAIK there is no way but mediaplayer to play these.  

Thanks to DRM for this.

---

### Post by Panthios on 2005-10-11
[QUOTE=nocturn]dvdcss only works on CSS encrypted streams (typically on a DVD).
I think the file you are trying to view is an encrypted WMV file and AFAIK there is no way but mediaplayer to play these.  

Thanks to DRM for this.[/QUOTE]

What? But they worked before! Before I installed Kubuntu, they worked in Ubuntu (before the repo's was going official)

You cannot tell me, that nobody in here can watch WMV files!

---

### Post by Panthios on 2005-10-12
Bump.
Can somebody justify that they can/cannot watch wmv files?

---

### Post by Hairy_Palms on 2005-10-12
i watch wmv files but not in mplayer, i can play them if i apt-get totem-xine xine is needed as gstreamer cant use the w32 codecs.

---

### Post by lninjo on 2008-01-21
what happens if you use some sort of media player in wine will it work?

---

### Post by AlanR8 on 2008-01-21
For better or worse, when I do a rebuild I always use Automatix (wwwgetautomatix.com)to install all the necessary media codecs and DVD files.

Always worked a treat for me.

---

