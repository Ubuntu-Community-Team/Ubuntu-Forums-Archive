---
title: "Unable to change Steam Library Folder to a separate drive"
date: 2020-04-12
forum: General Help
---

### Post by gottaslay on 2020-04-12
I have 2 SSDs and 1 HDD. [https://i.imgur.com/yjAZoVU.png](https://i.imgur.com/yjAZoVU.png)
 
I'd like to be able to install my Steam games to the 1000GB drive that can be seen in the screenshot. However, when I go to Steam's Library Folders and attempt to add a new folder: [https://i.imgur.com/RcmKps9.png](https://i.imgur.com/RcmKps9.png)

Only a "/" drive can be seen which is the 120GB SSD that my Ubuntu installation is running on. Neither my 500GB NVMe or my 1000GB HDD are shown as an option when attempting to create a new library folder. Now I normally wouldn't be too worried but... my 120GB drive will be screaming for mercy if I begin installing games on it. As a little bonus: OBS Studio also doesn't see these two drives.

---

### Post by CatKiller on 2020-04-12
You don't ever deal with drives (or partitions, which would be more accurate) directly when doing file management things. You just go to the place in the filesystem tree where those partitions are mounted.

---

### Post by zer010 on 2020-04-12
If I'm not mistaken there is an option in Steam to choose where to download and install game files.

---

