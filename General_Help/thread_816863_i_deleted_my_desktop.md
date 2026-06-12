---
title: "i deleted my desktop"
date: 2008-06-03
forum: General Help
---

### Post by sprightlyone on 2008-06-03
hi 
  as you guessed i `m new & inexperienced 
 from previous posts in other categories i now know that uninstalling evolution (i changed to thunderbird) &wanted to get rid of evolution from the program list now i don`t have a desktop depend on each other 
 itried suggested cmd to reinstall desktop nothing happened 
 i seemed to have reinstalled evolution  but it didn`t change anything either 
 can someone suggest a fix to restore my desktop or how to do some checking to see what is loaded /working &what is not 
 thanks 
lyle

---

### Post by bigken on 2008-06-03
try this 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

---

### Post by sprightlyone on 2008-06-03
> **bigken said:**
> try this 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

run all the commands 1st 2 did a lot of installing 
 last cmd finished with "couldn`t find package ubuntu"
where to next ??? i don`t seem to be getting anywhere yet 
  lyle

---

### Post by Bubba64 on 2008-06-03
Once your back installed with bigkens instruction you can edit your menus to not show in dropdown by opening menu edit with a right click on application-edit menus and tick the program, and if you want to remove it completely from the menu right click on the program in edit menu and hit the delete, but personally I wouldn't remove it unless it had been removed from the computer.

---

### Post by Bubba64 on 2008-06-03
I think it is gnome-desktop that you want if you are running a stock release, but I could be wrong run the same update just gnome desktop instead of Ubuntu.

---

### Post by bigken on 2008-06-03
try** startx** at the promt

---

### Post by bigken on 2008-06-03
put the cd in the drive and try to run **sudo apt-get install ubuntu-desktop** again

---

### Post by sprightlyone on 2008-06-03
hi 
 i had a typo in my last attempt i tried again success at last i have my desktop back
  now i want some simple easy to follow instruction on what files i can remove &what must stay to avoid another disaster to remove evolution so i can use thunderbird instead 
 thanks to big ken for the reply that solved my problem:):):):):):)
lyle

---

### Post by Bubba64 on 2008-06-03
> **Bubba64 said:**
> Once your back installed with bigkens instruction you can edit your menus to not show in dropdown by opening menu edit with a right click on application-edit menus and tick the program, and if you want to remove it completely from the menu right click on the program in edit menu and hit the delete, but personally I wouldn't remove it unless it had been removed from the computer.

These instructions work for the menus if you want to remove the email do it in synaptic it will tell you when it will remove other stuff, you can partially remove the email package but menu editing or removal is what I would do.

---

### Post by bigken on 2008-06-03
its easy to remove evolution from the menus just right click programs and edit

---

### Post by sprightlyone on 2008-06-03
hi 
 i opened boot/grub/menu.lst in a terminal window to edit with AMD64 fix
how do i save &exit?????  can i delete duplicate entries?????? i would copy &paste if i could work out how to show you which i`m interested in 

 lyle

---

### Post by danwood76 on 2008-06-03
to edit the menu.lst in gedit type the following command in the terminal:
```

sudo gedit /boot/grub/menu.lst

```
Its best to leave duplicate entries in, they generally have different kernel versions and its sometimes useful to have a spare kernel just incase your main one gets borked somehow.

---

### Post by sprightlyone on 2008-06-03
hi 
 thanks to danwood76
 i fixed my boot to load without errors 
lyle

---

