---
title: "[SOLVED] can't delete files in trash"
date: 2008-05-23
forum: General Help
---

### Post by AvengingAngel718 on 2008-05-23
this is kind of a stupid problem, but i have files in my trash that i cant delete because they are owned by root for some reason. i cant figure out how to navigate to my trash as root using nautilus, it wont let me change permissions on the files, and it wont let me use the chown command.

how can i get rid of them?

---

### Post by reza81 on 2008-05-23
Go to the right path.

```

$ chmod 777 file name
$ rm file name

```

---

### Post by ibuclaw on 2008-05-23
Press **Alt+F2**, then type into the run app textbox:
```
gksu chown $LOGNAME ~/.local/share/Trash -R
```
Enter your password, then try emptying the trash.

Regards
Iain

---

### Post by sisco311 on 2008-05-23
[http://ubuntuforums.org/showpost.php?p=4800640&postcount=3](http://ubuntuforums.org/showpost.php?p=4800640&postcount=3)

---

### Post by Bubba64 on 2008-05-23
> **AvengingAngel718 said:**
> this is kind of a stupid problem, but i have files in my trash that i cant delete because they are owned by root for some reason. i cant figure out how to navigate to my trash as root using nautilus, it wont let me change permissions on the files, and it wont let me use the chown command.

how can i get rid of them?

Highlight the files then hold down shift then hit delete on the keyboard.

---

### Post by reza81 on 2008-05-23
> **tinivole said:**
> Press **Alt+F2**, then type into the run app textbox:
```
gksu chmod 777 ~/.local/share/Trash -R
```
Enter your password, then try emptying the trash.

Regards
Iain

You don't want your trash directory set on 777

only the files which cannot be deleted.

---

### Post by ibuclaw on 2008-05-23
> **reza81 said:**
> You don't want your trash directory set on 777

only the files which cannot be deleted.
Ok, should I have suggested chowning then?
```
sudo chown $LOGNAME ~/.local/share/Trash
```

Iain

---

### Post by AvengingAngel718 on 2008-05-25
ok i finally got around to taking care of it... thank you all for your assistance. i ended up using sisco311's method so now i actually know where my trash folder is located which is a good thing i guess

---

### Post by JS Lemming on 2008-07-22
> **reza81 said:**
> You don't want your trash directory set on 777

only the files which cannot be deleted.

Dang... I should have read further before acting. How do I undo setting my trash directory to 777?

---

### Post by NestoRotseN on 2009-01-13
yeah sisco311's way is easy follow, if you have ibex you can use the heron way, it works.

---

### Post by mysoogal on 2009-05-09
always having this stupid problem when i remove gallery2 , folders such as g2data always has permission issues and i need to restore put this folder back to desktop and sudo chmod to 777 and every single file using the * :(

its pretty stupid files don't lose its permission status when they enter the trash ! this is one of many things i really hate about Ubuntu ! why do i need permission to delete files from a Trash folder ???? its beyond believe ! i really cant understand it and i rather not understand what these crazy developers do ! maybe this is some type of a freaking joke ? who knows :confused:maybe they were high on permission crack.


just in case this worked for me 

 sudo rm -fr ~/.local/share/Trash/files/* > 

---

### Post by hyburn on 2010-01-25
yes thank you sisco

---

