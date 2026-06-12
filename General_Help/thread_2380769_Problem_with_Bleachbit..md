---
title: "Problem with Bleachbit."
date: 2017-12-21
forum: General Help
---

### Post by Hewjr100 on 2017-12-21
Hello everyone, I am having a problem with Bleachbit and I hope someone can help.  I removed Chromium and Google Chrome from ubuntu 16.04, but I cannot seem to remove them from the list of apps in Bleachbit.  I tried removing Bleachbit to include running autoremove and clean but nothing works.  I don’t like having things show up where they no longer belong.  Any help would be nice.
 
 
 Henry

---

### Post by vasa1 on 2017-12-21
Do you still have *~/.cache/google-chrome*, for example? I think that this folder will persist even after Google Chrome has been purged from the system. If you don't have Google Chrome installed, you can safely manually delete the folder. Then see what bleachbit says.

---

### Post by Hewjr100 on 2017-12-21
Trying it now.

Henry

---

### Post by Hewjr100 on 2017-12-21
No it must be gone.  I did check all boxes under google chrome in bleachbit and cleaned it.  Just don't get it, wierd huh?

Henry

---

### Post by VMC on 2017-12-21
You still have them in one of your ~/home folders. Check .cache and .config.

---

### Post by yetimon_64 on 2017-12-21
I just checked bleachbit here and noted chromium was still listed as available for cleaning; I had previously purged it.
So I had the same situation as you with bleachbit check boxes remaining for that program. 

To get rid of them from bleachbit open ~/.config/bleachbit/bleachbit.ini and remove any chromium and google-chrome related lines from there (edit: save the file) and then relaunch bleachbit. Doing that here removed the checkboxes for chromium.

Edit2: the leftovers here were only in the bleachbit.ini file. No directories existed here in either ~/.cache or ~/.config for chromium while it still showed up in the bleachbit interface.

---

### Post by ajgreeny on 2017-12-22
When you remove any package from your system, even if you purge it and all its system configuration folders and files, nothing that is in your home will be removed, so as an example, for chromium, you will probably have many hundreds of files in **~/.cache** and **~/.config** which you will have to remove manually, if you wish.

The same will be true for google-chrome but as I have never used it I do not know the details of the location of its files; probably exactly the same as chromium so have a look in .cache and .config.

To see full details of what is left in your home try commands ```
sudo updatedb
locate chromium | grep $USER
``` and you will probably see as lot of output, all in **.cache** and **.config**

---

### Post by Hewjr100 on 2017-12-22
Ok got it.  It was in /.cache, back to normal thanks

Henry

---

