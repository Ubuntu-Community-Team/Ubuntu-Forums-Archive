---
title: "Windows not in Grub's menu?"
date: 2007-05-02
forum: General Help
---

### Post by Vinze on 2007-05-02
Hello, yesterday I installed Xubuntu on my brother's PC, on a new hard drive. During installation, it detected that new hard drive as hda and detected a 4GB device as sda.

Now I have no idea what hard drive his Windows is on, and it is not listed in Grub's menu... How can I get it back?

Thanks a lot.

**Never mind, I've found the cause... :( **

---

### Post by Sef on 2007-05-02
How did you do the partition during the install?

---

### Post by Vinze on 2007-05-02
> **Sef said:**
> How did you do the partition during the install?

Never mind, apparently his old hard disk was removed and all data copied over to his new one, which I emptied to make room for Xubuntu. MERDE! And of course it now is all my fault :(

---

### Post by strabes on 2007-05-02
Can you post the output of this command: ```
sudo fdisk -l
```

---

### Post by Vinze on 2007-05-02
> **strabes said:**
> Can you post the output of this command: ```
sudo fdisk -l
```

Never mind, the hard disk is just not present.

---

