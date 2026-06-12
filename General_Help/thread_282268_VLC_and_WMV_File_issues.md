---
title: "VLC and WMV File issues"
date: 2006-10-22
forum: General Help
---

### Post by Magiczero on 2006-10-22
Hi

I am trying to play a wmv video using vlc and I hear audio but no video.  Why?  Can I get help here please?

Thanks

---

### Post by tronica on 2006-10-22
becuase WMV's are evil :twisted: 

make sure you have w32codecs installed, check the link below

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)

---

### Post by Magiczero on 2006-10-22
When I did what the website told me to do I got this

> tanner@tanner-desktop:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
> gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
> gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-gl is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
tanner@tanner-desktop:~$




---

### Post by tronica on 2006-10-22
sorry about that, first do this

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

then do the other. That should get you going.

---

