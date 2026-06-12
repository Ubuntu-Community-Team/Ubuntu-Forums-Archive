---
title: "Error while trying to Empy trashcan."
date: 2008-02-14
forum: General Help
---

### Post by Crafty Kisses on 2008-02-14
So I was trying to empy my trashcan, I downloaded Photoshop CS2, I decided I didn't want it, and I deleted it, and then when I tried to empty my trashcan, I got the following error:

```
**Error while deleting.**
```
```
"/home/code...snl_NL.dll" cannot be deleted because you do not have permissions to modify its parent folder.
```

I've tried numerous things, but they havn't worked, any ideas? Thanks!

---

### Post by Crafty Kisses on 2008-02-14
> **Codename said:**
> So I was trying to empy my trashcan, I downloaded Photoshop CS2, I decided I didn't want it, and I deleted it, and then when I tried to empty my trashcan, I got the following error:

```
**Error while deleting.**
```
```
"/home/code...snl_NL.dll" cannot be deleted because you do not have permissions to modify its parent folder.
```

I've tried numerous things, but they havn't worked, any ideas? Thanks!

Bump.

---

### Post by AsoSako on 2008-02-14
-Do Alt+F2
-Type gksudo nautilus and enter your password
-You should now be in your root folder
-Navigate to your home folder and enter the hidden folder .Trash (To view hidden files and folders do Ctrl+H)
-Delete the files
-Go back to the Root folder
-There is a .Trash in there as well if it doesn't show try Ctrl+H again
-Now delete the files from there as well
-They should be gone for good at this point

Hope this helps...

---

### Post by Crafty Kisses on 2008-02-14
Hmmm, that's weird I tried this before you suggested this, but when I retried it, it worked, well thanks!

---

### Post by AsoSako on 2008-02-14
Glad I could help.

---

