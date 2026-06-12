---
title: "~ files"
date: 2007-01-31
forum: General Help
---

### Post by Mateo on 2007-01-31
1)  why is it that almost any time I edit a text file of some kind, a file with the same filename and a ~ at the end (like "filename~") gets created?

2) how can I make it not do this!

thanks.

---

### Post by ~LoKe on 2007-01-31
1.  That's a sort of "ghost" backup.  I like them incase I'm too lazy to back up my fstab or xorg.

2.  Open up GEdit (text editor).  Edit -> Preferences.  "Editor" tab, uncheck the "Create a backup copy of files before saving".

---

### Post by taurus on 2007-01-31
I believe gedit creates a backup file when you run it!  I don't have that problem when I use vim (from a terminal).  Maybe you want to look at the options or preferences in the top menu to see if you can turn that off.  I am at home right now so I can't check it until I get into the office tomorrow.

---

### Post by FluffyElmo on 2007-01-31
The default behavior of *gedit* is to make a back-up copy of the original file just before you save. You can turn it off in the preferences. 

Launch the text editor (*Applications->Accessories->Text Editor*), and then from the text-editor menu select *Edit ->Preferences*. Click on the *Editor* tab, remove the check-mark from beside '*Create a backup copy of files before saving*' in the *File Saving* section.

Close the dialog and exit the text editor and you should now be OK...

---

### Post by Mateo on 2007-01-31
ok thanks.  i was thinking it was a ubuntu thing, not just a gedit thing.  that should be easy to fix then.

---

