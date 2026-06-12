---
title: "Problem with &quot;quit&quot; utility"
date: 2008-02-27
forum: General Help
---

### Post by MadMax08 on 2008-02-27
hey all,
for some reason, in my "quit" button on my panel, i have all my options for loggin out, switching users, etc. but no "shutdown" button. it seems to have disappeared. any idea on how to get that back? i've been getting by by going to "log out" and then "shutdown" from the login screen,,...but thats a few extra steps that i would rather not take.

any help is appreciated!

---

### Post by Nameless_one on 2008-02-27
I don't know how to restore the button, but in the meantime you can run 
```
sudo shutdown -h 0
``` 
in a terminal. That will halt your computer. Running it in the Alt+F2 prompt might work too, but you're better off with the terminal.

---

