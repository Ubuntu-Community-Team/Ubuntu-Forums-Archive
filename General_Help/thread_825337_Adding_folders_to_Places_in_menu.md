---
title: "Adding folders to Places in menu"
date: 2008-06-10
forum: General Help
---

### Post by JustAnotherVagueAnon on 2008-06-10
I put all my Documents, Pictures, Videos, Music, etc. on a separate internal HDD and would like to create links to them in the places menu so that I am directed to the folders in my separate HDD when I click them. How can I do this? Also, does my extra drive need to be automounting to do this? The drive is listed in places when Ubuntu starts up, but if the system needs to access files from this drive, they do not appear until I have clicked the drive and it has mounted.

---

### Post by bpl07 on 2008-06-10
Open the folder you want to add to Places, then choose Bookmarks>Add Bookmark.

---

### Post by bpl07 on 2008-06-10
Or you could replace your default folders with soft links to your new folders.  This would probably work slightly better for integration with applications.

Open a terminal, then type:

> ln -s */location/of/folder*

For example, if your Documents folder is at /media/Storage/Documents, you'd type:

> ln -s /media/Storage/Documents

Make sure you remove the original folders first.

---

### Post by bpl07 on 2008-06-10
Oh, and install ntfs-config to set up your drives to automount.

---

### Post by JustAnotherVagueAnon on 2008-06-10
Thanks :)

---

