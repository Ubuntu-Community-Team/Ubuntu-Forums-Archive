---
title: "Having trouble restoring my Backup"
date: 2016-11-10
forum: General Help
---

### Post by Arminius on 2016-11-10
I used the default Backup software that was in Ubuntu 12.04, it made a lot of .gpg files.
When I try to restore them with backup tool it either goes through the entire process only to have no files appear at the destination folder.
or it hangs at calculating, it does that more lately.

---

### Post by Arminius on 2016-11-12
bump

---

### Post by g33zr on 2016-11-13
Is this something that happened all along or is it a recent phenomenon?

---

### Post by Arminius on 2016-11-13
> **g33zr said:**
> Is this something that happened all along or is it a recent phenomenon?

Recent, only because before now I used to just copy and paste all my folders into a spare drive, first time using the default backup software.

---

### Post by deadflowr on 2016-11-13
It's asking for a password at some point, right? or no?

---

### Post by Arminius on 2016-11-13
> **deadflowr said:**
> It's asking for a password at some point, right? or no?

The only password that gets asked is when I first load backup tool

Archive is ticked, Directory is not.

Source is the .gpg file
Destination is the home folder
I click on forward and nothing happens.
no error message, no helpful info at all.

I tried using directory, the directory the back up is in, to the home folder.
But all it did is transport every single .gpg file to the home directory.

---

### Post by g33zr on 2016-11-14
I'm not familiar with Ubuntu 12.04. Is Deja-Dup the default backup app and you're using it to backup your Home folder to an external backup drive? When you set up your backup, did you designate "Home (your user name)" as your backup destination or did you use another folder name such as "Backup"? If your source is your Home folder on your HDD and your backup destination is your Home folder on your external drive, then the Backup app should be able to find and restore your folder. All you have to do is select the date from which you want to restore.

---

