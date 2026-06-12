---
title: "errno:5"
date: 2014-05-24
forum: General Help
---

### Post by ix-jpn on 2014-05-24
I get errno:5 when transfering data from my usb-drive. The destination doesn't matter, even moving/copying the file within the drive gives that error.

Terminal gives this:
```
[FONT=century gothic]cp: reading ‘file.ogg’: Input/output error
cp: failed to extend ‘/home/ix/Downloads/file.ogg’: Input/output error[/FONT]
```

If I play the file in vlc I can hear it ok, so it's not (completely) corrupt.
I don't know what to do.
:confused::(:confused:

---

### Post by bapoumba on 2014-05-24
Usually, I/O errors come from a damaged file system. What file format is on your usb drive ?

---

### Post by ix-jpn on 2014-05-24
I have one that is FAT32 and the other is NTFS, both give that errno:5.

---

### Post by bapoumba on 2014-05-24
> **ix-jpn said:**
> I have one that is FAT32 and the other is NTFS, both give that errno:5.

I *think* it is better to check Windows file systems on windows, but do not quote me on that..

On Ubuntu, you have dosfsck to check the fat filesystem, which is part of the dosfstools that should be installed. You can have a look at man dosfsck for the different options.

Any error in dmesg after getting the I/O error ?

For ntfs, I'm not sure it is a good idea to check it on Ubuntu or not.

---

