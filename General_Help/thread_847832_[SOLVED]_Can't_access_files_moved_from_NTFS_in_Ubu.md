---
title: "[SOLVED] Can't access files moved from NTFS? in Ubuntu?"
date: 2008-07-02
forum: General Help
---

### Post by Return Privacy on 2008-07-02
Hello all,
I setup Ubuntu 8.04 machine on wired home network. I moved some  files to the Ubuntu machine. I can see them fine, but I can't access them. They have a padlock on them. If I hit properties, it says that I am not the owner and I can't change the permissions. I moved them from a windows xp pro (NTFS) computer on the same network.  This doesn't happen when I move files to Ubuntu from the apple computer on the same network. I can access those files fine. 
Is there a way to "unlock" these NTFS files in UBuntu?
Thanks:confused:

---

### Post by Separ on 2008-07-02
Did you by any chance copy them over as root?

---

### Post by cariboo on 2008-07-02
You could try Alt-F2 and enter 

```
gksu nautilus
```

or you could open a terminal and change the ownership:

```
sudo chown user.user filename
```

where user is your username and filename is the name of the file.

Jim

---

### Post by Separ on 2008-07-02
You beat me to that lol, that was gonna be my next post :D

---

### Post by Return Privacy on 2008-07-03
Thank You Cariboo and Separ!

I did the terminal chown command that you gave and it took the "X" and lock icon off of the file in Ubuntu. I had moved the files over from a windows NTFS external hd connected to the windows xp machine to the ubuntu machine. 
Before your reply I tried everything I could think of. I copied the file back to the apple machine and back again, nothing. I tried copying it to the windows xp machine and back again, nothing. 
But, now I have the ability to read and write to the file. I have about 8 files total that I will have to do this with, now that I know how!

Thanks again for the amazingly quick help!!!!

---

