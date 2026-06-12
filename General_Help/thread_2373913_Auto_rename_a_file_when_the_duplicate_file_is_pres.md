---
title: "Auto rename a file when the duplicate file is present"
date: 2017-10-10
forum: General Help
---

### Post by ramster2 on 2017-10-10
I used Mac in the past, and something I really like about it is that Mac will *automatically* rename a file if another one exists with the  same name.

For example:

If there is a file in a folder called  *somefile.txt* and you download or copy another file with the same name into that same folder, Mac will automatically rename the new file to  *somefile(1).txt*, allowing the 2 files to co-exist in the same folder without you having to  manually change either name.

Is there a way to make Ubuntu do this  automatically?

---

### Post by HermanAB on 2017-10-11
This behaviour depends on your file manager in Linux.  There are many and they all behave differently.  So install and try a bunch of them, maybe one will do what you want.

---

### Post by coffeecat on 2017-10-11
> **ramster2 said:**
> If there is a file in a folder called  *somefile.txt* and you download or copy another file with the same name into that same folder, Mac will automatically rename the new file to  *somefile(1).txt*, allowing the 2 files to co-exist in the same folder without you having to  manually change either name.

Is there a way to make Ubuntu do this  automatically?

That is exactly what Ubuntu with its default file manager "Files" does for downloads, but not for drag and drop copies. For the latter, if you do a drag and drop copy, you get a File Conflict popup window which allows you to rename the file as one of the choices. That's a little more elegant than having to rename before you do the copy and is useful for catching out inadvertent filename conflicts. Personally, I like it that way, with an automatic rename for downloads and more manual fine-grained control for copies, but it sounds as though that is not what you want. I don't believe there is a way of changing the behaviour in the Ubuntu file manager.  

But, as HermanAB says, there are other file managers which might behave as you wish. Each flavour of Ubuntu, Xubuntu, Lubuntu, and so on, comes with the file manager particular for that desktop environment, and most or all are installable in Ubuntu itself. I can tell you that Caja, the file manager for the Mate desktop, does the same as Ubuntu's Files with copies, but I haven't tested downloads.

---

