---
title: "Loading uninstalled libraries"
date: 2007-12-03
forum: General Help
---

### Post by orlox on 2007-12-03
I'm trying to run a binary on a pc were I don't have root access, and when executing the binary, it gives me:

./ioquake3.i386: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

I downloades an rpm (this thing is on fedora) an extracted the lobopenal.so.0 library. Is there a way to run the program using this???

---

### Post by orlox on 2007-12-03
I ran ldd on the binary and checked that the only thing i'm missing is the libopenal library. Is there any way to load this withowt root access?????

---

### Post by Spudgun on 2007-12-04
No.

---

### Post by orlox on 2007-12-07
Actually, there is.

I discovered that if I have the .so, I can modify a variable so it can search for libraries on a specified directory. I just run the comand:

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<path>

Where path is the additional folder where you want the system to find libraries. After running this on a console, I simply execute the binay and it works perfectly.

---

