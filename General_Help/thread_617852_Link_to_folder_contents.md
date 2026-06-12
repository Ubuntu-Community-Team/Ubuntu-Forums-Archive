---
title: "Link to folder contents"
date: 2007-11-19
forum: General Help
---

### Post by russell.h on 2007-11-19
If I had 2 folders at /data/Folder1 and /data/Folder2 is there a way for me to make a folder at /home/me/Documents that will display the contents of both Folder1 and Folder2 plus any files actually stored in Documents?

Basically the deal is I have some external hard drives, and I want files in certain folders on them to show up in my home folder when they are plugged in. But I don't want to have to create symlinks to each individual item on the hard drives, nor do I want to have to navigate into Documents/Folder1 and Documents/Folder2 in order to do stuff.

Thanks,

Russell

---

### Post by PeterJS on 2007-11-19
There's a tool called unionFS that does that. Knoppix uses it to layer the changes made to it's environment that are saved on a usb stick on top of the CD/DVD image. UnionFS is in the ubuntu repository. I couldn't find very good documentation on it, this is the best I could do:
[http://flaviostechnotalk.com/wordpress/index.php/2005/06/28/filesystem-snapshots-with-unionfs/](http://flaviostechnotalk.com/wordpress/index.php/2005/06/28/filesystem-snapshots-with-unionfs/)
Hopefully you can adapt that to your needs, or maybe the man pages are more useful. Good luck.

---

### Post by russell.h on 2007-11-19
Cool, thanks.

---

