---
title: "different file size in file managers"
date: 2016-04-03
forum: General Help
---

### Post by PLIACHAS PASCHALIS on 2016-04-03
Hello everybody. I use PCManFm 1.2.3 and Nemo in my UbuntuStudio. I am at  the same folder in both filemanagers and the same files in  detailed List view seem to have different size. Here are the printscreens.
[ATTACH=CONFIG]268150[/ATTACH][ATTACH=CONFIG]268151[/ATTACH]

Any Idea about what is happening?
Thanks in advance

---

### Post by X-RED_Tech on 2016-04-03
Different units are being used hence the difference.

KiB vs KB
GiB vs GB
etc.

---

### Post by PLIACHAS PASCHALIS on 2016-04-03
But as you can see in attachments both units are in Gb's

---

### Post by Impavidus on 2016-04-03
No. Under devices both are in GB and both give the same numbers. On the right one uses bytes, KiB and GiB, the other bytes, KB and GB. 1KiB=1.024KB, 1GiB=1.073741824GB, so all numbers are consistent.

---

### Post by X-RED_Tech on 2016-04-03
What I see in your attachments is exactly what I commented above. Read again and learn the difference between GiB and GB. Use Google if you need. I ain't doing your homework for you...

---

### Post by nerdtron on 2016-04-03
> **PLIACHAS PASCHALIS said:**
> But as you can see in attachments both units are in Gb's

Are you pertaining to the .vdi files? As shown on the screenshots you've attached, one is GB while the other is GiB. The size computation is different since they are different units.
More reading: [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

---

### Post by PLIACHAS PASCHALIS on 2016-04-03
Sorry the bytes are the same, (from the file properties) but the one unit is Gib and the other is GB

---

### Post by X-RED_Tech on 2016-04-03
So, you understand now?
Perhaps marking it solved is a good idea.

---

