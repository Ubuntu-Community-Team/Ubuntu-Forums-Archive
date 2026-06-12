---
title: "Download Streaming Media"
date: 2005-06-11
forum: General Help
---

### Post by wirjo on 2005-06-11
I want to download streaming media.
Is there any download managers in Linux that can allow this?

---

### Post by kvidell on 2005-06-11
[QUOTE=wirjo]I want to download streaming media.
Is there any download managers in Linux that can allow this?[/QUOTE]
 if you mean like an MP3 radio stream ripper then try kstreamripper :)
> 63/kvidell: apt-cache show kstreamripper
Package: kstreamripper
Priority: optional
Section: universe/sound
Installed-Size: 200
Maintainer: Michael Ablassmeier <abi@grinser.de>
Architecture: i386
Version: 0.2-1
Depends: kdelibs4 (>= 4:3.2.3), libart-2.0-2 (>= 2.3.16), libc6 (>= 2.3.2.ds1-4), libfam0c102, libgcc1 (>= 1:3.3.4-1), libice6 | xlibs (>> 4.1.0), libpng12-0 (>= 1.2.5.0-4), libqt3c102-mt (>= 3:3.2.3-3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxext6 | xlibs (>> 4.1.0), libxrender1, zlib1g (>= 1:1.2.1), streamripper
Filename: pool/universe/k/kstreamripper/kstreamripper_0.2-1_i386.deb
Size: 30778
MD5sum: b2965cbbe3e85c5e13175643d19419bf
Description: kde frontend for streamripper
 KStreamRipper is a small frontend for the streamripper command
 line utility. Streamripper captures internet shoutcast radio streams
 on your harddisk and splits them up in mp3 files. KStreamRipper helps
 you with managing/ripping your preferred streams.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by wirjo on 2005-06-11
I mean, something that can download .rm files from rtsp:// and etc. Flashget in Windows has the feature.

---

### Post by kvidell on 2005-06-11
[QUOTE=wirjo]I mean, something that can download .rm files from rtsp:// and etc. Flashget in Windows has the feature.[/QUOTE]
 Given these a shot?> 64/kvidell: apt-cache search download | grep -i manager
d4x - graphical download manager
jigdo - GTK+ download manager
kget - KDE Download ManagerUpon further investigation, some of them seem like likely candidates. (further investigation meaning apt-cache show [package name])
- Kev

---

### Post by wirjo on 2005-06-11
I tried D4X but it doesn't work.

---

### Post by Zerocool10482 on 2006-01-24
I want another program like kstreamripper. Because that program didn't work. I just want something that will work. And not cut songs. Is there other programs like this that will not cut songs.

---

### Post by Thulemanden on 2006-01-29
[quote=wirjo]I want to download streaming media.
Is there any download managers in Linux that can allow this?[/quote]

So you simply want to capture streaming media?

Video or sound?

---

### Post by timseal on 2006-02-10
Try mplayer with the -dumpstream option, like this:

[FONT="Courier New"]mplayer -dumpstream -playlist *url* -dumpfile whatever_filename_you_want.mpg
[/FONT]
replace *url* with the url of the stream.  They tend to be single entry playlists, like a pointer to the real media file.

---

