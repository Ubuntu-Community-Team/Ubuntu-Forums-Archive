---
title: "+[windows] File permission"
date: 2013-06-10
forum: General Help
---

### Post by tigerjack89 on 2013-06-10
Hey guys :)
Today a strange thing happen. I have a .ods file on my NTFS partition; the file is created with Windows, but I opened and modified the file also with Ubuntu.
Today, when I tried to opened the file via Windows, it returns an advertisement, something like
"You can't modify the file because it begins to tigerjack89". So, how can be possible? is it Windows capable of recognize permissions? and does Ubuntu change permissions when I modify a file?

Thanks in advance :)

---

### Post by dino99 on 2013-06-10
each file on linux have rights set; so you need windows to accept such rights

---

### Post by tigerjack89 on 2013-06-10
> **dino99 said:**
> each file on linux have rights set; so you need windows to accept such rights
How? So windows can read linux rights set?

---

### Post by Impavidus on 2013-06-10
NTFS partitions don't know about Linux permissions, so files stored on shared NTFS partitions don't have Linux permissions when accessed from Windows. In Linux they only have the permissions set for the entire partition. Was the file password protected? I don't even know whether that's possible for ods.

---

### Post by tigerjack89 on 2013-06-10
> **Impavidus said:**
> NTFS partitions don't know about Linux permissions, so files stored on shared NTFS partitions don't have Linux permissions when accessed from Windows. In Linux they only have the permissions set for the entire partition. Was the file password protected? I don't even know whether that's possible for ods.
It's just what I have ever known about files, permissions and partitions and it's the first time I have this problem. And no, the file isn't protected at all. Well, maybe it's just a windows bug?

---

