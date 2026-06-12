---
title: "How to update Ubuntu-Restricted-Packages?"
date: 2016-04-15
forum: General Help
---

### Post by dgeorge093 on 2016-04-15
I just installed this package. I noticed in the software center, it says canonical doesn't provide updates for these packages. Is there something I need to do to keep these up to date? 

Thanks,

---

### Post by randy33 on 2016-04-15
I have the same issue.

---

### Post by Bucky Ball on 2016-04-15
Where does it say this and what exactly does it say? Attach a screenshot if possible (Adv Reply> paperclip icon to attach a pic, please). This is not 'an issue'. There is probably some third-party software in the restricted extras that Canonical has no control over, including its updating/upgrading. 

Hopefully someone can give a fuller explanation.

---

### Post by grahammechanical on 2016-04-15
It says it in the software centre. These are third party software. They are free in the sense that we can download, install & use the software according to various licences but any updates must come from the owners of that software.

When we install Ubuntu if we tick the box "Install third party software" then we will get the audio & video codecs in Ubuntu Restricted Extras. I have never worried about updating this software in all the years I have been using Ubuntu. Do codecs need updating? Don't think so.

Regards.

---

### Post by deadflowr on 2016-04-15
Canonical doesn't provide updates for those packages.
They only provide updates for packages in the main repository.

Updates for packages that Canonical doesn't provide updates for come through the Community.

But anyhoo, the restricted extras package is actually a bundle of many other smaller packages, that, on their own, should all get updates individually.
The package was put together to ease the installation process, really.

---

### Post by vasa1 on 2016-04-15
> **grahammechanical said:**
> ... Do codecs need updating? ...
I think I've seen and accepted quite a few updates to chromium-codecs in Lubuntu 14.04 LTS.

