---
title: "how to format a data hard disk..."
date: 2008-03-26
forum: General Help
---

### Post by LK_gandalf_ on 2008-03-26
Hi all, I have a pc windows xp and kubuntu 8.04, on two different partition. Then I have a 160gb free partition I have to use to store data, music, video, documents, and so on. The user will use both windows and linux for some month, then if everything goes well, only Linux. He will install some videogames on this partition.

what kind of file system do you thinks is the best choose for that partition? fat32, ntfs or ext3 (with the proper driver for windows)?
Thank you

---

### Post by unoodles on 2008-03-26
Well, windows cannot read ext3 partitions so you probably dont want to go with that.

fat32 does not support files greater than 4gb, if you know for sure that you will not have files bigger than 4gb than i recommend fat32. otherwise i guess you're stuck with ntfs

---

### Post by forestpixie on 2008-03-26
If you're talking about the storage partition for both linux and win - I would go for ntfs.
NTFS support in linux is better I think than ext3 supprt in win.

Of course I expect you'll get other options :)

---

### Post by LK_gandalf_ on 2008-03-26
I'll chose the ntfs, because there are files greater than 4gb. I wonder if the ext3 supporto in windows was fine, but it's not the case :) Thank you

---

