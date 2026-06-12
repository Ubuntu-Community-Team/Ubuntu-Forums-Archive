---
title: "n00b question about K3B"
date: 2005-07-19
forum: General Help
---

### Post by Strangerdave on 2005-07-19
Greetings,

New to Ubuntu, I migrated over from SUSE and really liked K3B.  I read some threads here and saw that one could use apt-get to install it.  I did this and found that when I type K3B in the root terminal to start the program I get the following:

```
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' sp ecifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop'  specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-extension-mp4'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-extension-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/dv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-nsv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-flc'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-matroska'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-asf'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-asx'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-wax'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-real-audio'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'misc/ultravox'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-aiff'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-au'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-wav'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-windows-acm'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'image/vnd.rn-realpix'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies und efined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies und efined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies  undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.wordperfect'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/rtf'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'text/richtext'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645math.desktop' specifies un defined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/math.desktop' specifies undefined mime type/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-icb'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicet ype 'application/binary-certificate'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/xpm'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/g3fax'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-compressed-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-fits'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-sgi'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-sun-raster'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xwindowdump'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/wav'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies und efined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies und efined mimetype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimet ype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimet ype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'fontthumbnail.desktop' specifies undefined mimetype/serv icetype 'ThumbCreator'
kbuildsycoca: WARNING: 'Multimedia/k3b.desktop' specifies undefined mimetype/ser vicetype 'application/x-k3b'
kbuildsycoca: WARNING: '/usr/share/applications/gfloppy.desktop' specifies undef ined mimetype/servicetype 'x-device/floppy'
kbuildsycoca: WARNING: 'katepart.desktop' specifies undefined mimetype/servicety pe 'text/x-fortran'
kbuildsycoca: WARNING: '/usr/share/applications/gnome-stones.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-stones'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetyp e 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-ar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-bzip-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-gtar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-lhz'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-rar-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'multipart/x-zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-war'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-ear'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-java-archive'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-cd-image'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mi metype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mi metype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'application/vnd.lotus-1-2-3'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'text/x-comma-separated-values'
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
``` 

I am reasonably new to Linux, very new to Ubuntu...does this mean that I can not use K3B.  I am holding off using it but it seems as if GIMP really has a problem with it.  If it does appear to be a problem, how do I uninstall it, or any other program for that matter?

Thanks for any and all help!

-SD-

---

### Post by Seth on 2005-07-19
[QUOTE=Strangerdave]Greetings,

New to Ubuntu, I migrated over from SUSE and really liked K3B.  I read some threads here and saw that one could use apt-get to install it.  I did this and found that when I type K3B in the root terminal to start the program I get the following:

```
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
Session management error: Authentication Rejected, reason : None of the authenti cation protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' sp ecifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop'  specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-extension-mp4'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-extension-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/dv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/msvideo'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-anim'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-avi'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-nsv'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-flc'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'video/x-fli'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-matroska'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-m4a'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-asf'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-asx'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-ms-wax'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-real-audio'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'misc/ultravox'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-aiff'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-au'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-wav'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-windows-acm'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'image/vnd.rn-realpix'
kbuildsycoca: WARNING: '/usr/share/applications/totem.desktop' specifies undefin ed mimetype/servicetype 'audio/x-pn-realaudio-plugin'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifi es undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies und efined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies und efined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies  undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.wordperfect'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/rtf'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'text/richtext'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645math.desktop' specifies un defined mimetype/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/math.desktop' specifies undefined mime type/servicetype 'application/vnd.sun.xml.writer.math'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-icb'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined  mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: 'kcertpart.desktop' specifies undefined mimetype/servicet ype 'application/binary-certificate'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gthumb.desktop' specifies undefi ned mimetype/servicetype 'image/xpm'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/g3fax'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-compressed-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-fits'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-gray'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-png'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-portable-anymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-portable-graymap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-psd'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-sgi'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-sun-raster'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-tga'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xbitmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xcf'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xpixmap'
kbuildsycoca: WARNING: '/usr/share/applications/gimp-2.2.desktop' specifies unde fined mimetype/servicetype 'image/x-xwindowdump'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/wav'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/mp3'
kbuildsycoca: WARNING: '/usr/share/applications/XMMS.desktop' specifies undefine d mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies und efined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645web.desktop' specifies und efined mimetype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimet ype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/web.desktop' specifies undefined mimet ype/servicetype 'application/vnd.stardivision.writer.global'
kbuildsycoca: WARNING: 'fontthumbnail.desktop' specifies undefined mimetype/serv icetype 'ThumbCreator'
kbuildsycoca: WARNING: 'Multimedia/k3b.desktop' specifies undefined mimetype/ser vicetype 'application/x-k3b'
kbuildsycoca: WARNING: '/usr/share/applications/gfloppy.desktop' specifies undef ined mimetype/servicetype 'x-device/floppy'
kbuildsycoca: WARNING: 'katepart.desktop' specifies undefined mimetype/servicety pe 'text/x-fortran'
kbuildsycoca: WARNING: '/usr/share/applications/gnome-stones.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-stones'
kbuildsycoca: WARNING: 'knotify.desktop' specifies undefined mimetype/servicetyp e 'KNotify'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-ar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-bzip-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-compressed-tar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-gtar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-lhz'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-rar-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'multipart/x-zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-war'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-ear'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-java-archive'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies u ndefined mimetype/servicetype 'application/x-cd-image'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mi metype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: 'OpenOffice.org1.1/writer.desktop' specifies undefined mi metype/servicetype 'application/x-doc'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'application/vnd.sun.xml.math'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'application/vnd.lotus-1-2-3'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645calc.desktop' specifies un defined mimetype/servicetype 'text/x-comma-separated-values'
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
``` 

I am reasonably new to Linux, very new to Ubuntu...does this mean that I can not use K3B.  I am holding off using it but it seems as if GIMP really has a problem with it.  If it does appear to be a problem, how do I uninstall it, or any other program for that matter?

Thanks for any and all help!

-SD-[/QUOTE]
 You should NOT be running any program as root, so that would be a good place to start.

---

### Post by wellery on 2005-07-19
Why are you running it as root? What happens when you run it as a normal user and those error messages are just warnings. Does it crash or still work? I notice that when i run it in the terminal i get warnings as well but it still works.

---

### Post by Strangerdave on 2005-07-19
Hummm...interesting.  So I try it as user and get the same message.... ](*,) 

Okay i'll take the cheese even though its hooked up to the buzzer...

Maybe some more information would be helpful?

-SD-

EDIT:  Tried again as user and this is the message I recieved:

```
kbuildsycoca running...
k3b: WARNING: KGenericFactory: instance requested but no instance name or about data passed to the constructor!
``` 

The curser is blinking but the program seems to load up.  Humm...

EDIT#2:  Stopped thinking and this is what was said...

[HTML]k3b: ERROR: ```
(K3bSongManager) Can't open file /home/dsnorris/.kde/share/apps/k3b/songlist.xml
```

---

