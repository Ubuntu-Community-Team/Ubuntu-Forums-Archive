---
title: "Create Disk Images?"
date: 2005-05-02
forum: General Help
---

### Post by bluetang on 2005-05-02
I've been using Norton Ghost for years to create images of my Windows partitions and use the same images to restore. I'd like to discontinue this use of Ghost. Is there an open source application that would do the same trick in Windows and Linux partitions?

---

### Post by Xerampelinae on 2005-05-02
probably 'dd'

man dd

basically, just give an infile and an outfile such as
```

dd if=/dev/cdrom of=/home/bren/cd_image.iso

```

I haven't really used ghost, so I'm not sure if its the same, but it sounds like it.

---

### Post by Xerampelinae on 2005-05-02
Oh yeah, and of course partitions look something like /dev/hda2, so you would use that as an infile to make an image of a hdd partition.

---

### Post by bonifacio on 2005-05-02
Follow up question.  How do you restore it then?

---

