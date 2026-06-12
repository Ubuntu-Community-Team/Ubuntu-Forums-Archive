---
title: "Trash Can broken, how to remove trash files in terminal"
date: 2007-04-14
forum: General Help
---

### Post by keyo on 2007-04-14
I'm using feisty beta kubuntu.
My trash can won't empty and my trash's files folder( /home/..../Trash/files/ )has got out of sync with the links for the files to be deleted(/home/.../Trash/info/). How can i remove everything in the /Trash/files/ and /Trash/info/ folders with shh/terminal.
I tried the following but it didn't work because it's a folder
```
Sudo rm /home/ben/.local/.../Trash/
```

The easiest thing to do would be to delete the trash folder and then create a new trash folder with info and files inside it?

Please help, my linux partition is full :p

---

### Post by Maestro23 on 2007-04-14
Trash is a hidden(.Trash) directory in your home directory. 

> cd /home/username

ls -a (shows hidden directories/files)


---

### Post by keyo on 2007-04-14
My trash is definitly in /home/ben/.local/share/Trash/
I tried ```
 sudo rm /home/ben/.local/share/Trash/
``` and got
rm: cannot remove `/home/ben/.local/share/Trash/': Is a directory
Is there a different command to remove a dirrectory?

---

### Post by Maestro23 on 2007-04-14
> **keyo said:**
> My trash is definitly in /home/ben/.local/share/Trash/
I tried ```
 sudo rm /home/ben/.local/share/Trash/
``` and got
rm: cannot remove `/home/ben/.local/share/Trash/': Is a directory
Is there a different command to remove a dirrectory?

You don't want to delete the directory itself.  Just delete the files within.  Navigate to the directroy. 
> 
cd .Trash

sudo rm -r ....



rmdir is for directories.  You can check out the man page for it as well (man rmdir).

---

### Post by keyo on 2007-04-14
Thanks :D 
quick replies too ;)

---

### Post by derelict888 on 2007-10-16
I had a similar problem but I further complicated it   >_>

My linux partition ran out of space and the next time I restarted my computer I couldn't get into gnome. I booted into the recovery console and removed the .Trash directory for my profile, and then recreated the directory. That solved the initial problem, but now in gnome when I try to use the GUI to delete files off my desktop I get the following error:
```
Error while moving items to "/home/[user]/.Trash"
You do not have permissions to write to this folder
```

So I tried chown 644,755 that folder but that didn't fix anything. Can somebody help me out? What should my permissions be on that folder and could you please write out the command to change it? I'm not that savvy with linux yet  :(

-> As a side note I can delete items from a different partition (FAT32) from within gnome gui and those deleted files do show up in my trash and can be emptied.

---

