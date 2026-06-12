---
title: "Dumb grub question"
date: 2018-03-17
forum: General Help
---

### Post by Hat-trick on 2018-03-17
I've been dual booting ubuntu and windows for 13 years now and I'm ready to just get rid of windows completely.  I was wondering if I did a clean install and wiped the drive would I still get the grub screen at boot? That's my dumb question.

Another option I was looking at was just wiping out all the windows partitions and just growing my /home.  Would this not be recommended?

---

### Post by mikewhatever on 2018-03-17
No, you shouldn't get the grub screen. There is a way to make it show, but it doesn't by default. 

It's hard to recommend or not recommend without knowing more details. If you feel comfortable with doing something like that, I don't see why not.

---

### Post by Hat-trick on 2018-03-17
```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048    534527    532480   260M Sony boot partition
/dev/sda2     534528   3553279   3018752   1.5G Windows recovery environment
/dev/sda3    3553280   4085759    532480   260M EFI System
/dev/sda4    4085760   4347903    262144   128M Microsoft reserved
/dev/sda5    4347904 466321422 461973519 220.3G Microsoft basic data
/dev/sda6  466323456 506320895  39997440  19.1G Microsoft basic data
/dev/sda7  506320896 512321535   6000640   2.9G Linux swap
/dev/sda8  512321536 976771071 464449536 221.5G Microsoft basic data
```

/dev/sda5 has windows on it.  I'd just delete that and grow my /home an additional 220 GB.

---

### Post by mikewhatever on 2018-03-17
It is not just delete - expand job. You may not be able to easily resize the home partition, if it isn't next to /dev/sda5. Also, once resized, the partition's UUID will change, and you'll need to adjust it in /etc/fstab.

---

### Post by Hat-trick on 2018-03-17
I see.  When I'm ready I'll start a new thread.  Thanks, man!

---

### Post by Yellow Pasque on 2018-03-17
It almost looks like your partitions (except for swap) are formatted with NTFS. So yeah, if you're ready to completely part with Windows, I'd do a wipe. I would also wait for Ubuntu 18.04 next month.

---

### Post by Hat-trick on 2018-03-17
No, SDA6 and SDA8 are EXT4, SDA1 and SDA3 are FAT

---

