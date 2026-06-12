---
title: "[SOLVED] How do I change External USB FAT32 partition lable?"
date: 2008-02-08
forum: General Help
---

### Post by mdurham on 2008-02-08
Hi Guys, I think the title says it all. Any ideas?
Cheers, Mike

PS
What does LOL mean?

---

### Post by taurus on 2008-02-08
You can try gparted in System -> Administration.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```

---

### Post by mdurham on 2008-02-09
> **taurus said:**
> You can try gparted in System -> Administration.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```

Thanks for replying taurus but I don't think your advice is correct. Gparted can't set a lable on an individual partition (at least on the version I have in Gutsy Ver 0.3.3), it only sets it for the whole device (e.g. sdb) along with a warning that doing so will remove all data on the device. That's not exactly what I want to do. I just want to set one lable of many FAT32 and EXT3 usb partitions and retain it's data.
I imagine that this might be impossible judging by the lack of responses to this post.

Cheers, Mike

---

### Post by mdurham on 2008-02-12
I found the answer here: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")
Cheers, Mike

---

