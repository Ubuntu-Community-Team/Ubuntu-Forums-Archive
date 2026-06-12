---
title: "What do you use to make backups?"
date: 2005-04-06
forum: General Help
---

### Post by StrikeRTM on 2005-04-06
I had a simple idea to open the partition and rar all the files onto another partition. Since i'm not yet ready to let go windows i could put a backup of warty onto another partition from windows. So the obvious question is - how do i get to an etx3 Linux partition from windows and make a full partition copy?

Or is there another good way to do this?

Any idea or maybe someone can tell me how he does it :).

---

### Post by Leif on 2005-04-06
I'm not sure I understand what you're asking. What are you trying to backup, windows or warty ? The answer to the title question is rsync, btw.

---

### Post by StrikeRTM on 2005-04-06
I want to make a backup of warty and put the backup into the windows partition by using a program in win32. And if I do something wrong in warty, I cold just start windows and from there use backup to restore Linux.

---

### Post by Leif on 2005-04-06
Google says that you can mount ext3 drives using this :

[http://kennethhunt.com/archives/001314.html](http://kennethhunt.com/archives/001314.html)

and I think this one only does ext2:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

And this allows you to copy files too :

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

Good luck !

---

### Post by StrikeRTM on 2005-04-06
[QUOTE=Leif]Google says that you can mount ext3 drives using this :

[http://kennethhunt.com/archives/001314.html](http://kennethhunt.com/archives/001314.html)

and I think this one only does ext2:

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

And this allows you to copy files too :

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

Good luck ![/QUOTE]
I did search sf.net, but hdd backup were the wrong kay words i guess.

I have a system on ext3.

---

