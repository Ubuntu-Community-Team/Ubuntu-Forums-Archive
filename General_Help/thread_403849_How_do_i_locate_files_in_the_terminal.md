---
title: "How do i locate files in the terminal?"
date: 2007-04-07
forum: General Help
---

### Post by Booshibonton on 2007-04-07
hello, i'm trying o locate a file on my external hard drive but i cant seem to get to it. when i right click, go to properties, on the icon of the file i'm looking for on my external hard drive, it says the files location is /media/NewVolume. When i go into the terminal, and type /media/NewVolume, i get a message saying "/media/NewVolume: is a directory"...no duah :( ... how can i locate my file? (see the file in the terminal)

---

### Post by hikaricore on 2007-04-07
```
cd /media/NewVolume
```

---

### Post by Maestro23 on 2007-04-07
Try:

> cd /media/NewVolume

then

ls (list contents of directory)



---

### Post by solar george on 2007-04-07
If you just type in a file path the terminal thinks that you want to execute it (run it as a program), to view the contents of the directory use the command l
```
s *directoryname*
```
To change to another directory use the cd command
```
cd *directoryname*
```
If the file is a text file you can view it using less
```
less *filepath*
```

---

