---
title: "NTFS Drive - deleted items not freeing space"
date: 2007-12-13
forum: General Help
---

### Post by aerofoil on 2007-12-13
Hi all

I have been using gutsy for a while now, with an NTFS partition mounted as below:

/dev/sda3   /media/sda3   ntfs-3g  defaults,locale=en_US.utf8    0    0

When I delete items from the drive it seems to delete really fast, but doesn't free up any space on the drive?! If I cut an item and paste it elsewhere the space is freed up. 

My Current partition:

Capacity 31.2GB
Contents 13.0GB
Used Space 26.7GB
Free Space 4.6GB

Does anyone have any ides what to do - I want my hard drive space back, lol. I have googled it but only seem to find details to mount drives. 

Thanks for any help.

Aerofoil

---

### Post by Rocket2DMn on 2007-12-13
Navigate to /media/sda3 in nautilus then to CTRL+H to show hidden files.  You will see a folder called .Trash-yourusernamehere
Open that folder and see all your deleted files!  Delete them from in there and they will be gone for good!
This happens on any partition that is not your root, for future reference.

---

### Post by aerofoil on 2007-12-14
Yay problem solved - Thanks for the help and the explanation!

---

### Post by rockinlinux on 2007-12-14
also in the future you can do shift+delete and this deletes the file totally, then you wont have to do the .trash-username thing :)

---

