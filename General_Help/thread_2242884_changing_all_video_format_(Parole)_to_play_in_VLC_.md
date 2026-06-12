---
title: "changing all video format (Parole) to play in VLC as default"
date: 2014-09-04
forum: General Help
---

### Post by manuleka on 2014-09-04
Is there a way changing all file type (defaulted to Parole) set to VLC in a single action (once) instead of me going through MIME Type Editor and setting these individually manually?

cheers

---

### Post by Toz on 2014-09-04
This worked for me.

All of the mimetypes that vlc recognizes are listed in the /usr/share/applications/vlc.desktop file. Specifically:
```
$ cat /usr/share/applications/vlc.desktop  | grep MimeType
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;audio/amr;audio/amr-wb;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;application/xspf+xml;x-scheme-handler/mms;x-scheme-handler/rtmp;x-scheme-handler/rtsp;

```

Your current set of mimetype associations are listed in ~/.local/share/applications/mimeapps.list. The format of this file is such that there are two sections: "[Default Applications]" and "[Added Associations]". 

Before you proceed, backup this file:
```
cp ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeapps.list.BAK
```
...then open the file in mousepad and global replace all instances of parole with vlc. Save the file.

There may still be other associations that parole holds that aren't listed in this file (system defaults), so we're going to add all of the associations that vlc recognizes to the bottom of this file in the "[Added Associations]" section.
[LIST=1]
[*]Ensure that you have a "[Added Associations]" section in ~/.local/share/applications/mimeapps/list. If its not there, add it to the end of the file and save the file. (Note: the word "Added Associations" in square brackets).
[*]Then, run this command to get all of vlc's associations, parse them correctly, and append them to the end of that file:
```
for mtype in $(cat /usr/share/applications/vlc.desktop  | grep MimeType | sed -e 's/MimeType=//g' | sed -e 's/;/=vlc.desktop; /g'); do echo $mtype >> ~/.local/share/applications/mimeapps.list; done
```
[*]If thunar is running, close it and re-open and check that the default applications have properly changed.
[/LIST]
If anything goes wrong, simpy restore the ~/.local/share/applications/mimeapps.list file that we backed up earlier.

---

### Post by mc4man on 2014-09-04
Something similar to the above, sets all that vlc's .desktop has listed. 
for video - 
```
grep "^MimeType=" /usr/share/applications/vlc.desktop | cut -d "=" -f 2   | xargs -d ';' -n 1 | grep -e "^video/" -e "^x-content/video"   | xargs -n 1 -I '{}' xdg-mime default vlc.desktop '{}'
```

for audio
```
grep "^MimeType=" /usr/share/applications/vlc.desktop | cut -d "=" -f 2   | xargs -d ';' -n 1 | grep -e "^audio/" -e "^x-content/audio"   | xargs -n 1 -I '{}' xdg-mime default vlc.desktop '{}'
```

To keep in mind - 
there are a couple of instances where 2 or more mimes are basically setting the same thing, one example below. It can be an issue if all aren't set to same .desktop. (actually behind a current bug in gnome's system settings > default applications ...
video/mp4
video/mp4v-es
video/x-m4v

So if .mp4 doesn't change then in ~/.local/share/applications/mimeapps.list make sure all of above are the same. ( or all that are there

---

