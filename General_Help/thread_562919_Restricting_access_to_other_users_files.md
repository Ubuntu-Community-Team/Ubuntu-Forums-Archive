---
title: "Restricting access to other users files"
date: 2007-09-29
forum: General Help
---

### Post by Dwood108 on 2007-09-29
I have just created a new user 'guest' so anyone can use my computer, but when I log on as guest I can use the file manager to see all the files in my own home folder.

I don't want my files to be seen by other users, how can I accomplish this?

the 'guest' account is NOT an administrator account.

---

### Post by McNils on 2007-09-29
Start by denying others from reading your files.

chmod -R o-rx ~

And to prevent access to new files change your umask to 007. This can be done in a lot of places. I think ~/.profile would be a great place to add this line.

umask 007

---

### Post by mocoloco on 2007-09-29
Open the home folder (not YOUR home folder, it's one level up from yours).  Right-click on your home folder, select properties, go to the permissions tab.  Under others change "Access Files" to "none".

---

### Post by Dwood108 on 2007-09-29
Thats great thanks very much.

---

