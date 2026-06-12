---
title: "How to Stop ImageMagick from opening pdf's"
date: 2022-03-07
forum: General Help
---

### Post by BlueAZ on 2022-03-07
Hi,  I'm running Ubuntu 20.04 with Unity desktop on a 64-bit rig.  At some point, I installed ImageMagick from Ubuntu Software, thinking it might be a good replacement for Image Viewer.  I didn't like it, so I uninstalled it.  But some elements of the program remain apparently.  Now whenever I try to open a pdf file, ImageMagick tries (and fails) to open it.  I just want Document Viewer to open it.  I've tried changing the default program in Properties, but it won't change.
I've also searched for answers online and have found too many disparate solutions in the Terminal to want to try.  My Terminal use is limited to autoremove, autoclean and upgrade, so I need very clear specific instructions, please.
Thanks!!

---

### Post by #&amp;thj^% on 2022-03-07
show us this:
```
cat ~/.config/mimeapps.list
```

---

### Post by BlueAZ on 2022-03-07
> **1fallen said:**
> show us this:
```
cat ~/.config/mimeapps.list
```

A lot showed up but I think this is the pertinent section:  image/avs=display-im6.q16.desktop;
image/bie=display-im6.q16.desktop;
image/x-ms-bmp=display-im6.q16.desktop;
image/cmyk=display-im6.q16.desktop;
image/dcx=display-im6.q16.desktop;
image/eps=display-im6.q16.desktop;
image/fax=display-im6.q16.desktop;
image/fits=display-im6.q16.desktop;
image/gif=display-im6.q16.desktop;org.gnome.eog.desktop;
image/gray=display-im6.q16.desktop;
image/pjpeg=display-im6.q16.desktop;org.gnome.eog.desktop;
image/miff=display-im6.q16.desktop;
image/mono=display-im6.q16.desktop;
image/mtv=display-im6.q16.desktop;
image/x-portable-bitmap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/pcd=display-im6.q16.desktop;
image/pcx=display-im6.q16.desktop;
image/pdf=display-im6.q16.desktop;
image/x-portable-graymap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/pict=display-im6.q16.desktop;
image/x-portable-anymap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/x-portable-pixmap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/ps=display-im6.q16.desktop;
image/rad=display-im6.q16.desktop;
image/x-rgb=display-im6.q16.desktop;
image/rgba=display-im6.q16.desktop;
image/rla=display-im6.q16.desktop;
image/rle=display-im6.q16.desktop;
image/sgi=display-im6.q16.desktop;
image/sun-raster=display-im6.q16.desktop;
image/targa=display-im6.q16.desktop;
image/tiff=display-im6.q16.desktop;org.gnome.eog.desktop;
image/uyvy=display-im6.q16.desktop;
image/vid=display-im6.q16.desktop;
image/viff=display-im6.q16.desktop;
image/x-xbitmap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/x-xpixmap=display-im6.q16.desktop;org.gnome.eog.desktop;
image/x-xwindowdump=display-im6.q16.desktop;
image/x-icon=display-im6.q16.desktop;
image/yuv=display-im6.q16.desktop;

---

### Post by #&amp;thj^% on 2022-03-07
Change 
set **image/pdf to evince.desktop** or your preferred viewer.
Or right click on a PDF select properties, General, Open With. See Screenshot

---

### Post by BlueAZ on 2022-03-07
As noted, the Properties method will not work -- tried it multiple times, it simply stays as is.
Just tried to change it in the Terminal read-out, but I can't delete or replace anything there.  Please clarify how to "Change" or "set" this in Terminal.

---

### Post by #&amp;thj^% on 2022-03-07
```
nano ~/.config/mimeapps.list

```
Look for
```
[Added Associations]
text/x-matlab=xed.desktop;
application/ecmascript=xed.desktop;
application/mathematica=xed.desktop;
application/mbox=xed.desktop;
text/plain=xed.desktop;
application/json=sublime-text2.desktop;
**[U][COLOR="#FF0000"]application/pdf=f[/COLOR][/U}**oxitreader.desktop; ### Change to your preferred Reader


```
save and exit.

---

### Post by BlueAZ on 2022-03-07
OK, I had to remember to use the arrow keys to navigate text in T ;~]   I have managed to erase img6.  What is the term for Document Viewer?  And how do you save changes in T?

---

### Post by #&amp;thj^% on 2022-03-07
> **BlueAZ said:**
> OK, I had to remember to use the arrow keys to navigate text in T ;~]   I have managed to erase img6.  What is the term for Document Viewer?  And how do you save changes in T?

Named: (evince.desktop)
To save use [Ctrl + o} to write and {Ctrl + x} Saves

---

### Post by BlueAZ on 2022-03-07
Yay!  It worked!!!  Just hope I didn't screw up anything else :o   Thanks so much!

---

### Post by #&amp;thj^% on 2022-03-07
Your Welcome, Yes I noticed ImageMagick kind of took a strangle hold of a few things

---

### Post by BlueAZ on 2022-03-07
Right, there are still a lot of other things associated with it.  Any suggestions?
Thanks again!

---

### Post by #&amp;thj^% on 2022-03-07
I'm on Arch right now I'll remember to give a default list here (in this post), stay tuned. :)
Sorry for the delay, here is mine on Mate
```
 ~/.config/mimeapps.list
[Default Applications]
video/mp4=audacious.desktop
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
text/html=firefox.desktop
x-scheme-handler/about=firefox.desktop
inode/directory=caja-folder-handler.desktop
text/plain=pluma.desktop
audio/mpeg=audacious.desktop
audio/x-mpegurl=audacious.desktop
audio/x-scpls=audacious.desktop
audio/x-vorbis+ogg=audacious.desktop
audio/x-wav=audacious.desktop
video/mpeg=audacious.desktop
video/mp2t=audacious.desktop
video/msvideo=audacious.desktop
video/quicktime=audacious.desktop
video/webm=audacious.desktop
video/x-avi=audacious.desktop
video/x-flv=audacious.desktop
video/x-matroska=audacious.desktop
video/x-mpeg=audacious.desktop
video/x-ogm+ogg=audacious.desktop
image/bmp=eom.desktop
image/gif=eom.desktop
image/jpeg=eom.desktop
image/png=eom.desktop
image/tiff=eom.desktop
application/pdf=atril.desktop

[Added Associations]
video/mp4=mpv.desktop;

```
Edit them the same way with nano different names of course.

---

