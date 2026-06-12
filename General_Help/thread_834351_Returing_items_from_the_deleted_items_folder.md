---
title: "Returing items from the deleted items folder"
date: 2008-06-19
forum: General Help
---

### Post by Dalston on 2008-06-19
Hello im running 8.04 and I want to restore some items from the deleted items folder back into their original folders.  Is there a way to do this like there is in xp?  thanks in advance

---

### Post by Exsecrabilus on 2008-06-19
[http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/](http://tombuntu.com/index.php/2008/04/09/recover-deleted-files-with-foremost/)

---

### Post by Butthead on 2008-06-19
Um, you mean the **Trash Can**, right?

Open up the Trash Can, and **Right** mouse click on deleted item, pick the "recover from trash can" option (or whatever it's called?) to put the thing you deleted (and want back now) where it originally was.

---

### Post by Dalston on 2008-06-19
Yeah I do mean trashcan but I dont get an option to recover.

---

### Post by Butthead on 2008-06-20
Hmm, even when you select it with the right mouse button? :confused:

That's strange! :(

---

### Post by drs305 on 2008-06-20
You can try (in Hardy):
```
mv ~/.local/share/Trash/files/filename ~/Desktop
```

If you have multiple files, you can use the wildcard symbol (*) for all or part of the name, and of course you can change the location to move the files to.

---

### Post by Dalston on 2008-06-22
Thanks for your help but what I was really after was a way to return the items to their original folders. As I dont know where the files came from.

---

### Post by drs305 on 2008-06-22
> **Dalston said:**
> Thanks for your help but what I was really after was a way to return the items to their original folders. As I dont know where the files came from.

In the trash folder ( ~/.local/share/Trash ) is a folder called *info*. That folder has an entry for each deleted item in the *files* folder. It contains the information you are looking for (origin of deleted folder or file).

It might even be possible to create a script that would automatically restore the files to their original location.

---

### Post by Dalston on 2008-06-23
Thanks so much, thats exactly what I was after.  Thats what I love about these forums you learn more everyday.

---

