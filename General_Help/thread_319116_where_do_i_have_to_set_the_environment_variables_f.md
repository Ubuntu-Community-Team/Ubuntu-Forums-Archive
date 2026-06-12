---
title: "where do i have to set the environment variables for non-interactive ssh sessions?"
date: 2006-12-15
forum: General Help
---

### Post by Batwomansman on 2006-12-15
hi,

i installed an application on an ubuntu live cd and set the corresponding environment variables in .bashrc. 

i can execute it remotely by logging in:


$ ssh user@server

user@server$ application

but i cannot execute it non-interactively.


$ ssh user@server application

command not found


which file do i have to modify?
who can help me?

thank you
batwomansman

---

### Post by dcstar on 2006-12-15
> **Batwomansman said:**
> hi,

i installed an application on an ubuntu live cd and set the corresponding environment variables in .bashrc. 

i can execute it remotely by logging in:


$ ssh user@server

user@server$ application

but i cannot execute it non-interactively.


$ ssh user@server application

command not found


which file do i have to modify?
who can help me?

thank you
batwomansman

Various "path" variables are set in an interactive session, you should use the explicit path to the application in your command line.

Find it with:
```
whereis application
```

---

