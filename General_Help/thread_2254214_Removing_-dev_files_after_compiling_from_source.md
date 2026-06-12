---
title: "Removing -dev files after compiling from source"
date: 2014-11-25
forum: General Help
---

### Post by monkeybrain20122 on 2014-11-25
Hi,

This is kind of a basic question. I think the -dev files are needed only to compile software from source. So can I remove them after compilation?

Reason: I need libvtk5-dev to compile something, but it is in conflict with the ffmpeg -dev files I installed from a ppa(it wants livavcodecs-dev etc, those that I have installed have slightly different names like libavcodecs-ffmpeg-dev) I need the ffmpeg files because I use them for compiling media mplayers, but I need libvtk5-dev just for a one time compilation since this application doesn't update very often. So I am wondering if I can install libvtk5-dev, which will uninstall the ffmpeg-dev files, compile the software, then remove libvtk5-dev and reinstall the ffmpeg-dev files.  I have tried to install libvtk from source but keep getting build errors, I figure this would be easier if it works.

---

### Post by mc4man on 2014-11-25
You can  remove -dev packages anytime you want. 
(- if using synaptic usually best to remove, reload, install, ect. 
In recent  times synaptic seems to  need  reloading more than in past years

---

