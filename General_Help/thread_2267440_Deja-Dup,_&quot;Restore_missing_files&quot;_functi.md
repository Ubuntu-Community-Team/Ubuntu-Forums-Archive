---
title: "Deja-Dup, &quot;Restore missing files&quot; function not working"
date: 2015-03-01
forum: General Help
---

### Post by pmi2 on 2015-03-01
I have a fairly new ~2 weeks old installation of Ubuntu 14.04, and I recently backed up most of my Home directory, including the Music folder with a dozen subdirectories.  

In one directory, using the "Restore missing files" does not seem to work (works in others).  The function does show up on a right-click in the directory in question, but does nothing at all.  No popup window, no scanning for missing files, nothing.

As a test, I deleted the entire DD backup directory (not the original Music folder, just the backup), and started over.  i backed up Home including the Music folder, and tried the same thing - no luck.

In other respects, this directory works fine, the music does play (.mp3), the cover art shows up, and the file tags can be edited.  Only thing that does not work is restore.

edit:

Correction, "Revert to previous version" also does not always work in this directory.  By this i mean it works on some files, but not on others, and there is no popup window with a prompt, and no error of any kind.  On other (most) files in the directory, and in other music folders, it works as expected.

(stumped)

---

### Post by pmi2 on 2015-03-02
Maybe this will help narrow it down:

Deja-Dup DOES back up the folder and the .mp3 files correctly.  I can confirm this by restoring the complete Home directory tree which has the main Music directory and down to this folder and its files.

The ONLY thing that does not work is "Revert..." and "Restore missing..." when I attempt those functions from the open folder (open in the official nemo file manager), and only this folder.  Both Revert and Restore work in the other file folders.

edit:

clicking on "Restore missing.." does nothing
clicking on "Revert..." brings up the expected Backup screen, but fails with an error,> Could not restore ‘/home/peter/Music....’: File not found in backup

---

