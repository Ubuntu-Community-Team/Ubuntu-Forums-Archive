---
title: "move all files from all folders into another folder?"
date: 2014-10-18
forum: General Help
---

### Post by sohlinux on 2014-10-18
Hello, I have 790 folders , all folders have files inside, how can I move all files from all 790 folders into another folder called allfiles? I mean just the files not the folders. thanks

and if possible if some files have the same name it will rename them. thanks

---

### Post by O9aIevckc0 on 2014-10-18
first to remove all duplicate copies of data
 cd  to the directory then run 

fdupes -rdN .


if you dont have fdupes installed then 
apt-get install fdupes


next run 

find -type f -exec mv -nt '/full/pathto/desiredfolder'  {} \;

replaceing /full/pathto/desiredfolder whith the full path to the folder you want to put everything in to

next to remove any empty folders  run 

find -exec rmdir -p {} \;

there may still be some files left but unless you want to overwrite other files with the same name you will have to rename them first

mark this thread solved if this solves your problem

---

### Post by nerdtron on 2014-10-18
And be sure the the destination folder is not under the source folder when you run the find command. Just to be sure...

---

### Post by sohlinux on 2014-10-19
perfect. thanks :)

---

