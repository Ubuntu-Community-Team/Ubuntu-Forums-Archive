---
title: "creating a CD image fails"
date: 2013-01-26
forum: General Help
---

### Post by xaverius2 on 2013-01-26
Hi there,

I just like to create an image of an audio CD under Xubuntu, but dd fails:

```
$ dd if=/dev/cdrom of=test.iso
dd: Lesen von /dev/cdrom: Eingabe-/Ausgabefehler
0+0 Datensätze ein
0+0 Datensätze aus
0 Bytes (0 B) kopiert, 0,0206619 s, 0,0 kB/s

```The same with ```
if=/dev/sr0
``` And it doesn't matter whether the cdrom is mounted or not, and sudo doesn't work either. I can listen to the CD if it is mounted, and the folders /dev/cdrom and /dev/sr0 do exist:

```
$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 3 Jan 27 00:27 /dev/cdrom -> sr0
$ ls -l /dev/sr0
brw-rw----+ 1 root cdrom 11, 0 Jan 27 00:27 /dev/sr0

```So what is wrong? Thank you in advance!

---

### Post by claracc on 2013-01-27
I think the problem can be you don't specify where to do the iso file, i.e. /tmp/test.iso or you have the cd mounted and you have to unmount.

Here, [http://www.cyberciti.biz/tips/linux-creating-cd-rom-iso-image.html](http://www.cyberciti.biz/tips/linux-creating-cd-rom-iso-image.html), there is a simple howto do the task.

Anyway, you could use too some apps to make iso images as k3b or brasero.

---

### Post by xaverius2 on 2013-01-27
Well, I could figure out the root cause of the problem: It is not possible to create ISO images of audio CDs in general, see

[http://en.wikipedia.org/wiki/ISO_image#Limitations](http://en.wikipedia.org/wiki/ISO_image#Limitations)

---

### Post by Merrattic on 2013-01-27
Try
```
cdrdao read-cd foo.cue
```

---

