---
title: "Virtual CD-ROM"
date: 2008-03-04
forum: General Help
---

### Post by Halfbrazilian on 2008-03-04
Is there CD-ROM Virtualization in Ubuntu? I know about the whole "mount -o loop -t iso9660 -r image.iso /mountpoint" command but that is not what I want. If I mount it that way the system treats it as a directory. I want the system to treat it as a CD so programs will think it is a CD.

---

### Post by kpkeerthi on 2008-03-04
Try [cdemu]("http://cdemu.sourceforge.net/")

**Debs:**
[http://kabelkaos.net/cdemu/](http://kabelkaos.net/cdemu/)

**Compile from source:**
[http://ubuntuforums.org/showthread.php?t=69530](http://ubuntuforums.org/showthread.php?t=69530)

---

### Post by chewearn on 2008-03-04
I'm not 100% positive if this is true or not.

But when I mount an iso file directly on my cd-rom mount point (superceding the cd-rom drive hardware), and the system seems to think there is a real cd in the cd-rom drive.

```
sudo mount -o loop -t iso9660 <file.iso> /media/cdrom
```

---

### Post by Halfbrazilian on 2008-03-05
Thanks. I'll try them out.

---

