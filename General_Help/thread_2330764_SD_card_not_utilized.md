---
title: "SD card not utilized"
date: 2016-07-14
forum: General Help
---

### Post by s9032g@comcast.net on 2016-07-14
I have a laptop with a small capacity SSD and no hard drive. For extra space I added an 8 GB SD card. The card is recognized i.e. I can see it's presence; however it is not utilized to do anything. I cannot, for example, copy anything to it.

---

### Post by ajgreeny on 2016-07-14
Is it formatted and if so to which filesystem?

Run command ```
sudo parted -l
``` and report back here the output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by s9032g@comcast.net on 2016-07-15
After further consideration I believe the problem is that it is an SDHC card that is not compatible with my Dell Mini 9

---

