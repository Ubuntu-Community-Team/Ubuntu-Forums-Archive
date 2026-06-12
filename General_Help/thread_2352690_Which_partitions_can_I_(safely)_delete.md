---
title: "Which partitions can I (safely) delete ?"
date: 2017-02-14
forum: General Help
---

### Post by Odense on 2017-02-14
I have bought a cheap Lenovo laptop with a 120 or 130 GB SSD.
It does boot reasonably fast but I would still have preferred to get it with more space like a 1 TB HD - but done is done.


I have made a new partition and installed Ubuntu 16.0.4 on it and the dual boot works well.


Apart from the Windows 10 partition and the Ubuntu Linux partition there is a Linux swap partition and some restore partition.


Please have a look at the screen shots and tell me which partions I can safely delete. I don't want to restore from a partition anyway (I use a external drive for that) and I don't think I need a driver library - but I want windows 10 and Ubuntu Linux to keep working.

---

### Post by HereInOz on 2017-02-15
Personally the only partition I would consider deleting is sda5 because that is probably (emphasis on "probably") your recovery partition but I cannot guarantee that the system will work OK after you delete it.  The rest kinda have to be there.

---

### Post by Odense on 2017-02-17
Thanks - I guess I must ponder how much of a gambler I am :-D

---

### Post by Mark Phelps on 2017-02-17
I don't actually think you can safely delete any of them -- without consequences.  The one labeled Lenovo_Part is most likely a factory recovery partition loaded there by Lenovo.  If you create recovery media on your own, you could remove that.  But to really use the space, you need to remove the Win_RE partition in front of that, and that is most likely used by the Lenovo recovery utility.  Once those two are gone, you can reuse about 18GB of space.

Good Luck

---

