---
title: "my ~/.Trash folder points to my d drive after upgrade"
date: 2007-10-20
forum: General Help
---

### Post by rigelstar on 2007-10-20
my ~/.Trash folder points to my d drive after upgrade.  I can't find a way to unlink.  Ive attached screenshots.  

The odd thing is that ls -a lists nothing:

[email]rigelstar@rigelstar-desktop:~/.Tras[/email]h$ ls -a
.  ..

But, the nautilus Trash icon shows the contents of my d drive.  Not as in all my files from d got moved to ./Trash but the ./Trash folder acting as a symbolic link to my d drive.  

If I delete a file from the ./Trash folder it gets deleted from the d drive.  So I can't simply empty my trash folder without losing everything on d.  

Somehow during the upgrade the .Trash folder points to my d drive.

---

