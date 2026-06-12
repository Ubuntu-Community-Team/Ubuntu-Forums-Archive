---
title: "Folder contents disappeared on ntfs partition"
date: 2008-04-18
forum: General Help
---

### Post by redline99 on 2008-04-18
Hi there, 

I recently did lots of read write operations on my windows ntfs partition from ubuntu 7.10. Then suddenly i noticed the contents of my movies folder, which was more than 100Gb, just disappeared. It says folder is empty both from ubuntu and from windows. They just disappeared. 

The rest of the ntfs partition is ok. Windows works fine and there is no other loss. 

Another problem is that i cant access some dirs from windows which are in the ntfs partition but created from ubuntu. The owner of the folders is root but even that i can't change it from the gui (I didn't try the command line yet), and yea I can't access the folders from windows, it says access restricted or something. 

Any ideas???

---

### Post by vanadium on 2008-04-18
You will certainly need to check the ntfs partition thoroughly using the Windows tools.

When using an ntfs partition on a dual boot system, you must be aware that the ntfs volume must be properly "closed' by windows before accessing it under Ubuntu. This means that you must exit Windows completely (no hibernate!) before booting Ubuntu.

The ntfs permission system is not compatible with that of Ubuntu. For this reason, permissions you see under Ubuntu on an ntfs volume have no meaning. You should check the permissions of the directories you created on Ubuntu under Windows to see wether permissions have anything to do with this. My guess is that what you observe all results from the ntfs volume being damaged. That is why I suggest to do a torough check and repair under Windows.

---

### Post by george9233 on 2008-04-18
There is an easy way of changing the permissions of folders which are owned by root:
```

sudo nautilus

```
Then the window opened has the root permission.

---

### Post by vanadium on 2008-04-18
@george9233: it might have escaped you that this here concerns an ntfs volume.

---

