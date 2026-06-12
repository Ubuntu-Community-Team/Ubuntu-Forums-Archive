---
title: "cannot get driver installed for webcam on toshiba L875 laptop"
date: 2017-12-02
forum: General Help
---

### Post by graigster on 2017-12-02
I using Gnome 3 ubuntu 16.04 Ive tried cheese skype VLC  and webcam works with windows 8.1 64 bit but cannot get it to wotk with ubuntu ..I tried 
```
GUVCVIEW:  GUVCVIEW: couldn't open /home/graigster/.config/guvcview2/video0 for read: No such file or directory
V4L2_CORE: ERROR opening V4L interface: No such file or directory
Gtk-Message: GtkDialog mapped without a transient parent.
``` 
This is discouraged.  Ive tried

```
lsmod | grep videodev videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
```
 can anybody please help me resolve  my webcam problem  I just dont know what else to try to fix the problem  ....I wished this model had a F-key for turning on/off but it dont it uses windows app to turn/on/off  any help would be greatly appreciated thanks everybody Graigster

---

### Post by Perfect Storm on 2017-12-02
Thread moved, font set to standard and added code tags.

---

