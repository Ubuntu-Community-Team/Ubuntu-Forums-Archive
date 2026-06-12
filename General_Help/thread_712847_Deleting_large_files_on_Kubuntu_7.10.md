---
title: "Deleting large files on Kubuntu 7.10"
date: 2008-03-02
forum: General Help
---

### Post by TWO on 2008-03-02
I'm currently using Kubuntu Gutsy and I've found that when attempting to delete large files, for example a downloaded .iso file, a 'deleting file' dialogue window opens but it freezes rather than delete the file. This isn't an issue in Ubuntu Gutsy, where such a large file is deleted instantly. 

Does anyone else experience this problem?

Thanks in advance

TWO

---

### Post by jeffus_il on 2008-03-02
If you are sure that you want to get rid of the file and don't need it in the trash can, find the delete command, in Nautilus it can be added to the menu, and thunar has a shift->delete to bypass the trash. Have seen problems like this due to huge folders with tens of thousands of files and really full trash, Have a look at your folders for surprises.

---

### Post by Robin T Cox on 2008-03-02
I've experienced the problem in the past, too. One way that I've been able to delete a large file successfully is by using a live CD version, and booting the OS from it. Then you can view your hard drive from the CD OS and delete the file.

---

### Post by TWO on 2008-03-02
> **jeffus_il said:**
> If you are sure that you want to get rid of the file and don't need it in the trash can, find the delete command, in Nautilus it can be added to the menu, and thunar has a shift->delete to bypass the trash. Have seen problems like this due to huge folders with tens of thousands of files and really full trash, Have a look at your folders for surprises.

I suppose that you mean I can remove it by using the 'rm' command in the Terminal/ Konsole? I'm using  Dolphin/ Konqueror as my file browsers since I'm using Kubuntu. I'm still getting use to it since I only switched from Ubuntu a fortnight ago. 

But would you- or anyone else- know how to enable that feature in Kubuntu's window manager(s)?

Thanks in advance

TWO

---

### Post by jeffus_il on 2008-03-02
Try rm in a terminal and see if it speeds things up. I am sure that Dolphin has a way to delete and bypass trash. Have a look in the preferences menu.

---

### Post by emunch on 2008-03-02
TWO,

I was experiencing something similar with SuSE few months ago. I was having problems if I were directly deleting files or emptying the Trash. Basically, when it was doing the "deleting" it was taking a lot longer the it was supposed to. When you run the "rm" you may end up with the same wait time. Have u tried already? 

If with "rm" it still takes long time to delete the files, I believe it has something to do with the chipset drivers. Because I just experience this with my NVDIA Chipset board with SATA II drives. All other boards and regular IDE drives does not give me any problem.

---

### Post by TWO on 2008-03-06
> **emunch said:**
> TWO,

I was experiencing something similar with SuSE few months ago. I was having problems if I were directly deleting files or emptying the Trash. Basically, when it was doing the "deleting" it was taking a lot longer the it was supposed to. When you run the "rm" you may end up with the same wait time. Have u tried already? 

If with "rm" it still takes long time to delete the files, I believe it has something to do with the chipset drivers. Because I just experience this with my NVDIA Chipset board with SATA II drives. All other boards and regular IDE drives does not give me any problem.

I just tried the using the rm command as as far as I could tell it didn't take as long to delete as using the normal function. Saying that, I'm not too sure since the window didn't refresh after having used the command. I had to press f5 to see whether the file had been removed.

---

### Post by foldor on 2008-03-10
Yeah I had the same issue today, and  what worked for me was using shift+delete. This deletes it and skips the trash bin.

Hope this works for you.

---

