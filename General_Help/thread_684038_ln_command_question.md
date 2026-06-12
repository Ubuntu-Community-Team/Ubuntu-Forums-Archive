---
title: "ln command question"
date: 2008-01-31
forum: General Help
---

### Post by zoomiest on 2008-01-31
Just enjoying the benefits of a new Xubuntu 7.10 install, and setting it up for my wife...

symbolic link command is giving me grief... I am new at this but... this has worked before.

if I am typing ```
 ln -s /home/laura/smb4k/FILES/Group/Library/iRadio My_Music
```

...to get a shortcut to our family file server, mounted with smb4k... 

Why would I get "ln: target `My_Music' is not a directory"  ?

Is it not mounted correctly? Please shed some light on this.

---

### Post by jan quark on 2008-01-31
to display all partitions mounted or not type this into the terminal and please post the result here thx

```
sudo fdisk -l
```

---

### Post by ~LoKe on 2008-01-31
Where is "My_Music"?

---

### Post by zoomiest on 2008-01-31
sudo fdisk -l bring us:

```
 Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa631a631

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9375    75304656   83  Linux
/dev/hda2            9376        9729     2843505    5  Extended
/dev/hda5            9376        9729     2843473+  82  Linux swap / Solaris
   
```

Answering The second question by ~Loke:

My_Music would be the shortcut name. The music directory is on a pc server a few feet away. Its a Windows XP box (conversion to Linux coming up) used exclusively to serve files.

(does the second term - that I am using My_Music for - HAVE to be a directory? (can't it be the more-user-friendly link name?)

---

### Post by ~LoKe on 2008-01-31
My_Music has to be an existing directory, and it'll look in there for the contents of iRadio.

For example, I have /var/lib/mpd/music look for my music in ~/Music
sudo ln -s ~/Music /var/lib/mpd/music

---

### Post by dominik_ap on 2008-05-10
> **~LoKe said:**
> My_Music has to be an existing directory, and it'll look in there for the contents of iRadio.

For example, I have /var/lib/mpd/music look for my music in ~/Music
sudo ln -s ~/Music /var/lib/mpd/music

I don't know if you have already solved this, but I had similar problem.
I wanted to list content of few directories in new one. So i got resolutino here: [http://ubuntuforums.org/showthread.php?t=788425](http://ubuntuforums.org/showthread.php?t=788425)

I hope it will help

have a nice day

---

