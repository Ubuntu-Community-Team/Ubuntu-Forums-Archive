---
title: "Deleteing a directory and all contents"
date: 2007-02-15
forum: General Help
---

### Post by mistypotato on 2007-02-15
Hi,

I am trying to delte a directory called /var/ossec that I created but need to change the type of install from local to server.

So I need to erase the entire folder (and all contents) and reinstall.

Problem is, It is telling me I dont have permission.  So I successfully changed ownership of the folder to my account but I still can't.  It seems the sub folders/files are still not under my ownership?

Is there a way to set all sub folders and files so that I can delete them with one command?

Thanks

---

### Post by bscbrit on 2007-02-15
If you doing it from the command line, you have to make chown recursive by using the -R option:

sudo chown -R newowner: /var/ossec

but why bother?, just use 

sudo rm -r /var/ossec

and then it is gone.

NB Always take care when using rm - one typing mistake can kill your system.

---

### Post by bscbrit on 2007-02-15
Sorry, that's only half the answer.

If you are changing permissions using nautilus (under sudo, to give you root access) then simply select the permissions on the relevant tab and click "Apply permissions to enclosed files".

---

