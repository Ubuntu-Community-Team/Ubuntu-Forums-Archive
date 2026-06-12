---
title: "I try to get a Plane Shift .bin working and it doesnt work"
date: 2008-03-10
forum: General Help
---

### Post by jkreef on 2008-03-10
Like it says in the topic. It did nothing using the GUI so I went to terminal. Here are the commands and results I tried.
> joe@joe-laptop:~$ cd Desk*
joe@joe-laptop:~/Desktop$ ./PlaneShift*
bash: ./PlaneShift-v0.4.00-x86.bin: Permission denied
joe@joe-laptop:~/Desktop$ sudo ./PlaneShift*
sudo: ./PlaneShift-v0.4.00-x86.bin: command not found

I also tried Vega strike which is a .bz2.run and once again no luck with the GUI so here are the commands I tried.
> joe@joe-laptop:~/Desktop$ ./vegastrike*
bash: ./vegastrike-0.4.3-base.bz2.run: Permission denied
joe@joe-laptop:~/Desktop$ sudo ./vegastrike*
sudo: ./vegastrike-0.4.3-base.bz2.run: command not found
 
Thanks for any help!

---

### Post by taurus on 2008-03-10
You need to make sure the file has an executable permission before you run it.

```
cd ~/Desktop
chmod 755 PlaneShift-v0.4.00-x86.bin
./PlaneShift-v0.4.00-x86.bin
```

---

### Post by jkreef on 2008-03-10
BRILLIANT! Thanks for the help, it worked like a charm. Can I use the same commands but switch to filenames to the vegastrike file?

---

### Post by taurus on 2008-03-10
Yip.

---

### Post by jkreef on 2008-03-10
Thank you very much. *Adds to growing list of potential fixes* Thanks again.

---

