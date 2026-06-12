---
title: "Buffer I/O error"
date: 2006-08-30
forum: General Help
---

### Post by Jii92 on 2006-08-30
```
Buffer I/O error dm-0, sector *numbers*
```
Everytime when i boot Ubuntu install cd (newest version), i get this.
I get some 50 msgs and then it will boot to ubuntu. But partition section in install will freeze install program. :(

I heard that some usb devices might do that, should i plug them out?

I have Windows XP on master drive (maxtor's 80 g) so i have ntfs file system. I have tried to chkdsk that drive, but that doesn't work. (i have my 250 g maxtor's sata drive in chkdsk at home and i put my maxtor 80 g slave drive to chkdsk when i get home, im now at school)

But if that doesn't work, is there any other soluitions?

Ps. Im installing Ubuntu as dual boot.

---

### Post by ayoli on 2006-08-30
this isnt enough to knw what drive is concerned by the i/o errors, that also may be your cdrom drive. Did you try another one ?
Does the errors messages mention anything else about drives (i mean something like : hda1, hda2, sda1, sda2, sdb1, ....) ?
regards.

---

### Post by Jii92 on 2006-08-30
> **ayoli said:**
> this isnt enough to knw what drive is concerned by the i/o errors, that also may be your cdrom drive. Did you try another one ?
Does the errors messages mention anything else about drives (i mean something like : hda1, hda2, sda1, sda2, sdb1, ....) ?
regards.
No, nothing else.

Oh, i pluged hard drives out expect my sata drive. (sry my bad english)
Then i started my computer with Ubuntu CD, and..I got through of it. But i now download ubuntu alternative cd, let's see if that works.

---

### Post by jdong on 2006-08-30
dm-0 leads me to believe it's the device-mapper device that's created from the LiveCD, so the LiveCD is corrupt.... Have you tried burning the CD a bit slower or using different media?

---

### Post by Jii92 on 2006-08-30
> **jdong said:**
> dm-0 leads me to believe it's the device-mapper device that's created from the LiveCD, so the LiveCD is corrupt.... Have you tried burning the CD a bit slower or using different media?
I have used ImgBurn with 2x speed (i choosed 1x, so it will select slowest speed) and desktop.iso was correct with md5. Media was Verbatim's cd-r.

Well, in alternative..It freezed in partition section. :(

---

