---
title: "Question about bash commands completion?"
date: 2015-07-07
forum: General Help
---

### Post by peter1897 on 2015-07-07
Is it possible, with a script or some other way, to implement this: When i press ctr+r and then type, for example, **s**, after this using the up and down arrow keys to go only through the commands in history that starts with **s**?

---

### Post by Plueonic on 2015-07-07
Create a the file .inputrc if it doesn't exist and put the following code in there
```
"\e[A":history-search-backward
"\e[B":history-search-forward

```
Just type in a letter or a command in a terminal and use the arrow keys as you normally would to search your bash history

---

### Post by peter1897 on 2015-07-07
Where i have to put the .inputrc file? I created the file in the user home directory but the completion by first letter of the commands doesn't work when i test it.

---

### Post by peter1897 on 2015-07-07
I also found a file inputrc in /etc/inputrc and inserted the two lines at the end of the file, but this also didn't work.

---

### Post by nerdtron on 2015-07-07
> **peter1897 said:**
> Is it possible, with a script or some other way, to implement this: When i press ctr+r and then type, for example, **s**, after this using the up and down arrow keys to go only through the commands in history that starts with **s**?

(pardon)
Doesn't Ctrl+r again to search backward and Ctrl+Shift+r to search forward on the history? Or I'll assume you really want the arrow keys?

---

### Post by peter1897 on 2015-07-07
I want to search only the commands that start with specific letter. Pressing ctrl+r again search all commands from history not only these that start with the specified letter.

---

### Post by peter1897 on 2015-07-07
Actually, it is working but without pressing ctrl+r, just typing the first letter and then using the arrow keys. I was trying to do this with first pressing ctrl+r. My mistake.

---

