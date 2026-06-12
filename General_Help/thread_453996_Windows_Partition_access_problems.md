---
title: "Windows Partition access problems"
date: 2007-05-25
forum: General Help
---

### Post by grogger13 on 2007-05-25
I just installed ubuntu on my families old desktop, and festy imported all the user names and it recognizes the windows partition.  On my user name i can access the windows folder, but on the others it says they don't have access to it.  When i try to change the group it tells me i dont have the rights to change it.

Then i logged in as the root to try and change it and it didn't work, then i tried "chown" but it said
```
chown: changing ownership of `/media/disk': Operation not permitted

```

---

### Post by ezrollers on 2007-05-25
> **grogger13 said:**
> I just installed ubuntu on my families old desktop, and festy imported all the user names and it recognizes the windows partition.  On my user name i can access the windows folder, but on the others it says they don't have access to it.  When i try to change the group it tells me i dont have the rights to change it.

Then i logged in as the root to try and change it and it didn't work, then i tried "chown" but it said
```
chown: changing ownership of `/media/disk': Operation not permitted

```

What type of windows partition is it? ntfs? FAT?

How is it mounted? ro? rw?

---

### Post by grogger13 on 2007-05-25
I had problems with this machine before on partitioning it, so for some reason i partitioned with fat32.(its only about 40gigs),
 then it stopped working 
so i put the live cd of ubuntu in and it gave the menu in the beginning, but when i selected launch live cd it gave me a kernel panic, not syncing.  Then i tried mem test and it basically 100% errors so i took one of the ram sticks out and the computer would boot into the live cd

I didn't want the files to be lost from windows so i dual booted it and now i cant get my sisters profile to read music from her windows folder because it gives me a can't access.

I'm not sure how it is mounted, because i really didn't know there where different ways.  It is an old ide harddrive if that helps, and it was just detected by ubuntu

didn't realise what you meant, i believe it is read and wright because it is fat 32, i would have installed nfts-3g if it where ntfs

---

### Post by ezrollers on 2007-05-25
can you post the output when you type *mount* on a terminal

---

