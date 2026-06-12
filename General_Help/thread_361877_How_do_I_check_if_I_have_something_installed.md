---
title: "How do I check if I have something installed?"
date: 2007-02-14
forum: General Help
---

### Post by BostonBrother on 2007-02-14
I was wondering if there is some way to check to see if I have something installed and if I do what version I am running?

---

### Post by yabbadabbadont on 2007-02-14
sudo aptitude search "pattern"

then

sudo aptitude show packagename

for the details including version and dependencies and such.

Example:
```
/root # aptitude search libxine
p   libxine-dev                                            - the xine video player library, development packages             
i   libxine-extracodecs                                    - the xine video/media player library, binary files               
i   libxine-main1                                          - the xine video/media player library, binary files               
p   libxine1c2                                             - the xine video/media player library, transitional package       
i   libxinerama-dev                                        - X11 Xinerama extension library (development headers)            
i   libxinerama1                                           - X11 Xinerama extension library                                  
p   libxinerama1-dbg                                       - X11 Xinerama extension library (debug package)                  
/root # aptitude show libxine-extracodecs 
Package: libxine-extracodecs
New: yes
State: installed
Automatically installed: no
Version: 1.1.1+ubuntu1-2
Priority: optional
Section: multiverse/libs
Maintainer: Siggi Langauf <siggi@debian.org>
Uncompressed Size: 3047k
Depends: libc6 (>= 2.3.4-1), libmad0 (>= 0.15.1b), zlib1g (>= 1:1.2.1), libxine-main1
Conflicts: sinek (< 0.7), xine-ui (< 0.9.10), libxine1c2 (< 1.1.1+ubuntu1)
Replaces: xine-dvdnav, libxine1c2 (< 1.1.1+ubuntu1), libxine-main1 (< 1.1.1+ubuntu2)
Description: the xine video/media player library, binary files
 This is the xine media player library (libxine). Libxine provides the complete infrastructure for a video/media player. It
 supports MPEG 1/2 and some AVI and Quicktime videos out of the box, so you can use it to play DVDs, (S)VCDs and most video
 files out there. It supports network streams, subtitles and even mp3 or ogg files. It's extensible to your heart's content
 via plugins for audio_out, video_out, input media, demuxers (stream types), audio/video and subtitle codecs. Building a GUI
 (or text based) frontend around this should be quite easy. The xine-ui package provides one for your convenience, so you can
 just start watching your VCDs ;-)

```

---

### Post by highneko on 2007-02-14
dpkg -l *package* #also works

---

### Post by K2712 on 2007-02-14
Open up a terminal and do:

```
apt-cache showpkg "name of package here"
```
                                                        (without quotes)

It will list the installed version, reverse dependencies, and dependencies.

---

### Post by dcstar on 2007-02-14
> **BostonBrother said:**
> I was wondering if there is some way to check to see if I have something installed and if I do what version I am running?

If you use the Gnome desktop, open up the Synaptic package manager and you will have a list of all of your installed packages - and their versions - available to you.

You can even select an individual package and see what versions of it are available in your listed repositories.

---

### Post by yabbadabbadont on 2007-02-14
That's one of the things I love about Linux, there are 60 different ways to do almost everything.  :D :lol:

---

### Post by DirtDawg on 2007-02-15
> **yabbadabbadont said:**
> That's one of the things I love about Linux, there are 60 different ways to do almost everything.  :D :lol:

No kidding! I was going to say, I usually use:
```
 aptitude search <whatever package name>
```
Then look for an 'i' to the left.

---

### Post by ardchoille42 on 2007-02-15
apt-cache policy appname

---

### Post by yabbadabbadont on 2007-02-15
Edit /var/lib/dpkg/status and search for the package.

(Ok, this is just getting silly...  :lol:)

---

