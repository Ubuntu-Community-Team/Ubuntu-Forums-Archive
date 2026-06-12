---
title: "GParted &amp; Resizing"
date: 2006-12-24
forum: General Help
---

### Post by Dubbayoo on 2006-12-24
Is Gparted reliable for resizing partitions? I have a large storage partition I want to resize to add additional swap but I don't want to risk losing it.

---

### Post by bodhi.zazen on 2006-12-24
> **Dubbayoo said:**
> Is Gparted reliable for resizing partitions? I have a large storage partition I want to resize to add additional swap but I don't want to risk losing it.

Problems are infrequent, but resizing has some risk.

Obviously almost everyone would advise you back up your partition before you resize....

[http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7](http://ubuntuforums.org/showpost.php?&p=1628330&postcount=7)

---

### Post by petok on 2006-12-24
According to my experience, it depends on what filesystem you are using. I never had problems with ext3 and fat32, but it seems ntfs always gets corrupted...maybe I should have defragmentated that ntfs partition first. Can you give some more info?

---

### Post by bodhi.zazen on 2006-12-24
> **petok said:**
> ...maybe I should have defragmentated that ntfs partition first. 

Errr .... yes, always defragment fat and ntfs before resizing.

---

### Post by Dubbayoo on 2006-12-24
It's a 250GB disk formatted as one big ext3 partition. I would like to shrink it by 1GB and add more swap.

---

### Post by bodhi.zazen on 2006-12-24
You should be fine.

If you are paranoid, add a swap file (rather then a partition)

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by Dubbayoo on 2006-12-24
> **bodhi.zazen said:**
> You should be fine.

If you are paranoid, add a swap file (rather then a partition)

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

Great idea. Thank you.

---

