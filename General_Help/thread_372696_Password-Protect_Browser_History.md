---
title: "Password-Protect Browser History"
date: 2007-02-28
forum: General Help
---

### Post by navneeth on 2007-02-28
Is there a way I can protect the History(Firefox) from deletion unless the user provides a password?

---

### Post by Ramses de Norre on 2007-02-28
It's hold in ~/.mozilla/firefox/*.default/history.dat, * is a certain string for your user profile.
I'm afraid you can't deny write privileges on this file because firefox wont write to it neither then...
But you could regularly back it up if no one finds a better way..

PS: I'm not sure how hardlinks act when one representation of the inode is deleted, maybe you can look into that and create a hardlink to the history file somewhere without anyone knowing it.

---

### Post by navneeth on 2007-02-28
> **Ramses de Norre said:**
> But you could regularly back it up if no one finds a better way..

PS: I'm not sure how hardlinks act when one representation of the inode is deleted, maybe you can look into that and create a hardlink to the history file somewhere without anyone knowing it.

I'm afraid I don't understand what you say in your post script, but is it possible to copy the contents of the history files dynamically to another file elsewhere?

---

### Post by Ramses de Norre on 2007-03-02
Well, a file is basically a reference to a certain place on your harddisk, if you open a file you tell your computer to show you the data on that certain place.
A hardlink is a second file which holds the same reference as the one your linking with, so it's in fact a second place from where the data can be accessed and it doesn't go to the first file and then to the harddisk like a symlink does.

If someone changes the history file this will be represented in both files, what I was suggesting was that maybe if one of the hardlinked files gets deleted, the other one persists and thus when someone thinks he has deleted his history file, you still have it.

The only problem could be that probably if firefox deletes the history, it doesn't remove the file but rewrites it blank. And in that case you wont be able to recover it this way...
It was just a quick thought that could maybe get other people to think of a better method.

---

