---
title: "how can i change filesystem?"
date: 2007-08-02
forum: General Help
---

### Post by kukulcanmaya on 2007-08-02
hey guys, wubi is wonderful isnt it. Just wondering if it possible to change to an other filesystem instead of default ext3 when i start to install a new system? (sorry about my english, if i didnt make it clear.
thanks

---

### Post by ago on 2007-08-02
In 7.10, not now

---

### Post by kukulcanmaya on 2007-08-02
thank you, Ago

---

### Post by tuxcantfly on 2007-08-02
> hey guys, wubi is wonderful isnt it. Just wondering if it possible to change to an other filesystem instead of default ext3 when i start to install a new system? (sorry about my english, if i didnt make it clear.
thanks

Follow the same instructions as those at [https://wiki.ubuntu.com/WubiGuide#head-9ccff9cbed2c966e21b9e8437b60633782234436](https://wiki.ubuntu.com/WubiGuide#head-9ccff9cbed2c966e21b9e8437b60633782234436) and instead of doing mkfs.ext3, use mkfs.reiserfs. Also remember to edit the /etc/fstab file to replace every occurrence of ext3 with reiserfs. Same process should also work on jfs and xfs, since support is built into the Lupin initrd for those filesystems, but I've only tested it with reiserfs.

---

### Post by kukulcanmaya on 2007-08-02
thank you, Tuxcantfly, that's pretty helpful. i am trying it now with JFS. lol

---

