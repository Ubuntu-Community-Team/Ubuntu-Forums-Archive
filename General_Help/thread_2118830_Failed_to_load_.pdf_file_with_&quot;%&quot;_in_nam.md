---
title: "Failed to load .pdf file with &quot;%&quot; in name."
date: 2013-02-22
forum: General Help
---

### Post by 2CV67 on 2013-02-22
Since upgrading to 12.10 yesterday (but that could be a coincidence) I suddenly found myself unable to open a couple of .pdf files.

Normally, these are opened with Document Viewer, now at v.3.6.0, but that gave a large red display I have never seen before, saying:
"Failed to load remote file. Failed to create a temporary file. No such file or directory".
I tried opening with Acrobat Reader v.9 & that gave no message, but left the window black.
I tried LibreOffice Draw v.3.6.2.2 & that opened the file perfectly...

In File Managers (Nautilus & PCManFM) the files look OK, with correct sizes & legible Thumbnails.

I have backups in an External hard drive, but with exactly the same results.

Switching to my Ubuntu 10.04LTS drive, the backup files in the EHD opened instantly using Document Viewer v.2.30.3.

I made fresh copies of the backups, placed them on LTS desktop & tried opening from 12.10, but no good.

I tried opening lots more .pdf & other files in the original folder & all were OK.

At that point, it struck me that both problem files had "%" characters in the file name.
I checked with lots of Googling & "%" is supposedly a valid filename character.
But when I removed the character, both Document Viewer & Acrobat Reader now open the files perfectly.

I don't need any help on this, but am posting:
 - In case it can help anybody else.
 - In case anybody knows why "%" is suddenly not accepted.

Thanks!

---

### Post by 2CV67 on 2013-02-23
I did a bit more digging and found .pdf files with "%" in the name were opened without problem in:
- Lubuntu 12.04 - Document Viewer 3.4.0
- Ubuntu 10.04 - Doc Viewer 3.6.2.2
- Windows 7 - Adobe Reader 9.1.0
- Windows XP - Adobe Reader 9.5

I also looked at .jpg files:
.jpg files with "%" in the name were opened without problem in:
- Lubuntu 12.04 - Image Viewer 3.4.2  &  GPic Viewer 0.2.2
- Ubuntu 10.04 - Eye of Gnome 2.30.0  &  Gimp 2.6.8
- Windows 7 - Picasa  &  Windows Photo Viewer
- Windows XP - MS Office Picture Manager

But .jpg files with "%" Fail to open in Lubuntu 12.10 with:
- Gimp 2.8.2
- Image Viewer 3.6.0 (Gnome)
- GPicView 0.2.3
- Image Magick

Conclusion:
Lubuntu 12.10 Fails to open files with "%" in the name, whereas Lubuntu 12.04, Ubuntu 10.04, W7 & XP handle that easily.

Is that a bug or is it deliberate?

---

