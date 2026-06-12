---
title: "How to Execute a Shell Command in PHP that requires root acceess"
date: 2008-03-30
forum: General Help
---

### Post by hvshah69 on 2008-03-30
I would like to execute ```
sudo /etc/init.d/tor reload
``` with PHP script called from a **web client**.

Since this command prompts for a root  passwd, I modified the sudoers to allow NOPASSWD access to the file owner. 

The php script works if I run it from the command line interface (CLI) (when I am logged in as the file owner). However, when I call the script from a web browser, the command is not executed. 

What am I missing ?

:confused:

EDIT: My sudoer entry is as follows

```
*username* ALL = (ALL) NOPASSWD: /etc/init.d/tor
```

---

### Post by hvshah69 on 2008-04-02
Bump.

I am sure someone knows answer to this.

---

### Post by Whiffle on 2008-04-02
I don't know any PHP, but what does the line look like that you're using to call the script from?

---

### Post by #Reistlehr- on 2008-04-02
need to see a snippet of the code before i can tell you any suggestions

---

