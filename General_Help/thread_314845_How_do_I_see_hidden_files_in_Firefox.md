---
title: "How do I see hidden files in Firefox?"
date: 2006-12-08
forum: General Help
---

### Post by gargoyle on 2006-12-08
How do I see hidden files in Firefox?
Example.
The bookmarks are kept in a hidden file.

I would like to be able to view the bookmarks.

Is there something I can change to be able to view them?

Ubuntu Dapper
Firefox 1.5.0.3

---

### Post by ahaslam on 2006-12-08
Right-click in the dir/file list & select 'Show Hidden Files'

Tony ;)

---

### Post by CatKiller on 2006-12-08
I don't really understand the question. But you can view hidden files in the Open File... dialogue by right-clicking and selecting Show _H_idden Files.

---

### Post by yopnono on 2006-12-08
Don't know exactly what you mean, but if it's the FX profile folder, then open your home dir and CTRL+H to show hidden files folders.

Then look for the folder called ".mozilla" there you have all the file etc, for firefox

---

### Post by rlozano on 2006-12-08
or from the terminal you can issue a command:

ls -a or ls -al or ls -alh

---

### Post by gargoyle on 2006-12-08
Thanks that was just what I was looking for.  I had tried that before but I was clicking on the left panel not the right panel in the open file window.

I just wonder why they choose to place the profile in a hidden directory? I would think that a standard directory would be the logical place.

Thanks for the replies and the useful information.

---

### Post by strabes on 2006-12-08
why are your bookmarks in a hidden folder anyway? jw

---

### Post by thomashauk on 2006-12-08
So you don't accidentally delete them.
So it heeps out the way of the rest of your home file stucture.
Tradition.
Hundreds of reasons!

But if you want it visible just do a ```
ln -s .mozilla Mozilla
``` or something

---

