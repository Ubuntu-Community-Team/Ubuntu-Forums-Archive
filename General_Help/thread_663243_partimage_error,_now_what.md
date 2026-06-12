---
title: "partimage error, now what?"
date: 2008-01-09
forum: General Help
---

### Post by starling on 2008-01-09
A discovered bad blocks in the linux partition of my HDD. So I've taken an image of the other unaffected partition on the drive (windows NTFS). And since then the cancer has taken over that partition as well.
So I have a 30gb gzip file which partimage can't restore due a known bug (I didn't know). I have an empty partition which is 40gb (smaller than the previous windows partition) and I need to get the two together.

Any ideas? How can I get the gzip file decompressed onto an empty partition?

Thanks.

---

### Post by starling on 2008-01-09
At the risk of speaking too soon, I might have found the answer [here]("http://www.partimage.org/forums/viewtopic.php?t=213"). Had to change the extension to .gz (I thought linux was immune to that sort of thing) and am currently making an uncompressed image file which apparently will work in partimage 
*fingers crossed*

---

### Post by wieman01 on 2008-01-10
Please beware of the fact that the new partition must have the same size as the one from which you have created the image. Otherwise you'll run into trouble.

---

### Post by starling on 2008-01-13
> **wieman01 said:**
> Please beware of the fact that the new partition must have the same size as the one from which you have created the image. Otherwise you'll run into trouble.

Indeed I did. Turns out windows doesn't like being on the second partition either.
Now, on the first partition, it has some hal.dll error. Stupid windows.

---

