---
title: "How does one browse to a driver on the desktop via the console?"
date: 2007-05-01
forum: General Help
---

### Post by Jonathan123 on 2007-05-01
So how do you browse to the desktop via the console?

I tried stuff like /home/<myusername>/desktop/<filename> and it doesn't work

The Nvidia driver is on the desktop, but how can I browse to it or get the root to be desktop?  I had it like that before, where "desktop$" was already entered each time, and all I had to was enter the name of the file to start it?

---

### Post by tkjacobsen on 2007-05-01
Try with 'Desktop' -- With capital D

---

### Post by strabes on 2007-05-01
cd ~/Desktop

---

### Post by jfinkels on 2007-05-01
Some other helpful hints:

You can type the command 
```

ls

```
(that's a letter L and a letter S) to list the contents of your current folder. 

You can type the command:
```

pwd

```
to Print your current Working Directory.

You can type the command ```
cd ..
```
to change to the directory above your current directory.

You can type a partial filename and then press "tab" and bash (the program that allows you to internet with the system from within the terminal) will automatically present you with options for the completion of that filename (or command name or whatever).

---

### Post by Jonathan123 on 2007-05-01
Thanks :)

---

