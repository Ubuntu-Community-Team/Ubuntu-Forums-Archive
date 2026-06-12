---
title: "need help moving files with the terminal..."
date: 2006-10-24
forum: General Help
---

### Post by goosy22 on 2006-10-24
i am trying to get my belkin wireless adaptor to work, and to do that i need to move some files (located on the desktop) into the directory 'windows-drivers' located in 'filesystem'... i couldn't just cut and paste because it says i'm not the owner of the files... so i tried using the terminal window and every single line of code i put in i got this "file or directory doesn't exist" line... let it be know that i've been playing with ubuntu for 5 hours and i have no previous linux experience...

so here's what i would like, the code line that moves:

rt2500.sys
rt2500.inf
rt2500.cat
(all located on the desktop)

to the file 'windows-driver'
(located in the filesystem, or root folder)

thanks for all your help...

---

### Post by taurus on 2006-10-24
You probably need to do something like

```

cd ~/Desktop (Linux or Unix is case sensitive so Desktop is not the same as desktop...)
sudo cp * wherever_you_want_to_copy_to

```
Now, you need to know where you want to copy those files to since you need to replace the "wherever_you_want_to_copy_to" with the complete path of your destination directory...

---

### Post by goosy22 on 2006-10-24
k... thanks i will try that...

EDIT: thanks for the suggestions... i didn't know that linux was case sensitive and after i learned that i tried:

chris@chris-laptop:~$ sudo mv ~/Desktop/rt2500.sys /windows-drivers/

and that did the trick... thank you for you insight, it helped me out...

---

### Post by CatKiller on 2006-10-24
For the future, you can use Tab-completion for paths and filenames. Type the start and press Tab, and the computer will attempt to fill in the rest for you. Very handy.

---

### Post by threegremlins on 2006-10-24
you could also gksudo "filemanager" and move them as root

---

