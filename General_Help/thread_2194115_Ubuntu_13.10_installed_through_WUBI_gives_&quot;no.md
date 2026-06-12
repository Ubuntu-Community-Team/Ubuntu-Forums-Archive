---
title: "Ubuntu 13.10 installed through WUBI gives &quot;no wubildr&quot; during boot"
date: 2013-12-16
forum: General Help
---

### Post by kgandhiok on 2013-12-16
Hi,

I'm aware that WUBI is no longer supported for Ubuntu installations, however I somehow managed to get Ubuntu 13.10 64bit installed on dual boot alongside Windows 7 through WUBI. Ubuntu works perfectly fine, no errors at all. On boot I see this message "No Wubildr" for about half a second, so I'm just curious as to what this means and if I should be concerned about it.

From what I understand it means that wubi doesn't have a directory created for itself on the system... I don't know if I'm wrong or right... Any suggestions / tips would be appreciated.

Thanks!

---

### Post by hakuna_matata on 2013-12-16
The file wubildr.mbr is searching for the file wubildr. If wubildr.mbr finds an unsupported file system earlier than wubildr it fails.

---

### Post by kgandhiok on 2013-12-16
Oh, so what should I do so that wubildr.mbr can get the wubildr file? How come Ubuntu works fine on my system even though I get this error message each time at boot?

---

### Post by hakuna_matata on 2013-12-16
Is your installation on first hard disk of your system? Is it on first partition ? Maybe you can disconnect external devices you don't need.

---

### Post by kgandhiok on 2013-12-16
My installation is on the same hard disk that has windows 7, I have a windows laptop, but I've done a dual boot of 13.10 on the same hard disk using wubi. I'm sorry I don't understand what you mean by first hard disk or first partition. I did not partition my drive manually for Ubuntu, because wubi did that when I did the installation.

---

### Post by hakuna_matata on 2013-12-16
Windows assigns partitions letters like c: d: e: f: but some partitions e.g. for recovery are hidden.

I'm reading your first post again. If it works the message "no wubildr found" is OK.
> Try (hd0,0): NTFS5: no wubildr found
Try (hd0,1): NTFS5:

It means only that wubildr is not on the first partition.

If you want to see all your partitions, you can type in Ubuntu:
```
sudo parted -l
```

---

### Post by kgandhiok on 2013-12-16
Thanks :)

---

