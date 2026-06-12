---
title: "Privacy Alert-Temp Files Not Really Gone, Etc..."
date: 2007-06-06
forum: General Help
---

### Post by thehessian on 2007-06-06
Hey Guys,

I am a privacy and security nut, mainly because my life's work resides on my harddrive.

I have used Truecrypt with Forcefield, and it is great, but I have some issues with the way that Ubuntu stores Thumbnails of the documents, videos and books that I have opened, as well as recently opened files.

I've tried using the "Clear Recent Documents" function, but it doesn't really help all that much.

Are there any scripts that will clear the history of my computer usage?

Thanks,
Hessian

---

### Post by esavato on 2007-06-06
I clear the terminal with
```
history -c
```

then reset it and clear.  One thing to mention is that truecrypt does not guaranty true protection when you use a journaling file system (e.g. ext2/3 etc.).

---

### Post by thehessian on 2007-06-06
Thanks for the reply.

I am going to give Suse a try, because there is a full disk encryption program called compusec that would put my mind at ease!

Take Care,
Hessian

---

### Post by TDK800 on 2007-06-09
Greetings, here's a link to a post i made about various encryption methods researched, hope it's of help:

[http://ubuntuforums.org/showpost.php?p=2433247&postcount=2](http://ubuntuforums.org/showpost.php?p=2433247&postcount=2)

Without encryption the file erasing is according to specialists is not of much help, because when your adversaries get their hands on the harddrive, theoretically they can read anything off it that ever was there, no matter how many overwrites you've done.

BUMP! For adding a built-in full disk encryption to next Ubuntu :)

---

