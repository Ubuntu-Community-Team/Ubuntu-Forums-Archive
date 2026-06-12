---
title: "Permissions"
date: 2008-07-04
forum: General Help
---

### Post by Joseph_Schafer on 2008-07-04
ok, so here is the problem..

I used to have another partition, but moved all the files into another directory in my first partition.

BUT 

All the files are now root permission. I have tried the "Apply permissions to enclosed files" button, but i just cannot change the permissions to my other user, kit. 

Is there a chmod command or something? any help would be... helpful.

---

### Post by spiderbatdad on 2008-07-04
sounds like you want to chown the files; that is have the directory and the files in it owned by your user.

sudo chown -R username:username /path/to/directory

the -R flag is used to own the files recursively.

so if my username were bob, and I had a folder in my home directory named my_files, but it was root owned, I would:```
sudo chown -R bob:bob /home/bob/my_files
```

---

