---
title: "Can't install Dungeon Defenders.."
date: 2012-12-22
forum: General Help
---

### Post by Jhall1108 on 2012-12-22
Hey, i'm trying to install Dungeon Defenders from the Humble Indie Bundle 7. Everytime i try to run it i get this error; 
noone-ubuntu:~/Desktop$ ./dundef.mojo.run
bash: ./dundef.mojo.run: No such file or directory

---

### Post by raja.genupula on 2012-12-22
are you sure about position of that file is there in Desktop itself ?

---

### Post by Jhall1108 on 2012-12-22
Yes I am. Its on my desktop; 
noone-ubuntu:~/Desktop$ ls
dundef.mojo.run
noone-ubuntu:~/Desktop$ ./dundef.mojo.run
bash: ./dundef.mojo.run: No such file or directory

---

### Post by oldos2er on 2012-12-23
Did you make it executable? ```
chmod +x dundef.mojo.run
```

---

### Post by kkovacs2 on 2013-12-22
Happened to me too. Chances are, you're running a 64-bit OS, like I do.

After looking at the binary with objdump, I installed the 32-bit libc libraries with:

[FONT=courier new]apt-get install libc6:i386[/FONT]

Hopefully this helps other people out there too.

---

### Post by oldos2er on 2013-12-22
Old thread closed.

---

