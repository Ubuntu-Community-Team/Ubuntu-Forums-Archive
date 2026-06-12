---
title: "shared libraries erro"
date: 2008-03-21
forum: General Help
---

### Post by ima998 on 2008-03-21
hi i get this error 

imantha@imantha:~/rcsoccersim/rcssserver3D/app/boldhearts$ ./boldhearts ./boldhearts: error while loading shared libraries: liboxygen_debug.so.3: cannot open shared object file: No such file or directory


liboxygen_debug.so.3  file is in /usr/local/lib folder and I have set the LD_LIBRARY_PATH as well

imantha@imantha:~/rcsoccersim/rcssserver3D/app/boldhearts$ echo $LD_LIBRARY_PATH
/usr/local/lib


any help is much appriciated

-ima

---

### Post by ad_267 on 2008-03-21
Check that liboxygen_debug.so.3 is pointing to a file that exists if it's a symbolic link

---

### Post by ima998 on 2008-03-21
sorry im very new to linux,

how can i see whare it is pointing
-thanks

---

### Post by ima998 on 2008-03-21
solved,

actually mu ld_path was wrong i fixed it now its working
thanks for the help guys
-ima

---

