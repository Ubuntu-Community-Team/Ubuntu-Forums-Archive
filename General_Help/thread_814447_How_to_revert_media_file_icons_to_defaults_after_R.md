---
title: "How to revert media file icons to defaults after RealPlayer installation"
date: 2008-05-31
forum: General Help
---

### Post by dwasifar on 2008-05-31
Many people here have had the unwelcome experience of installing RealPlayer  and finding that the installation has assigned RealPlayer icons to their mp3, movie, and other media file formats.  There has been a lot of thrashing around with people trying to figure out how to reverse the changes.  

I had the same problem with Realplayer 11 installation setting up all sorts of default icons without asking. I looked at its logs and found 173 xdg-icon-resource commands forcing its icons into the desktop icon system.

Needless to say I was not amused.

Fortunately the installation log provided enough information to reverse the damage. Here is how to do it.

1) Open your text editor, copy the text below, and paste it into your editor:

```

#!/bin/sh
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ram
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-rm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-ra
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 text-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-avi
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-mov
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-rv
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-swf
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-vorbis+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-x-theora+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-rn-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-windows-acm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-windows-pcm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 text-vnd.rn-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-vnd.rn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia-vbr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realmedia-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realsystem-rmj
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-vnd.rn-realsystem-rmx
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 image-vnd.rn-realpix
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-vnd.rn-realvideo
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-vnd.rn-realvideo-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-aac
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-smil+xml
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-x-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 application-sdp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-basic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-pn-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 audio-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-x-real-video
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 48 video-mpeg4-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ram
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-rm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-ra
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 text-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-avi
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-generic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-mov
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-rv
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-swf
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-vorbis+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-x-theora+ogg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mp3
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-m4a
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mp4
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-rn-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpeg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpg
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-mpegurl
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-scpls
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-wav
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-windows-acm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-windows-pcm
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 text-vnd.rn-realtext
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-vnd.rn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-realaudio
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realaudio-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia-vbr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realmedia-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realsystem-rmj
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-vnd.rn-realsystem-rmx
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 image-vnd.rn-realpix
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-vnd.rn-realvideo
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-vnd.rn-realvideo-secure
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-aac
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-smil
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-smil+xml
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-x-streamingmedia
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 application-sdp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-basic
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-au
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-pn-aiff
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-x-rn-3gpp-amr-wb-encrypted
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 audio-3gpp2
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-x-real-video
xdg-icon-resource uninstall --novendor --noupdate --context mimetypes --size 192 video-mpeg4-generic
xdg-icon-resource forceupdate
```

2) Save it as an .sh file. (I named mine fixicons.sh.)

As an alternative to the above steps, you can download my script here: [http://www.dwasifar.com/fixicons.sh]("http://www.dwasifar.com/fixicons.sh")

3) Set it executable (right-click, Properties, Permissions, and check Executable).
4) Double-click to run.

This should reverse all RealPlayer's icon mischief, but **results are not guaranteed.** You may want to check the RealPlayer install log for yourself first.  **Also, please note** that if you had previously set up custom icons for the media file types, this script will not restore them; it will instead return the icon mappings to the default (presumably what was in place when you first installed Ubuntu).

---

