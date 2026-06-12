---
title: "using raring.. unity's Files interface... how to work with ???"
date: 2013-09-27
forum: General Help
---

### Post by YannosB on 2013-09-27
Still a bit new at Linux, and am on  unbuntu raring box... all the updates current.
 My problem, being from a windows world.. is I have not discovered how to do file/folder operations in the Desktop interface (unable to get permissions out side of the /Home environments). Trying to delete an install folder in the term. is just ungodly! have to traverse each dir. del each file, return, del dir...(cause rmdir won't delete a non-empty dir) with a program install with over fifty folders... is just insane:confused:!
 So, can some one point this poor newb in the right direction!!! Please!!! day's of man, help files, and documentations have not given me insight....
 my logon is as administrator, if that helps.:popcorn:

---

### Post by deadflowr on 2013-09-27
So how did you install the program(s), and what makes you think deleting files and folder will help?
If you used the normal installation procedures, you would be able to remove the installation files with
```
sudo apt-get clean
```
To remove a package rather then an installation file
```
sudo apt-get purge packagename
```

Simply deleting files leaves nothing but a giant mess, as most packages have files scattered all over.

---

### Post by YannosB on 2013-09-27
thanks for the reply... however as we all know not all apps are fully cleaned with uninstalls. This one, in fact was a manual install (ie non apt-get).
 My question remains, how does one,using the desktop interface, get around to doing routine file/folder maint.? Surely linux is not stonewall bound to the terminal to do these thing?!

---

### Post by mikewhatever on 2013-09-28
Launch Nautilus (the file browser) as admin, and delete whatever you want.
```
gksu nautilus
```

You can also use 'sudo rm -r /folder-name'. Note the '-r' flag, that's how you delete none empty folders.

Do be careful with those. Deleting a lot of stuff outside your home folder is usually not a good idea.

---

### Post by oldos2er on 2013-09-28
> **YannosB said:**
> thanks for the reply... however as we all know not all apps are fully cleaned with uninstalls. This one, in fact was a manual install (ie non apt-get).

How *exactly* did you install this program? No one can give you a precise answer without precise details.

---

### Post by YannosB on 2013-10-14
I posted a manual install.. ie: an un-arc into proper app folder where all files ana structure are init on first run. Uninstall is reverse, ie: manual removal of file structure.... 

BTW Thanks to [mikewhatever] for two clear and swift solutions....
 ..sorry for long delay was in hospital for .. too long!

---

