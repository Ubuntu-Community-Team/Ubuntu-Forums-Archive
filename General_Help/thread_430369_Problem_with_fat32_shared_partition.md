---
title: "Problem with fat32 shared partition"
date: 2007-05-02
forum: General Help
---

### Post by Nightfall on 2007-05-02
Hello,
I have a dual boot system: WinXP - Ubuntu Feisty.
I would like to share data saving my documents in a 30GB fat32 partition.
But I have a problem when saving PDFs (for example) from the web directly to fat32: the PDF is stored as "Text document" and the owner is "root". Then if I double click on it, I get some security error (sorry I can't post it now).
Instead, if I save the PDF to my home, everything works great, even if I move it to fat32 later.

Can you help me please? I hope it's just matter of changing some properties in fstab.

---

### Post by Steve H on 2007-05-02
That is odd, without the error it is hard to work out what is going wrong. I have a shared FAT32 drive for my mp3's, and never had any problems.

Have you checked your permissions on the etc/fstab? it may be a simple permissions problems, but I doubt it as you seem to be writing to the disk ok.

If you could post the error that would definitely help.

:)

---

### Post by strabes on 2007-05-02
Sorry for the non-answer but I'm a big fan of using ext3 as my shared partition filesystem and using the driver from fs-driver.org to read/write to ext3 from windows. It works perfectly.

---

### Post by Steve H on 2007-05-03
strabes, the driver from fs-drivers is good, but no use to me as I'm using my shared partition as my "music share" it would be too slow for the media players. I have used a driver from fs-drivers but it was much slower than just using FAT32, and as long as you don't have anything like system files on there, then there is no security risk.

---

### Post by orb9220 on 2007-05-03
Post your fstab here for the fat32 partition.

I have a 120GB fat32 that I share with xp.

---

### Post by Nightfall on 2007-05-07
thank you for fs-driver suggestion

---

