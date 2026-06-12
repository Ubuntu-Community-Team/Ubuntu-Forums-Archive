---
title: "Gnome-tweak-tool NEED HELP Mines keeps starting and wont stop.."
date: 2015-09-28
forum: General Help
---

### Post by CWZ on 2015-09-28
Ok so I need to know how/were(what) conf file **gnome tweak** tool changes/uses to set up start up programs. I installed it to try and fix **Ubuntu-tweak** issues but inadvertently set up a start up application and then removed **gnome-tweak**. NOW the startup program starts up every time and even when i tried to just reinstall **gnome-tweak** to turn it off gnome tweak doesn't even show it as in the start up list. I did a system wide search for start up, found a few files that are *not* it, and a couple that might be **but** they are binary files and i don't want to just delete them. So I am at an impasse and need help.

---

### Post by CWZ on 2015-10-02
I am having a problem that I posted about but it seems I cant get any answers. ( [my post]("http://ubuntuforums.org/showthread.php?t=2296795") ) So I guess I need to learn how to  track down the creator of the gnome-tweak-tool that I used. Witch leads me to ask:
_***How do I get info on a packet/program in apt-get repo?***_

---

### Post by slickymaster on 2015-10-02
Threads merged.

You can start here: [https://wiki.gnome.org/action/show/Apps/GnomeTweakTool?action=show&redirect=GnomeTweakTool](https://wiki.gnome.org/action/show/Apps/GnomeTweakTool?action=show&redirect=GnomeTweakTool)

---

### Post by CWZ on 2015-10-06
OK How do I ask ::_***How do I get info on a packet/program in apt-get repo? ***_Since Thats what I was asking. I get that I referenced my previous post that was getting no reply but the subject of that post was not the only packet/program that I need to locate info on. To help illustrate, I also need info on a few other packets/programs. Also the link you referred to I had already read and can see that it is not the same version that apt-get had downloaded from the repo. Hence the reason I didn't ask :: How do I Google Gnome-Tweak tool but rather ...:: _***How do I get info on a packet/program in apt-get repo?***_ While they seem similar they are not. I am trying to get info on how to get more info on things in repos _***VIA***_ apt-get. So pleas help me to understand how to ask a question on this matter with out having you merge it into a thread that dose not reflect the issue nor subject any farther than an example of one aspect of the issue. I am not trying to complain I am simply trying to ascertain a less ignorant position on how to stop this from happening in the future. As I forsee more questions that while they are not about a problem I have already faced BUT may be more easily illuminated by referencing the aforementioned problems.

---

### Post by slickymaster on 2015-10-06
Use ```
apt-cache show packageName
```It will display what the package is designed to do, version info and so forth.
As an example```
~$ apt-cache show parole
Package: parole
Priority: optional
Section: universe/xfce
Installed-Size: 1708
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>
Architecture: i386
Version: 0.8.0-2ubuntu2
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libclutter-1.0-0 (>= 1.10.0), libclutter-gtk-1.0-0 (>= 0.91.8), libdbus-1-3 (>= 1.9.14), libdbus-glib-1-2 (>= 0.88), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.41.1), libgstreamer-plugins-base1.0-0 (>= 1.0.0), libgstreamer1.0-0 (>= 1.0.0), libgtk-3-0 (>= 3.11.5), libnotify4 (>= 0.7.0), libtagc0 (>= 1.5), libx11-6, libxfce4ui-2-0 (>= 4.11.1), libxfce4util7 (>= 4.9.0), libxfconf-0-2 (>= 4.6.0), gstreamer1.0-clutter, gstreamer1.0-x, gstreamer1.0-libav, gstreamer1.0-plugins-base, gstreamer1.0-alsa | gstreamer1.0-audiosink, gstreamer1.0-plugins-good
Recommends: gstreamer1.0-pulseaudio
Suggests: gstreamer1.0-plugins-ugly, gstreamer1.0-plugins-bad, gnome-codec-install
Filename: pool/universe/p/parole/parole_0.8.0-2ubuntu2_i386.deb
Size: 311634
MD5sum: cb3088b180c206849419bbdb5c53c770
SHA1: 97ef9bf2f06f431afa313f92f2736d09abe7353e
SHA256: e1831c33ff32c4a075456395bc3cd769b3a77cfdf83b60dada3394d5d932e1cf
Description-en: media player based on GStreamer framework
 Parole is a media player for the Xfce desktop environment, written using the
 GStreamer framework.
 .
 Parole features playback of local media files, including video with subtitles
 support, DVD/CD and live streams; it is also extensible via plugins.
 .
 This package contains Parole media player.
Description-md5: 4483a597da4d512da23e2a9ae41ea0f8
Homepage: http://goodies.xfce.org/projects/applications/parole
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: xubuntu-desktop, ubuntustudio-desktop

```

From ```
man apt-cache
```> **DESCRIPTION**
**apt-cache** performs a variety of operations on APT's package cache.
       **apt-cache** does not manipulate the state of the system but does provide
       operations to search and generate interesting output from the package
       metadata.

---

### Post by CWZ on 2015-10-06
Ok thank you, that solved that problem. BUT the other problem that caused my threads to be merged is still at large. How in the future, do I keep my threads from being merged? Should I attempt a less erroneous method of projecting my quandary? Either way thank you for solving the issue of the 2nd quarry. Now maybe somebody will come along and help me with the 1st one before I fix it my self. If I should fix it first, Ill be sure to post my findings for anyone else who develops this problem. Again thank you.

---

### Post by howefield on 2015-10-06
> **CWZ said:**
> Ok thank you, that solved that problem. BUT the other problem that caused my threads to be merged is still at large. How in the future, do I keep my threads from being merged? 

Generally speaking, one thread per issue (or closely related issue).

> Now maybe somebody will come along and help me with the 1st one before I fix it my self. If I should fix it first, Ill be sure to post my findings for anyone else who develops this problem. Again thank you.

I am finding it difficult to parse your question, you have an application that is starting at boot and you want to prevent it from starting, would that be correct ?

Are using Ubuntu with Unity interface ?

If so, search via the Dash for "Startup Applications"

To get all all applications that are started to be listed you might need to firstly run the command ..

```
cd /etc/xdg/autostart/ && sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop
```

---

