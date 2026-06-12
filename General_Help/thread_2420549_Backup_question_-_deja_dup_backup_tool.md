---
title: "Backup question - deja dup backup tool"
date: 2019-06-06
forum: General Help
---

### Post by Tom_Carr on 2019-06-06
I am using the deja dup backup tool.  In the folder on my computer where I told it to put the backup it put a bunch of files ending in .gpg such as 

duplicity-full.20190606T160635Z.vol10.difftar.gpg

If I click on one of these files it can not be opened.


Is  deja dup backup tool the best thing to use for backups, and if not what would you recommend?

If  deja dup backup tool is a good backup, what are the .gpg files and how do I open them?

---

### Post by #&amp;thj^% on 2019-06-06
I'm just commenting on this "If deja dup backup tool is a good backup, what are the .gpg files"
Déjà Dup relies on duplicity to handle the encryption, and it uses gpg with a symmetric cipher. Basically, that means it is encrypted just with the password your provide. You will need to remember that password to restore your data. 
Makes sense right? :)

---

### Post by Tom_Carr on 2019-06-06
I understand a little more about it now.  You use the backup tool to restore from the .gpg files.  You have to restore the whole backup though.  You can't just restore a few files or folders.

---

### Post by deadflowr on 2019-06-06
You can restore individual files directly through the File manager.
Open Files and right click Should give a Restore missing files (or revert to previous version).
Which will then open a deja-dup popup window which will run a check and then list any and all files that have backups for whatever directory you've right click in/on.
From there you can select which files to restore and then from when.

After that all you need to do is enter the encryption password you set, if set.
(Note if you selected the option to save the password when you created the backup, then it'll use that without interaction.
(The saved password will be listed in Passwords and Keys in the Login section) 

Make sense?

edit: Also note you only get the restore/revert options for folders in the Include list (folders to save).
Any folder marked as excluded (folders to ignore) in deja-dup will not get the options.

---

### Post by Tom_Carr on 2019-06-06
I see how it works now.  Thanks.

---

