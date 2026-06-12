---
title: "Trash wont fully empty because USB drive is missing"
date: 2013-05-30
forum: General Help
---

### Post by kevincs on 2013-05-30
1) Insert USB media.
2) Delete file on USB media --> It gets put in .Trash at the top level of the media, and the Trash icon on the side pane becomes full.
3) Eject media.
4) Empty Trash --> This will never fully empty, because the USB media is missing.  The icon remains full.


Reinserting the media and emptying works, but this time I have formatted the USB, so even this no longer works.


How can I get rid of the full trash icon on the side pane?  Where is the file that is telling ubuntu / gnome / nautilus / whatever what files should be in the trash?  ~/.local/share/Trash is empty.

Ubuntu 12.04 3.2.0-41-generic

---

### Post by CatKiller on 2013-05-30
I don't know where else it would be, but you should be able to use locate on the filename to find it. Then an rm should get rid of it.

---

### Post by BBQdave on 2013-05-30
> **kevincs said:**
> How can I get rid of the full trash icon on the side pane?  Where is the file that is telling ubuntu / gnome / nautilus / whatever what files should be in the trash?  ~/.local/share/Trash is empty.

Show *hidden files* in Trash and USB Stick may reveal the files you wish to delete. If you do find the files; SHIFT - DEL will allow you to permanently remove files from your USB Stick and Ubuntu.

Deleting files from my USB attached Sansa Clip+ does not remove files, but places them in a hidden trash folder on the Sansa Clip+ drive. So drive space is still used - the deleted files are just hidden. To remove the files from the Sansa Clip+ drive, I select the files and strike SHIFT - DEL, which allows me to remove the selected files from my Sansa Clip+ drive.

---

