---
title: "why are terminal changes with Sudo Su not affecting my regualr user profile?"
date: 2008-06-11
forum: General Help
---

### Post by eival on 2008-06-11
im trying to change the ulimit -n

when i log in as Sudo Su and change the limit is there somethign else i have to type to save it? 

cause when i clost and reopen the terminal and run ulimit -a to check the settings its back to default 1024.

---

### Post by eival on 2008-06-11
okay i figured out this particular change that im making, reverts back to the default settings once i log out, so i need to know what authorizations to apply to my user so i can make that change.

so far ive set Set User Configerations and Manage System Configurations but i still cant change the ulimit as a normal user.

anyone know what authorisation covers that?

---

### Post by sdennie on 2008-06-11
I think the file you want to change is /etc/security/limits.conf.  The file is well documented.

---

### Post by wolfen69 on 2008-06-11
there is no need to log in as root. open a terminal as regular user and ```
sudo command
```  or gksudo if it a graphical app.

---

### Post by eival on 2008-06-12
i know HOW to change it, the terminal in hardy haron only lets sudo su make this change.

i just want to know why my normal user doesnt get changed.

if i check again as Sudo Su i see the change i made tho.

so apparently ill have to stay logged in as root all together :mad:

---

### Post by sdennie on 2008-06-12
Your normal user doesn't get changed because when you "sudo su", you are creating a child shell which inherits the parent shells environment.  When you type "exit" you return to the parent shell and any environment changes you made in the child are lost.  This is simply how Unix works.  An easy way to illustrate this is to start a terminal and do the following:

```

bash
export PS1=child:
exit

```

The best way to fix your problem is to edit /etc/security/limits.conf and set your user to have a higher open files limit.

---

