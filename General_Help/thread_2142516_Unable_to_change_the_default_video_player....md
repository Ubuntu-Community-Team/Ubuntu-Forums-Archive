---
title: "Unable to change the default video player..."
date: 2013-05-06
forum: General Help
---

### Post by Roasted on 2013-05-06
I have Totem, VLC, and SMPlayer installed. I'm trying to set the default video player, which of course is done globally in system settings - details - default applications. Whenever I select a new default application, close, and reopen the menu, it's still the same application it was before. I'm a little unsure of what to do seeing as though I'm not getting an error... I'm just simply not getting the results I expected.

This is an Ubuntu 13.04 system.

Thanks!

---

### Post by fantab on 2013-05-06
Look in dconf-editor, in com section. I am not on Ubuntu machine so can't confirm.
I remove default totem and use only VLC.

---

### Post by scouser73 on 2013-05-06
> **Roasted said:**
> I have Totem, VLC, and SMPlayer installed. I'm trying to set the default video player, which of course is done globally in system settings - details - default applications. Whenever I select a new default application, close, and reopen the menu, it's still the same application it was before. I'm a little unsure of what to do seeing as though I'm not getting an error... I'm just simply not getting the results I expected.

This is an Ubuntu 13.04 system.

Thanks!

You could try opening the folder with a video in, right clicking on a video and choosing Properties and then select Open With and find the player you wish to use as default.

---

### Post by Roasted on 2013-05-06
> **scouser73 said:**
> You could try opening the folder with a video in, right clicking on a video and choosing Properties and then select Open With and find the player you wish to use as default.

I did. That doesn't work either. The setting just simply never takes, and if I hit apply/okay/whatever, close out, go back in, it's back to how it was originally. Funny thing is, it's only with videos. If within System Settings - Details I change the default music program, it's absolutely fine and changes as expected. It's JUST videos...

---

### Post by mc4man on 2013-05-06
When you set globally thru SS it should write quite a number of new lines to ~/.local/share/applications/mimeapps.list,  under both the [Default Applications] & [Added Associations] headings. Subsequent changes to SS should alter the picked app's .desktop in [Default Applications] & add it to the lines under the [Added Associations] if not already there.

What does that file look like for you?

---

### Post by Roasted on 2013-05-06
Here's the mimeapps.list. I even renamed the original file and let the system re-generate a new one:

[Default Applications]
video/x-ogm+ogg=ghb.desktop
video/dv=totem.desktop
video/mpeg=ghb.desktop
video/x-mpeg=ghb.desktop
video/msvideo=ghb.desktop
video/quicktime=ghb.desktop
video/x-anim=totem.desktop
video/x-avi=ghb.desktop
video/x-ms-asf=totem.desktop
video/x-ms-wmv=totem.desktop
video/x-msvideo=totem.desktop
video/x-nsv=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop
video/x-flv=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/mp4=ghb.desktop
video/mp4v-es=ghb.desktop
video/mp2t=totem.desktop
video/x-matroska=ghb.desktop
video/webm=totem.desktop
video/avi=smplayer.desktop
video/flv=totem.desktop
video/x-ogm=smplayer.desktop
video/x-theora=smplayer.desktop
video/3gp=totem.desktop
video/3gpp=totem.desktop
video/divx=totem.desktop
video/fli=totem.desktop
video/ogg=totem.desktop
video/vivo=totem.desktop
video/vnd.divx=ghb.desktop
video/vnd.mpegurl=totem.desktop
video/vnd.vivo=totem.desktop
video/x-flic=totem.desktop
video/x-m4v=ghb.desktop
video/x-mpeg2=totem.desktop
video/x-ms-asx=totem.desktop
video/x-ms-wm=totem.desktop
video/x-ms-wmx=totem.desktop
video/x-ms-wvx=totem.desktop
video/x-theora+ogg=ghb.desktop
video/x-totem-stream=totem.desktop
audio/x-vorbis+ogg=clementine.desktop
audio/aac=clementine.desktop
audio/mp4=clementine.desktop
audio/mpeg=clementine.desktop
audio/mpegurl=clementine.desktop
audio/ogg=clementine.desktop
audio/vnd.rn-realaudio=clementine.desktop
audio/vorbis=clementine.desktop
audio/x-flac=clementine.desktop
audio/x-mp3=clementine.desktop
audio/x-mpeg=clementine.desktop
audio/x-mpegurl=clementine.desktop
audio/x-ms-wma=clementine.desktop
audio/x-musepack=clementine.desktop
audio/x-oggflac=clementine.desktop
audio/x-pn-realaudio=clementine.desktop
audio/x-scpls=clementine.desktop
audio/x-speex=clementine.desktop
audio/x-vorbis=clementine.desktop
audio/x-wav=clementine.desktop

