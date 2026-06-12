---
title: "Image disck with two operating systems."
date: 2019-12-16
forum: General Help
---

### Post by michael351 on 2019-12-16
I have both Ubuntu and windows 10 loaded on my mini PC's internal HDD. I would like to image the entire disk to an external drive for backup/restore should my internal drive fail. Is this easy to do?
I would have to boot from this external drive should my internal drive fail and then restore to a new drive.

---

### Post by SeijiSensei on 2019-12-16
```
sudo apt install gddrescue
```

ddrescue will make a bit-for-bit copy of the source device to the target device. Used this twice to replace SATA drives with SSDs in laptops.

You'll need to boot from a third device since copying the disks requires they both be unmounted.

---

