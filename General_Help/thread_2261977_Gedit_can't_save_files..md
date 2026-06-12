---
title: "Gedit can't save files."
date: 2015-01-22
forum: General Help
---

### Post by moteprime on 2015-01-22
My Gedit has greyed out the 'Save' button, and only offers to 'Close without saving'.
Other programs saves the same files without any problems and i seem to have enough rights.
The only thing i have been messing with are changing the 'Run', 'Display or 'Ask' option for texts files in Nautilus, but i set it back.
I also reinstalled gedit.

I can't figure out what to do, please help.

---

### Post by oldrocker99 on 2015-01-22
Is the file you're trying to edit in your /home directory, or in any other directory? You only have read/write access to /home. For any other text file, for example, in /etc, you need to start it this way:
```
gksudo gedit
```
This will allow you to edit any text file, but don't use it that way to edit /home text files, since it will change ownership of the file to root, which you **don't** want to do.

---

### Post by moteprime on 2015-01-22
This happends with files all my home folder, even on a usb drive.
With 'gksudo gedit' it works. But i have the permission for the file, and i can save the file if i open it with Libre office write instead, only gedit will not.
If i make a test file on my desktop, that have the permission read and write, for Me, my group and others. I open it with gedit, i cannot save it. open it with libre office i can save it. with 'sudo gedit' it does not work, but with 'gksudo gedit' i can save it.
i must have broken something in gedit?

---

