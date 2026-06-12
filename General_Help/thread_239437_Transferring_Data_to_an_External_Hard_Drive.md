---
title: "Transferring Data to an External Hard Drive"
date: 2006-08-19
forum: General Help
---

### Post by blue_thunder on 2006-08-19
Hi all,

I've just hooked up my Maxtor external hard drive, and I can access all of the files currently stored in it, but I don't have the permissions to copy onto it (it's read-only right now). Anyone know how I can enable these?

Also, I should add that the hard drive was only and last used while I was still running windows.

Thanks for helping.

---

### Post by orb9220 on 2006-08-19
Well that is because it is likely a ntfs partion which is the default winxp file system.

Linux cannot normally write to ntfs. There is a way but it is not  recommended if the data is critical and you do not wish to lose it. Just search using 3g as the search term.

If you want the ext. hd to have read and write abilities for winXP and linux then it must be converted to fat32 like I have a 112GB that is fat32 for my pics,music that is availiable to xp and linux.

 The disadvantage is I cannot write a file ex: 4.4GB dvd iso file to it because fat32 limits single file size to 3.99GB. To get around that I use dvdshrink in linux   to rip as file instead of iso and that works great as a workaround.

---

### Post by blue_thunder on 2006-08-19
Alright. I've got the ntfs-3g thing up and running--no problems so far. However, I would like to know what the dangers are? Also, how would I convert it from ntfs to fat32?

Thanks again.

---

### Post by orb9220 on 2006-08-19
Well I converted my using partition magic in windows. After doing a defrag,defrag,defrag. Very important to keep from losing data.

I don't think you can in linux and windows built in only does fat32 to ntfs  I believe.

The only other way is to backup stuff onto dvd's or another hd then reformat to fat32 and copy back.

---

### Post by yopnono on 2006-08-19
There is some drivers that allow read/write to ext from windows, just like you have ntfs read/write for linux.

---

