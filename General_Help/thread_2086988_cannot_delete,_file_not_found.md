---
title: "cannot delete, file not found"
date: 2012-11-22
forum: General Help
---

### Post by imagiz on 2012-11-22
hi,

i hope someone can solve this problem. 

i had a hard drive error earlier. when moving files between drives, one of them seemed to have malfunctioned. restarting the pc i found the destination folder had text files, and a SQLite 3 database instead of the folder containing video I was expecting. 

now, when i try to send them to the rubbish bin,  first it says cannot move them to the bin and must delete them. then it says it cannot delete: no such file or directory. 

so how can i get rid of them?!

any help would be most appreciated.

---

### Post by 0011235813 on 2012-11-22
> **imagiz said:**
> hi,

i hope someone can solve this problem. 

i had a hard drive error earlier. when moving files between drives, one of them seemed to have malfunctioned. restarting the pc i found the destination folder had text files, and a SQLite 3 database instead of the folder containing video I was expecting. 

now, when i try to send them to the rubbish bin,  first it says cannot move them to the bin and must delete them. then it says it cannot delete: no such file or directory. 

so how can i get rid of them?!

any help would be most appreciated.

You probably have to run as root to delete them. For a reason unknown to me, nautilus doesn't have a graphical way to be run as root, so you have to use the terminal, and run:
```

gksu nautilus

```
or kdesu dolphin if you're on a KDE system.

Try deleting them then. If it still don't work, you need to use shred.

First, navigate to the directory containing the dodgy files. You can do this with:
```

cd /name/of/directory

```
Obviously replacing the end with the name of your directory (for example, /media/HDD, or whatever it is — you can see the directory name by right clicking — 'properties' in nautilus). 

Then, the actual shred command:
```

shred *.txt *.sql

```
to delete all text and sql files. Or just shred the directory that contains the files.

---

### Post by imagiz on 2012-11-24
hey thanks for the reply. having trouble navigating to dir. i can get to media and ls show the drive. but when i go cd / media name, i get no such directory. 

i found someone mentioned bleachbit can shred files. using bleachbit, i managed to remove one of the recalcitrant files. so it finds the files to be done away with. when i press delete in its' file shredder, i just get a blank screen. 

so now i am going to take the long route, move stuff off the drive, format the drive, move it back.

---

### Post by 0011235813 on 2012-11-25
> **imagiz said:**
> **hey thanks for the reply. having trouble navigating to dir. i can get to media and ls show the drive. but when i go cd / media name, i get no such directory. **

i found someone mentioned bleachbit can shred files. using bleachbit, i managed to remove one of the recalcitrant files. so it finds the files to be done away with. when i press delete in its' file shredder, i just get a blank screen. 

so now i am going to take the long route, move stuff off the drive, format the drive, move it back.

I know what you mean... If the location contains spaces, you have to use backslashes (\) to replace the spaces. Also, once you've navigated to /media, don't use 'cd /location' when using cd – just ' cd location'. Why don't you post the output of ls so I can help you?

---

