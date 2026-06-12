---
title: "Isn't 'gtk-3.0' - a newer version of gtk2 ??"
date: 2015-10-19
forum: General Help
---

### Post by simba4 on 2015-10-19
Trying to install 'Subtitle Editor'.  The instruction says to start with the './configure' command.

Doing so, I got a long list of 'checkups'.
Among others, It complained that 'intltool' was missing. Ok, I installed it.

Then, repeating that './configure' command, now it says it wants (gtkmm-3.0 >= 3.0)..

   Hmm..

It seem that I have already gtk2 installed. Here is a 'short' list of how it looks like...
```

J:~/Downloads/Install/subtitleeditor-0.52.1$ dpkg -s gtk
gtk2.0-examples                    gtkfalse
gtk2-engines                       gtk-gnutella
gtk2-engines-aurora                gtkguitune
gtk2-engines-blueheart             gtkhash
gtk2-engines-cleanice              gtkhash-common
gtk2-engines-equinox               gtk-im-libthai
gtk2-engines-magicchicken          gtklick
gtk2-engines-moblin                gtklp
gtk2-engines-murrine               gtkmm-documentation
gtk2-engines-nodoka                gtkmorph
gtk2-engines-oxygen                gtkmorph-example
gtk2-engines-pixbuf                gtkorphan
gtk2-engines-qtcurve               gtkperf
gtk2-engines-wonderland            gtkpod
gtk2-engines-xfce                  gtkpod-data
gtk2-ex-formfactory-perl           gtkpod-dbg
gtk2hs-buildtools                  gtkpool
gtk3-engines-oxygen                gtk-recordmydesktop
gtk3-engines-unico                 gtk-redshift
gtk3-engines-xfce                  gtkrsync
gtk-3-examples                     gtk-sharp2
gtk3-im-libthai                    gtk-sharp2-examples
gtkam                              gtk-sharp2-gapi
gtkam-dbg                          gtk-sharp3
gtkam-gimp                         gtk-sharp3-examples
gtkaml                             gtk-sharp3-gapi
gtkaml-dbg                         gtkterm
gtkatlantic                        gtk-theme-config
gtkballs                           gtk-theme-switch
gtkboard                           gtktrain
gtk-chtheme                        gtk-vector-screenshot
gtk-clearlooks-gperfection2-theme  gtkvncviewer
gtkcookie                          gtkwave
gtk-doc-tools  
 



```Now I am hesitating.

Isn't that requires 'gtk-3.0' - a newer version of gtk2?
Am I duplicating instead of upgrading or maybe - I have to Remove gtk2 and install gtk3.0 instead ??

I would appreciate some help on this matter.


Thank you, 

James

---

### Post by buzzingrobot on 2015-10-19
> **simba4 said:**
> Trying to install 'Subtitle Editor...
Isn't that requires 'gtk-3.0' - a newer version of gtk2?


gtk2 and gtk3 are two separate toolkits.  gtk3 is not a point release of gtk2.

BTW, there's a "Subtitle Editor" in the repos.

---

### Post by vasa1 on 2015-10-19
> **buzzingrobot said:**
> ...
BTW, there's a "Subtitle Editor" in the repos.
OP, where are you trying to install Subtitle Editor from? Are you following instructions from some tech site or blog?

