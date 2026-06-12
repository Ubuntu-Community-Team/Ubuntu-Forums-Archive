---
title: "Folder and content permissions"
date: 2008-04-26
forum: General Help
---

### Post by nami on 2008-04-26
I still can't get used to this permissions thing in linux.

I need to give myself full access to /var/www and everything inside it including sub directories and the content of sub directories.

How do I do that?

---

### Post by nami on 2008-04-26
I tried chmod 777 /var/www and it only game me full access to the files within www, but not for the sub folders.  How do I do that without doing the above command for each and every folder?

---

### Post by pietjanjaap on 2008-04-26
gksudo nautilus
Then you can change evething.
Don't change to much, is not always secure.

---

### Post by bribri124 on 2008-04-26
If you want full access to everything in /var/www, just do chmod -R 777.  I wouldn't recommend doing that can keep the permissions at 755, but I'm sure you have your reasons.

---

### Post by lordrick112 on 2008-04-26
Hello there.

You might want to try this.

Alt + F2 to open a run program dialog box, then enter "gksudo nautilus"

this will give you root access using your file manager.

I'm assuming your using ubuntu, the command is different for me using xubuntu which uses a different file manager. "gksudo thunar" gives me root access with the file manager.

Hope this helps you out!

---

### Post by nami on 2008-04-26
Basically, I want to allow aptana to read and write files to var/www and all subdirectories, and I want apache2 to have access to those folders too.  At the moment, those programs only have direct access to /var/www and non of the sub folders.

---

### Post by nami on 2008-04-26
> **bribri124 said:**
> If you want full access to everything in /var/www, just do chmod -R 777.  I wouldn't recommend doing that can keep the permissions at 755, but I'm sure you have your reasons.

chmod -R 755 /var/www worked.  Is that safe enough?

---

### Post by bribri124 on 2008-04-26
You should be fine with your permissions set at 755.  No one else will be able to modify your files.

---

