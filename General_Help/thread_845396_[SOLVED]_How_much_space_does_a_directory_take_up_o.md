---
title: "[SOLVED] How much space does a directory take up on a fat32 partition?"
date: 2008-06-30
forum: General Help
---

### Post by Jordanwb on 2008-06-30
For my music manager that I'm making, I'm making a class that represents a drive (like my mp3 player). It recursively calculates the amount of space used by files on the drive. To make it more accurate; does a directory - on a fat32 partition - take up any space? If so how much?

[edit]

Damn wrong category.

---

### Post by Gunman1982 on 2008-06-30
The memory a directory takes on a fat32 partition depends on the cluster size and if it is a long directory name. 
You can take a look and calculate yourself:
[http://en.wikipedia.org/wiki/Fat32#Directory_table]("http://en.wikipedia.org/wiki/Fat32#Directory_table")

---

### Post by Jordanwb on 2008-06-30
So the size of the directory (in bytes) would be the cluster size + the length of the name of the directory?

Isn't the cluster size by default 4096 bytes?

---

### Post by Gunman1982 on 2008-06-30
If I recall it right and the glimps I took on wikipedia doesn't set me off to far its more like: The directory information just takes 32 bytes, but since the cluster is (assuming your default suggestion) 4096 bytes those 4096 are blocked. 
In case of a long directory name multiple directory informations are created, each in its own cluster.
But I can't guarantee that this information is correct.

---

### Post by vanadium on 2008-06-30
A directory will take up one cluster as long as all info fits into one cluster. As the directory grows larger, eventually additional clusters will be used as the need arises. If you delete files in a directory, the entries remain there and keep using the space. Eventually, an entry marked "deleted" might be reused later on when creating a new file.

---

### Post by Jordanwb on 2008-06-30
This part of my program will have to wait because Mono reports that the amount of total space on my mp3 player is 8 Petabytes. :confused:

---

