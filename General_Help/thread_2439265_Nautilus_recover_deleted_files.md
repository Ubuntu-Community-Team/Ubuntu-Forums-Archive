---
title: "Nautilus: recover deleted files?"
date: 2020-03-25
forum: General Help
---

### Post by dmikulec on 2020-03-25
Hi!  Bit of indigestion here regarding Nautilus.  I had created "bookmark" --> ~/bookmark/file.  I thought  "bookmark" was just a link.  There were many other files in the directory.  I deleted "bookmark" in Nautilus with the delete key.  Now, the only file in the directory tree is ~/bookmark/file.  <ctrl>z in Nautilus does not work to undo the change.  The files are not in ~/.local/share/Trash.  Any thoughts on how to recover the missing files?

I'm running Ubuntu 14.04 Hi!  Bit of indigestion here regarding Nautilus.  I had created "bookmark" --> ~/bookmark/file.  I thought  "bookmark" was just a link.  There were many other files in the directory.  I deleted "bookmark" in Nautilus with the delete key.  Now, the only file in the directory tree is ~/bookmark/file.  <ctrl>z in Nautilus does not work to undo the change.  The files are not in ~/.local/share/Trash.  Any thoughts on how to recover the missing files?

I'm running Ubuntu 14.04 libgnome2-comm 2.32.1-4ubun

---

### Post by yancek on 2020-03-25
>   The files are not in ~/.local/share/Trash. 

You will have an option to send to Trash and an option to delete which are different so that if you select 'delete', the files will be deleted and not sent to trash.  You could try downloading Testdisk from the link below and using it.  I would suggest you give the instructions a thorough read before beginning.

[https://vitux.com/how-to-recover-deleted-files-in-ubuntu-through-testdisk/](https://vitux.com/how-to-recover-deleted-files-in-ubuntu-through-testdisk/)

---

### Post by Impavidus on 2020-03-25
It's not entirely clear to me. Did you create a bookmark named "bookmark" that pointed to a file in a directory also called "bookmark"? I can't say whether your files are really gone or just in some place where you didn't expect them to be. But I never use Nautilus or bookmarks.

But the real reason why I post here is that Ubuntu 14.04 reached end of life a year ago. After you recovered your files (if you manage that; they could be really gone), prepare for a fresh install of 18.04 or 19.10.

---

### Post by TheFu on 2020-03-25
+1 to moving off an unsupported release. Move to 18.04.

As for understanding **symbolic links**, wikipedia is a good source: [https://en.wikipedia.org/wiki/Symbolic_links](https://en.wikipedia.org/wiki/Symbolic_links)
I have ZERO idea about nautilus.  I don't really use GUIs for file management due to unforeseen surprises, as you've learned.

Heck, the current version of Nautilus might look and work completely different.  [https://wiki.gnome.org/Apps/Files](https://wiki.gnome.org/Apps/Files)  They've even renamed it completely.

---

### Post by HermanAB on 2020-03-26
Hmm, this should help for next time:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