```
05:25 PM ~ $ apt-cache show subtitleeditor
Package: subtitleeditor
Priority: optional
Section: universe/x11
Installed-Size: 1780
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Philip Rinn <rinni@inventati.org>
Architecture: amd64
Version: 0.41.0-2ubuntu1
Depends: libatkmm-1.6-1 (>= 2.22.1), libc6 (>= 2.2.5), libcairomm-1.0-1 (>= 1.6.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.36.2), libgstreamer-plugins-base0.10-0 (>= 0.10.12), libgstreamer0.10-0 (>= 0.10.9), libgstreamermm-0.10-2 (>= 0.10.11), libgtk2.0-0 (>= 2.24.0), libgtkmm-2.4-1c2a (>= 1:2.24.0), libpangomm-1.4-1 (>= 2.27.1), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.6), libsubtitleeditor0 (= 0.41.0-2ubuntu1), gstreamer0.10-x, libenchant1c2a, gstreamer0.10-plugins-good, gstreamer0.10-plugins-base
Suggests: gstreamer0.10-ffmpeg
Filename: pool/universe/s/subtitleeditor/subtitleeditor_0.41.0-2ubuntu1_amd64.deb
Size: 292686
MD5sum: 2f2f4e1d286a4c876ef33379bc73840b
SHA1: 938a3767aac51ee2a8c18d3ef781930dd10d4f96
SHA256: 097d901d8129d26044ec314d8164b937a708bbd7d831e54b972c64b8913df551
Description-en: Graphical subtitle editor with sound waves representation
 Subtitle Editor is a GTK+2 tool to edit subtitles.  It can be used for new
 subtitles or as a tool to transform, edit, correct and refine existing
 subtitles.
 .
 This program also shows sound waves, which makes it easier to synchronise
 subtitles to voices.
 .
 This package has these features
 .
  o Multiple document interface.
  o Internationalization support.
  o Video player integrated in the main window (based on GStreamer).
  o Can play preview with external video player (using MPlayer or other).
  o Style Editor.
  o Move subtitle.
  o Scale.
  o Split and joint subtitle.
  o Edit text and adjust time (start, end).
  o Generate Waveform from Video.
 .
 Supported formats:
 .
  o Sub Station Alpha.
  o Advanced Sub Station Alpha.
  o SubRip.
  o MicroDVD.
  o MPL2.
  o MPsub (MPlayer subtitle).
  o SubViewer 2.0.
  o Plain-Text.
  o Adobe Encore DVD.
Description-md5: d7caacfd869f7a5f15e079d796123aee
Homepage: http://home.gna.org/subtitleeditor/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video

```
Compiling software from source as you seem to want to do requires quite a bit of experience. I guess you're going that route to get the latest version?

---

### Post by simba4 on 2015-10-19
Yes.  The version on the Ubuntu Software Center is 0.41.0.  the description: Subtitle Editor is a GTK+2 tool to edit  subtitles.  It can be used for  new subtitles or as a tool to transform, edit, correct and refine  existing subtitles.

On the other hand, on _[[COLOR=#0000ff]this site[/COLOR]]("http://home.gna.org/subtitleeditor/")_ is states that the newest version is 0.52.1 and the description: Subtitle Editor is a **GTK+3** tool to edit subtitles for GNU/Linux/*BSD.                  It can be used for new subtitles or as a tool to transform, edit, correct and refine existing subtitle.                 This program also shows sound waves, which makes it easier to synchronise subtitles to voices.


Well, You can see now why I thought that GTK3 is a newer version of GTK2.


Hmm, I am still puzzled.


James

---

### Post by steeldriver on 2015-10-19
GTK3 is in a sense a newer version of GTK, but the API (function calls etc.) is different i.e. the two toolkits are not interchangeable 

In other words, the maintainers of Subtitle Editor would have substantially re-written their code to take advantage of the new toolkit

See [https://developer.gnome.org/gtk3/stable/gtk-migrating-2-to-3.html](https://developer.gnome.org/gtk3/stable/gtk-migrating-2-to-3.html)

---

### Post by mc4man on 2015-10-19
You may still have issues building the newer version on trusty as the new version uses both gtk-3 & gstreamer 1.0
If so the issue could be with libgstreamermm-1.0-0 in 14.04

In any event 15.10 & 16.04 will have the current version of subtitleeditor

---

### Post by simba4 on 2015-10-19
> "..In any event 15.10 & 16.04 will have the current version of subtitleeditor.."

I am not sure what does it means.
Maybe the Ubuntu version. Mine is 14.04 and I don't really know how to upgrade it.

Well, Thanks for all the answers.
I still not sure how to tackle all that, but thanks anyway.

Now I'm too tired to handle it. Tomorrow is another day.

James
[IMG]http://www.livepencil.com/mambers/english/youremails/2004/sleepy/yawn.gif[/IMG]

---

### Post by buzzingrobot on 2015-10-19
15.10 is the next, non-LTS, Ubuntu release, due out in a few days.  16.04 will be the next release after that, in 6 months, and it will be an LTS release. 

If you are not otherwise committed to running an LTS like 14.04, you could spend the time before 15.10 is released checking out how to do an upgrade, backing up files, etc., and then do the upgrade to 15.10. I've been using it in pre-release and it looks to be solid.

You have run into the issue of dependencies with your attempt to build from source:  Building the version of Subtitle Editor you want on 14.04 requires other, newer, packages that, in all likelihood, are not compatible with 14.04.

As mc4mn said, the version in 15.10 will be 52.1:  [URL="http://packages.ubuntu.com/wily/subtitleeditor"]http://packages.ubuntu.com/wily/subtitleeditor
[/URL]

---