```
09:25 AM .../log/apt $ zgrep codecs history.*
history.log.10.gz:Upgrade: google-chrome-stable:amd64 (43.0.2357.81-1, 43.0.2357.124-1), chromium-codecs-ffmpeg-extra:amd64 (41.0.2272.76-0ubuntu0.14.04.1.1076, 43.0.2357.81-0ubuntu0.14.04.1.1089)
history.log.13.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (40.0.2214.111-0ubuntu0.14.04.1.1069, 41.0.2272.76-0ubuntu0.14.04.1.1076)
history.log.14.gz:Binary file (standard input) matches
history.log.17.gz:Install: libmimic0:amd64 (1.0.4-2.1ubuntu1, automatic), libmpeg2-4:amd64 (0.5.1-5ubuntu1, automatic), libopencv-core2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libdc1394-22:amd64 (2.2.1-2ubuntu2, automatic), gstreamer1.0-plugins-bad-faad:amd64 (1.2.4-1~ubuntu1, automatic), libopencv-ml2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), oxideqt-codecs-extra:amd64 (1.2.5-0ubuntu0.14.04.1), libchromaprint0:amd64 (1.1-1, automatic), libopencv-video2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libsbc1:amd64 (1.1-2ubuntu2, automatic), libspeexdsp1:amd64 (1.2~rc1.1-1ubuntu1, automatic), gstreamer1.0-libav:amd64 (1.2.4-1~ubuntu1), liboil0.3:amd64 (0.3.17-2ubuntu4, automatic), libgomp1:amd64 (4.8.2-19ubuntu1, automatic), gstreamer1.0-plugins-base:amd64 (1.2.4-1~ubuntu1, automatic), libopencore-amrwb0:amd64 (0.1.3-2ubuntu1, automatic), libcdaudio1:amd64 (0.99.12p2-13, automatic), libvo-aacenc0:amd64 (0.1.3-1, automatic), libfftw3-double3:amd64 (3.3.3-7ubuntu3, automatic), libilmbase6:amd64 (1.0.1-6ubuntu1, automatic), libopenal1:amd64 (1.14-4ubuntu1, automatic), libopencv-legacy2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libzbar0:amd64 (0.10+doc-9build1, automatic), chromium-codecs-ffmpeg-extra:amd64 (38.0.2125.111-0ubuntu0.14.04.1.1061), gstreamer0.10-plugins-bad:amd64 (0.10.23-7.2ubuntu1), libwildmidi-config:amd64 (0.2.3.4-2.1ubuntu3, automatic), libwildmidi1:amd64 (0.2.3.4-2.1ubuntu3, automatic), flashplugin-installer:amd64 (11.2.202.418ubuntu0.14.04.1), libgme0:amd64 (0.5.5-2, automatic), libsrtp0:amd64 (1.4.5~20130609~dfsg-1, automatic), libopencv-features2d2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libopencv-objdetect2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), freepats:amd64 (20060219-1, automatic), libflite1:amd64 (1.4-release-8, automatic), libasound2-plugins:amd64 (1.0.27-2ubuntu2, automatic), gstreamer0.10-fluendo-mp3:amd64 (0.10.23.debian-3), libgles2-mesa:amd64 (10.1.3-0ubuntu0.2, automatic), libopencv-imgproc2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libopenal-data:amd64 (1.14-4ubuntu1, automatic), libtwolame0:amd64 (0.3.13-1ubuntu1, automatic), libdvdnav4:amd64 (4.2.1-3, automatic), libzvbi0:amd64 (0.2.35-2, automatic), ubuntu-restricted-addons:amd64 (20), libdirac-encoder0:amd64 (1.0.2-6ubuntu1, automatic), gstreamer1.0-plugins-ugly:amd64 (1.2.3-2build1), gstreamer1.0-plugins-bad:amd64 (1.2.4-1~ubuntu1), libslv2-9:amd64 (0.6.6+dfsg1-2, automatic), libopenexr6:amd64 (1.6.1-7ubuntu1, automatic), libgstreamer-plugins-good1.0-0:amd64 (1.2.4-1~ubuntu1, automatic), libopencv-highgui2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libgtkglext1:amd64 (1.2.0-3.1fakesync3, automatic), libgstreamer-plugins-bad0.10-0:amd64 (0.10.23-7.2ubuntu1, automatic), libofa0:amd64 (0.9.3-5ubuntu1, automatic), libopencv-calib3d2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), gstreamer1.0-plugins-bad-videoparsers:amd64 (1.2.4-1~ubuntu1, automatic), libspandsp2:amd64 (0.0.6~pre21-2, automatic), libzvbi-common:amd64 (0.2.35-2, automatic), gstreamer1.0-fluendo-mp3:amd64 (0.10.23.debian-3), libsoundtouch0:amd64 (1.7.1-5, automatic), libsidplay1:amd64 (1.36.59-5ubuntu1, automatic), libopencv-contrib2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libkate1:amd64 (0.4.1-1ubuntu1, automatic), libopencv-flann2.4:amd64 (2.4.8+dfsg1-2ubuntu1, automatic), libvo-amrwbenc0:amd64 (0.1.3-1, automatic), libgstreamer-plugins-bad1.0-0:amd64 (1.2.4-1~ubuntu1, automatic), libmpcdec6:amd64 (0.1~r459-1ubuntu3, automatic), gstreamer0.10-plugins-ugly:amd64 (0.10.19-2ubuntu5), libopencore-amrnb0:amd64 (0.1.3-2ubuntu1, automatic), libtbb2:amd64 (4.2~20130725-1.1ubuntu1, automatic)
history.log.17.gz:Upgrade: oxideqt-codecs-extra:amd64 (1.2.5-0ubuntu0.14.04.1, 1.3.4-0ubuntu0.14.04.1), language-pack-gnome-en:amd64 (14.04+20140707, 14.04+20141110)
history.log.17.gz:Commandline: apt-get purge oxideqt-codecs-extra
history.log.17.gz:Purge: oxideqt-codecs-extra:amd64 (1.3.4-0ubuntu0.14.04.1)
history.log.17.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (38.0.2125.111-0ubuntu0.14.04.1.1061, 39.0.2171.65-0ubuntu0.14.04.1.1064)
history.log.1.gz:Upgrade: libjavascriptcoregtk-3.0-0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), libwebkitgtk-1.0-0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), gir1.2-javascriptcoregtk-3.0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), chromium-codecs-ffmpeg-extra:amd64 (48.0.2564.116-0ubuntu0.14.04.1.1111, 49.0.2623.87-0ubuntu0.14.04.1.1112), libwebkitgtk-3.0-0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), libwebkitgtk-3.0-common:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), libwebkitgtk-1.0-common:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), libjavascriptcoregtk-1.0-0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1), gir1.2-webkit-3.0:amd64 (2.4.8-1ubuntu1~ubuntu14.04.1, 2.4.10-0ubuntu0.14.04.1)
history.log.1.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (49.0.2623.87-0ubuntu0.14.04.1.1112, 49.0.2623.108-0ubuntu0.14.04.1.1113), libpcre3:amd64 (8.31-2ubuntu2.1, 8.31-2ubuntu2.2)
history.log.2.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (48.0.2564.82-0ubuntu0.14.04.1.1108, 48.0.2564.116-0ubuntu0.14.04.1.1111), libssh-4:amd64 (0.6.1-0ubuntu3.1, 0.6.1-0ubuntu3.3)
history.log.3.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (47.0.2526.73-0ubuntu0.14.04.1.1106, 47.0.2526.106-0ubuntu0.14.04.1.1107)
history.log.3.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (47.0.2526.106-0ubuntu0.14.04.1.1107, 48.0.2564.82-0ubuntu0.14.04.1.1108)
history.log.4.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (45.0.2454.101-0ubuntu0.14.04.1.1099, 47.0.2526.73-0ubuntu0.14.04.1.1106)
history.log.6.gz:Upgrade: linux-image-extra-3.13.0-65-generic:amd64 (3.13.0-65.105, 3.13.0-65.106), linux-image-3.13.0-65-generic:amd64 (3.13.0-65.105, 3.13.0-65.106), linux-headers-3.13.0-65-generic:amd64 (3.13.0-65.105, 3.13.0-65.106), chromium-codecs-ffmpeg-extra:amd64 (45.0.2454.85-0ubuntu0.14.04.1.1097, 45.0.2454.101-0ubuntu0.14.04.1.1099), linux-headers-3.13.0-65:amd64 (3.13.0-65.105, 3.13.0-65.106)
history.log.7.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (44.0.2403.89-0ubuntu0.14.04.1.1095, 45.0.2454.85-0ubuntu0.14.04.1.1097), ffmpeg:amd64 (2.7.2+git4~trusty, 2.8.0~trusty)
history.log.8.gz:Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12), chromium-codecs-ffmpeg-extra:amd64 (43.0.2357.130-0ubuntu0.14.04.1.1092, 44.0.2403.89-0ubuntu0.14.04.1.1095), apport-gtk:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12), apport:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12), python3-apport:amd64 (2.14.1-0ubuntu3.11, 2.14.1-0ubuntu3.12)
history.log.9.gz:Upgrade: chromium-codecs-ffmpeg-extra:amd64 (43.0.2357.81-0ubuntu0.14.04.1.1089, 43.0.2357.130-0ubuntu0.14.04.1.1092), libnss3-nssdb:amd64 (3.17.4-0ubuntu0.14.04.1, 3.19.2-0ubuntu0.14.04.1), libnss3:amd64 (3.17.4-0ubuntu0.14.04.1, 3.19.2-0ubuntu0.14.04.1)
09:26 AM .../log/apt $ 

```

---

### Post by mcduck on 2016-04-16
It's not uncommon for codecs to need updates to batch security holes. Didn't they just recommend uninstalling Quicktime codecs from Windows due to security issues? After all an embedded video or image file on a web page is pretty convenient way to get binary data to people's computers in a way the user will actually run the content...

---

### Post by dgeorge093 on 2016-04-16
I did just read it is recommended to drop Quicktime from Windows. The reason I ask is because last week Adobe released an emergency update to patch a security vulnerability in Flash Player. [http://money.cnn.com/2016/04/08/technology/adobe-emergency-update/](http://money.cnn.com/2016/04/08/technology/adobe-emergency-update/) I know this talks about Windows. Just curious about keeping this stuff up to date on my system.

---

