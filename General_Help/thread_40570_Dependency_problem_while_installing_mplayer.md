---
title: "Dependency problem while installing mplayer"
date: 2005-06-09
forum: General Help
---

### Post by kuang on 2005-06-09
Hi, all,

I try to follow the instruction of the unofficial starter guide for installing mplayer and realplayer, since I want my firefox with plug-in player.

However, I kept getting the following error message:

 mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

I check the related packages: libc6. My synaptic manager showed that it's the latest version, but it's not matched what these players require. What can I do for that? I don't understand this kind of problem.

Thank you very much.

kuang

---

### Post by bored2k on 2005-06-09
Use the right repositories from ubuntuguide.org

This is not the place to ask questions!

---

