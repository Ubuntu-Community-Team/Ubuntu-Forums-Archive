---
title: "Easy Tag and Permissions"
date: 2007-03-23
forum: General Help
---

### Post by le_vainqueur on 2007-03-23
I have all of my mp3s (about 5000) on a separate FAT32 shared partition.  I was hoping to use Easy Tag to change the file names of all of the files, but when attempting to do so it informs me that it does not have permissions to write to that disk.  I checked the permissions by right clicking on the drive, and found that the permissions were as follows:

Owner: Can view and modify content
Group: Can view and modify content
Others: Forbidden

It is not possible, however for me to modify anything withing this dialog box (everything is greyed out).  I tried logging in as the super user by typing sudo su into the Konsole, but that did not change the results.  Any suggestions?

---

### Post by ffxr on 2007-03-23
that looks like a more general permissions issue on that FAT32 drive.. can you write anything at all to that drive? is the drive being mounted with read/write permissions?

---

### Post by le_vainqueur on 2007-03-23
I tried to create a new text document and save it to that partition, and it worked fine.  I also opened a text document, modified it, and saved it without complications.

I do remember having a problem saving an Audacity file to that partition a few days ago, though.  I didn't have time to do anything about it, though, so I just saved it to my home folder.

Is there away the FAT32 problem?

---

