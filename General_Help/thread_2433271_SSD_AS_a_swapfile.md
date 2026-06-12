---
title: "SSD AS a swapfile"
date: 2019-12-16
forum: General Help
---

### Post by ra7411 on 2019-12-16
I recently installed a 0.5 tb ssd with o/s on an AMD machine (4 core CPU min MHz:1400 max MHz:3800, 8gb ram).

Other than faster bootup, I saw little speed improvement, and 40 v. 200 seconds of bootup time is almost irrelevant to me.

This might be a dumb question, but here goes:

There's a lot of advice about using  swapiness of 10 vs. usual 60 to lengthen life of the o/s ssd, but what about making the ssd only a swap file or partition, and increasing swapiness to 100.  

Wouldn't it be getting a far lower overall volume of read writes than as an o/s with o/s installs, upgrades, app installs/removals, big /home user files in and out? Even with aggressive swap it might have a long life?  

With a setup of o/s & apps on an HD, aggressive swap on the ssd, is it likely regular machine usage speed would be boosted?

thanks

---

### Post by oldfred on 2019-12-16
Moot point on SSD wear.

My Ubuntu with 4GB of RAM never used swap. Only my old laptop with 1.5GB of RAM used swap if I loaded more than one larger app like Firefox, Thunderbird or LibreOffice. But could also have several smaller apps running. 

So it may depend on your use, but normal desktop use should not even need swap and then you are not writing anything to swap.

What does this show? 
free -m

And if editing videos, 100's of tabs in Firefox or huge photos, you may want more RAM, not more swap. Swap is orders of magnitude slower than RAM.

---

### Post by QIII on 2019-12-16
Swap is a legacy of the days when RAM was expensive and even high-end systems at the time didn't have much of it.

I'm going to agree with oldfred:  With 8GB of RAM, you probably don't need *any* swap.  I haven't used it for years.

---