[Added Associations]
video/mpeg=smplayer.desktop;totem.desktop;ghb.desktop;
video/quicktime=smplayer.desktop;totem.desktop;ghb.desktop;
video/x-ms-asf=smplayer.desktop;totem.desktop;
video/x-ms-wmv=smplayer.desktop;totem.desktop;
video/x-msvideo=smplayer.desktop;totem.desktop;
video/vnd.rn-realvideo=smplayer.desktop;totem.desktop;
video/mp4=smplayer.desktop;totem.desktop;ghb.desktop;
video/x-matroska=smplayer.desktop;totem.desktop;ghb.desktop;
video/x-ogm+ogg=smplayer.desktop;
video/avi=smplayer.desktop;
video/flv=smplayer.desktop;
video/x-ogm=smplayer.desktop;
video/x-theora=smplayer.desktop;
audio/aac=clementine.desktop;
audio/mp4=clementine.desktop;
audio/mpeg=clementine.desktop;
audio/mpegurl=clementine.desktop;
audio/ogg=clementine.desktop;
audio/vnd.rn-realaudio=clementine.desktop;
audio/vorbis=clementine.desktop;
audio/x-flac=clementine.desktop;
audio/x-mp3=clementine.desktop;
audio/x-mpeg=clementine.desktop;
audio/x-mpegurl=clementine.desktop;
audio/x-ms-wma=clementine.desktop;
audio/x-musepack=clementine.desktop;
audio/x-oggflac=clementine.desktop;
audio/x-pn-realaudio=clementine.desktop;
audio/x-scpls=clementine.desktop;
audio/x-speex=clementine.desktop;
audio/x-vorbis=clementine.desktop;
audio/x-wav=clementine.desktop;
video/dv=totem.desktop;
video/mp2t=totem.desktop;
video/mp4v-es=totem.desktop;ghb.desktop;
video/msvideo=totem.desktop;ghb.desktop;
video/webm=totem.desktop;
video/x-anim=totem.desktop;
video/x-avi=totem.desktop;ghb.desktop;
video/x-flc=totem.desktop;
video/x-fli=totem.desktop;
video/x-flv=totem.desktop;
video/x-mpeg=totem.desktop;ghb.desktop;
video/x-nsv=totem.desktop;
video/vnd.divx=ghb.desktop;
video/x-m4v=ghb.desktop;
video/x-theora+ogg=ghb.desktop;

It's interesting because if I have the file open in gedit and I select a new default videos application, I get a flag in gedit saying this file has changed, click reload to show the new content. I click reload and NOTHING changed. There's no VLC entry, just all Totem.

---

### Post by mc4man on 2013-05-06
Interesting...
I believe that only the listed MimeType= in an apps .desktop will be changed (set as default or added thru SS
So in that regard not all mimetypes would be changed to vlc, though in your case none are.

What is on the MimeType= line in vlc's .desktop?
```
gedit /usr/share/applications/vlc.desktop
```
Do you have a vlc.desktop anywhere else like /usr/local/share/applications or  ~/.local/share/applications ?

(the other mystery is why the r. click > properties > open with on any video file type > pick Vlc media player > set as default doesn't work

(also just for info
```
apt-cache policy vlc
```

---

### Post by Roasted on 2013-05-06
While I haven't tried any of your above suggestions, I just noticed something that I wanted to post here. I set up a fresh 13.04 VM. I installed SMPlayer and VLC. I went into system settings - details - default applications. I then did the following:

Selected VLC to be default video player
Closed System Settings
Reopened System Settings
VLC was still set as default

Selected "Videos" (Totem) to be default video player
Closed System Settings
Reopened System Settings
Totem was still set as default

Selected SMPlayer to be default video player
Closed System Settings
Reopened System Settings
SMPlayer was still set as default

(here's where it gets weird)

Selected Totem to be default video player
Closed System Settings
Reopened System Settings
SMPlayer was still set as default

Selected VLC to be default video player
Closed System Settings
Reopened System Settings
SMPlayer was still set as default

So once I installed SMPlayer and began tinkering with it, it somehow confused/borked something to strong-arm the default position.

EDIT - Come to think of it, it may not be due to SMPlayer entirely. I just did an apt-get remove --purge of SMPlayer. Now Totem is strong-holding the default position, even if I select VLC.

rageragerageragerage

---

### Post by Roasted on 2013-05-06
Well, I went into (right click on the MP4 file) properties - open with - and selected VLC as default. It wouldn't let the setting stick. It flashed real quick but kept Totem as the default. I ended up hitting the "reset" button on the left. After that I was able to select VLC as my default, which works great. However, I'm a little confused over how I'm still seeing weirdness in my System Settings - Details - Default Applications menu. If I select VLC, quit, go back, it's still Totem. Why is that?

---

### Post by mc4man on 2013-05-06
Can't dupe your issue no matter how I try, all changes persist & are reflected in mimeapps.list
Have to go out, will give some thought

---

### Post by Roasted on 2013-05-06
> **mc4man said:**
> Can't dupe your issue no matter how I try, all changes persist & are reflected in mimeapps.list
Have to go out, will give some thought

A user in the Ubuntu IRC channel was able to duplicate my findings. They said since GCC (gnome control center, aka system settings) does not hold the settings properly, but Nautilus does (Right click file - Properties - Open With - Set Default), that it's a GCC issue, so I filed a bug accordingly.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1177012](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1177012)

Basically it seems like the applications fight over who will be the actual default application. If SMPlayer is installed and I select it as default, it refuses to let me choose VLC or Totem. I mean, I can select it, it looks fine, but if I close/reopen it's back to SMPlayer. If I apt-get remove smplayer and do the same things, this time Totem is the one who's continually set as default even if I select VLC as default. But fortunately as least the Nautilus way (properties - open with) works without issue.

---

