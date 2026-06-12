---
title: "How to copy folder structure without folder contents ?"
date: 2020-11-14
forum: General Help
---

### Post by bauton on 2020-11-14
Hello and thank you in advance
 I hope you can help me. I'm dual booting and I have a absolute mess of pictures and videos under three large folders 2018, 2019 and 2020 and then divided up by months within those years.

At this point I want to just copy over the structure without all the contents. -

Note that the folders are in windows partition. 

in a perfect world you know of a GUI that I can use to copy the whole file  structure onto a thumb drive. that way I can put it on another computer where it will all ultimately end up. I really don't want to mess with the command line I've already dinked around with that on the Windows side for a while only ending in frustration.

---

### Post by ActionParsnip on 2020-11-14
[https://stackoverflow.com/questions/14352290/listing-only-directories-using-ls-in-bash](https://stackoverflow.com/questions/14352290/listing-only-directories-using-ls-in-bash)
Gives a good starting point

---

### Post by sisco311 on 2020-11-14
It's relatively easy to do it in BASH. Check out BashFAQ #10 (link in my signature).

---

### Post by col48 on 2020-11-14
bauton, welcome to the forum.

Of course, the two replies above use the command line, but don't shy away from it.  The help and man assistance make it much more friendly (usually!) than Windows used to be when I was a Windows user.
The solution cisco offers amounts to this, in 3 steps. (1) go to the top of the folder tree whose structure you want to copy (2) get a list of all the folders, remembering their place in the structure (3) feed this list into cpio which recreates the folder tree at the nominated destination.

If you are nervous, try it out on a small scale first, perhaps creating a brand new destination folder for the purpose.  I know I would!

---

### Post by TheFu on 2020-11-14
I would use **find** with **mkdir -p**
[LIST=1]
[*]cd {top of directory structure to be cloned}; # being in the directory is ABSOLUTELY critical.
[*]find . -type d -print -exec mkdir -p "$TARGET/{}" \;
[/LIST] find - exec can be slow.  Usually, I'd use xargs with it, but I didn't feel like looking up how to use xargs where their wasn't a space in the $TARGET/{} part.

Or I'd check gnutar for a way to create a tar archive with just directories (tar cvf), no files, do that, then de-tar (tar xvf) in the new directory area. I don't know if this is possible or not.  5 minutes of google. [https://stackoverflow.com/questions/12057925/tar-only-the-directory-structure](https://stackoverflow.com/questions/12057925/tar-only-the-directory-structure)

Or I'd just use **rsync** to clone everything, but limit the size of all files to 4K or less.  I know rsync has an option to restrict by file size. Generally, I use it to prevent getting huge (2GB+) files, but it could be useful for this. [https://www.cyberciti.biz/faq/unix-linux-bsdosx-copying-directory-structures-trees-rsync/](https://www.cyberciti.biz/faq/unix-linux-bsdosx-copying-directory-structures-trees-rsync/)

Those are off the top of my head.  I didn't test any. I'd setup a 2-20 directory test area to play and test.

---

