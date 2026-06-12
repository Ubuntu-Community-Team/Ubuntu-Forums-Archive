---
title: "Uninstalling and then reinstalling Wubi preserves /home?"
date: 2007-07-16
forum: General Help
---

### Post by CSMatt on 2007-07-16
I came across an Error 17: file not found error with GRUB4DOS.  As suggested in the Wiki, I checked to see that c:\wubi was defragmented with JkDefrag and not compressed.  When neither of these remedies worked, I uninstalled Wubi.  From what I can recall, this deleted my c:\wubi folder.  I had copied system.virtual.disk, home.virtual.disk, and swap.virtual.disk to c:\ so that I could reinstall Wubi and then overwrite the new virtual disks with the backups.  However, when Wubi finished installing, I was surprised to find out that it somehow did not lose the home.virtual.disk file, even though system.virtual.disk was new.  How is this possible?  Granted, I downloaded the latest Wubi installer and the alternate ISO image to c:\, the same folder where the backups of the disks were, but how did Wubi preserve home.virtual.disk when it got deleted?  Does it undelete the file?

---

### Post by CrazyGuy123 on 2007-07-16
usually during uninstall, it moves the home disk and downloaded CD image to the c:\wubi-save folder - thats the two checkboxes on the uninstaller.  (I guess you just clicked next next next through it rather than reading it - just like I do :))

During installation, if the wubi-save folder is found, the files in there are used for the new installation.

---

### Post by ago on 2007-07-16
When you uninstall, there is an option to backup home (that's selected by default), it will save home into wubi-save and reuse it automatically on next installation, so that your settings and files are preserved

---

### Post by CSMatt on 2007-07-16
There were no questions regarding any backups during the uninstall.  there was only the statement that Wubi was in c:\wubi, and then Uninstall and Cancel buttons.  I had initially installed with an earlier version of Wubi, so this checkbox you are referring to might have not been there yet.  There certainly isn't any wubi-save folder now, and I don't remember there being one then either.

I just checked and home.virtual.disk isn't in c:\ anymore, although I'm sure that I put it there.  The system.virtual.disk and swap.virtual.disk images are still there though.  Seeing as Wubi and the ISO image were also run in c:\, is it possible that /home was found here by Wubi in the same way that it found the ISO image?

---

### Post by ago on 2007-07-17
> **CSMatt said:**
> There were no questions regarding any backups during the uninstall.  there was only the statement that Wubi was in c:\wubi, and then Uninstall and Cancel buttons.  I had initially installed with an earlier version of Wubi
It must be quite an old version there. You should use the latest wubi you find in the website.

---

