---
title: "Error with trash bin"
date: 2007-10-03
forum: General Help
---

### Post by obloxeon on 2007-10-03
I looked and couldn't find the answer. This is more of a nuisense than anything, but whenever I go to "Empty Trash Bin" by clicking the trash container in Kubuntu, it will delete all my files like I would expect it to, but then I get an error popup:

"Error - KDE Panel

The file or folder /home/USERNAME/.local/share/Trash/files/picture.jpeg does not exist."

I check the trash bin and all the files are gone but it keeps popping up. Any suggestions on how to fix this?

---

### Post by ctschap on 2007-10-03
In a terminal session enter: 

sudo rm /home/USERNAME/.local/share/Trash/files/picture.jp

---

### Post by obloxeon on 2007-10-03
I appreciate the reply but the terminal says "No such file or directory" :(

---

### Post by por100pre1 on 2007-10-03
Try this:

```
rm -r ~/.local/share/Trash/info
```

```
mkdir ~/.local/share/Trash/info
```

---

### Post by obloxeon on 2007-10-03
THANK YOU por100pre1, the top piece of code worked perfectly. Thanks :)

---

