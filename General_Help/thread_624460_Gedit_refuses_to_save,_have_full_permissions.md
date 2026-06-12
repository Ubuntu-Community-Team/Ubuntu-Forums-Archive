---
title: "Gedit refuses to save, have full permissions"
date: 2007-11-27
forum: General Help
---

### Post by Crashmaxx on 2007-11-27
I have an ssh share mounted in /media and it works great. There is a public_html folder for my own little webpage and I'm adding to it for a school project.

All of the files in this folder are 644, or 755 and I'm the owner of them all. They open fine in gedit, but when I go to save my changes it says I don't have permissions to. So I checked them and as I said, I am the owner and I have full access. I do the same thing with nano and it saves fine. Any idea what is wrong here?

---

### Post by dpar on 2007-11-27
Are you doing the gksudo thing?

ie:> gksudo gedit 'path to file'

---

### Post by Crashmaxx on 2007-11-27
That would probably work, but I shouldn't need root to modify these files. I am the owner of the files and as I said nano can modify them without root, just not gedit.

EDIT: Tried it anyway, STILL can't save the modified file even with root privileges. Its definitely something with gedit. I think I need to file a bug.

---

### Post by kabads on 2008-03-12
I'm also getting this problem - perhaps it should be raised as a bug?

---

### Post by swiftsam on 2008-04-25
I have this problem all the time, and it still happens after upgrading to 8.04. I thought it was just me being stupid, but yeah, I think it's a bug

---

