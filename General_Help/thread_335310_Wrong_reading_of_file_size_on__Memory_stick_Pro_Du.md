---
title: "Wrong reading of file size on  Memory stick Pro Duo"
date: 2007-01-10
forum: General Help
---

### Post by CroEragon on 2007-01-10
I have problem with reading my Memory stick Pro Duo.
I have Sony Ericsson W850i and i got Memory stick Pro Duo 1GB with it. I have about 600mb of songs and some pictures, themes and so on on it. I had D12's songs on it and i deleted'em and after some time now i want same songs back on stick. Problem is that Ubuntu says that there is no enough free space on it (and there is, after deleting D12 i didn't add anything). I even tried to deleting some other songs and it still says "Not enough space". When i select all files on sticka and Properties it shows 798mb of data but says just 19mb of free space. So it looks that there is about 200mb unallocated space but i didn't change partition on it. It is same as before. And i could use it before.
Anyone got any ideas?

---

### Post by Obor on 2007-01-10
Ubuntu and memory sticks is bit funny from my experience. I suggest you go to show hidden files and delete .trash from you stick. for some reason ubuntu just moves things to the .trash folder on the stick when you delete them.

[There is a bit about it here.]("http://ubuntu.wordpress.com/2006/09/13/no-trash-on-external-usb-drives/")

---

### Post by CroEragon on 2007-01-10
Thanks, deleting trash resolved my issue. I knew about hidden trash on NTFS drives when you use ntfs-3g but not on FAT16 partitions.

---

