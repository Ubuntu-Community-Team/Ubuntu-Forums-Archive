---
title: "How To Use gparted Values in ddrescue?"
date: 2015-03-22
forum: General Help
---

### Post by johny why on 2015-03-22
hi

i'm attempting to recover a single partition on a hard disk drive with ddrescue. 

gparted says this about the partition:

[img]http://s2.postimg.org/fx6ct8255/gparted2.png[/img]

can i use the "First Sector" value as-is for the gnu ddrescue -i option? Or do i need to divide by 8 or 512 or something?

Fyi, ddrescue documentation is here: [https://www.gnu.org/software/ddrescue/](https://www.gnu.org/software/ddrescue/)

thx!

also asked here:
[http://gparted-forum.surf4.info/viewtopic.php?pid=33145](http://gparted-forum.surf4.info/viewtopic.php?pid=33145)

---

### Post by matt_symes on 2015-03-23
Hi

Can't you do something like

```
sudo ddrescue /dev/sda4 /path/to/image.img
```

Where path/to/image.img may be on an external hard drive or some such and is a file.

You can then try mounting the image file and/or using other data recovery tools on it.

Kind regards

---

### Post by johny why on 2015-03-23
I COULD do that. 

But I am asking how to do THIS.

---

### Post by johny why on 2015-03-23
plz see continuation of this discussion over here:

[http://ubuntuforums.org/showthread.php?t=2270340](http://ubuntuforums.org/showthread.php?t=2270340)

thx

---

