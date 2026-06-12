---
title: "ntfs-3g Read Write problems"
date: 2007-12-06
forum: General Help
---

### Post by ridetheteapot on 2007-12-06
Dunno, maybe someone else has experianced this problem

I am finding that any files created or altered using the ntfs-3g driver are undeletable in windows (at least in XP)

I use an external harddrive with ntfs for my music, i didnt releaze that gutsy had RW enabled by default and accedently dragged one folder into another then moved it back, but now i can't delete it (in windows, i can in linux). Also i deleted a few files in linux and then tried to get rid of the .Trash folder while the drive was hooked up to my windows machine and found that i could not....

i disabled write, but i am kind of worried that the 3g driver might mess up the file system...

---

### Post by szaka on 2007-12-06
The Windows error message should say why you're denied to remove files. There can be several reasons.

1. The given user doesn't have the permisson to do so. Then try to do it as the Administrator user.
2. Some Windows applications are buggy when they meet with valid POSIX files: [http://ntfs-3g.org/support.html#posixfilenames2](http://ntfs-3g.org/support.html#posixfilenames2) 
3. You can also have a character set conversion problem if you used national characters in the filenames.

---

### Post by ridetheteapot on 2008-02-27
its not that the files are read only, when in windows, and i doubt its character conversion problems, cause it happens to any file, also its files that have been there before (written by windows, moved or edited in linux), and i the standard US characters.
As for #2 i get this problem if i deleted something in linux (gdm) and it moves to mount/.Trash-user and then try to use explorer to delete the file in windows from .Trash...

I don't have any windows machines at the moment, So i can't really mess around with it anymore (but i still have the ntfs formatted external, which the 3g drivers dont have any problem with from machine to machine)

---

