---
title: "cdrom permissions"
date: 2007-07-30
forum: General Help
---

### Post by woodcrusher on 2007-07-30
Hello Forum 

I am quite new to ubuntu and i have solved most of my problems but now i have one that seems to be a little tricky.  Here is my problem when ever i create a new folder on the cdrom for files i intend to put there well the folder is there no prob but i can't put any files.  It says i can not write to it because it is read only. i have tried sudo chmod 777 /media/cdrom to no avail here is the output of ls -l /media  

total 8
lrwxrwxrwx 1 root root     6 2007-07-10 13:30 cdrom -> cdrom0
dr-xrwxrwx 2 root larry 4096 2007-07-10 13:30 cdrom0
lrwxrwxrwx 1 root root     7 2007-07-10 13:30 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2007-07-10 13:30 floppy0

oh i guess i should say i am running feisty.

---

### Post by eggdeng on 2007-07-30
Sorry if I have completely misunderstood your post, but are you trying to copy files directly to a cd (as you would to a floppy) without using a burning application??
If this is the case try getting hold of a cd burning app
```
sudo apt-get install gnomebaker
``` for gnome
or
```
sudo apt-get install k3b
``` for kde
Again, apologies if I have misread your post. If I have, are you sure you are using a good writeable cd?

---

### Post by gentine on 2007-07-30
Unlike windows, you cannot place files onto the cd and burn them, you have to use a bruning applacation.

---

### Post by woodcrusher on 2007-07-30
No you did'nt misunderstand i am so used to windows that i thought i could put files on a cd the sameway obviously i can't. But after reading these posts i think i can figure it out now.  Thanks guys for all your help.

---

