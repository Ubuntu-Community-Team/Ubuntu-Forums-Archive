---
title: "Startup commands"
date: 2005-11-02
forum: General Help
---

### Post by mad_alfred on 2005-11-02
Hi!

everytime i start ubuntu i need to execute some commands from the console like:

set | grep -i utf

export LANG=en_US.euro

export LC_CTYPE=en_US.euro

mount /dev/hdb1 /mnt/HD

etc...

is there a way i can make ubuntu do this for me as soon as i login gnome??

---

### Post by frodon on 2005-11-02
For your mount line, add a line like that in your /etc/fstab file (open it as root) : ```
/dev/hdb1 /media/HD auto rw,user,noauto 0 0
```For the other lines, create a bash script which run all your commands and add it in the gnome sessions, go to System > Preferences > Session in startup programs tab, click "add" and then add the path of the script.

---

### Post by mad_alfred on 2005-11-02
thanks!

you saved me from doing a pretty annoying task everytime i log in !:D

---

### Post by mad_alfred on 2005-11-02
sorry, one more problem.
this is how my bash file looks like:

#!/bin/bash
set | grep -i utf
export LANG=en_US.euro
export LC_CTYPE=en_US.euro
hdparm -d 1 /dev/dvdrw
mount /dev/hdb1 /mnt/HD

...these two commands seem ignored :
export LANG=en_US.euro
export LC_CTYPE=en_US.euro

how is it possible?
thanks for the support!:D

---

### Post by frodon on 2005-11-02
Does the 2 lines are useful only in terminal ?
If it's the case just add them in your .bashrc file, it's in your home directory

---

### Post by mad_alfred on 2005-11-02
i wouldn't know..i use them to start vdr to avoid the error message:

vdr: please turn off UTF-8 before starting VDR

---

### Post by frodon on 2005-11-02
it's strange, however if you add your 2 lines in your .bashrc files, the variable will be set automatically after you open a terminal.
I have no idea for the moment why it doen't work in your script.
Or i have another idea, you could create a script which set the good variables and then start vdr, then create an icon which launch this script and why not add it in the menu.

---

### Post by mad_alfred on 2005-11-02
I went for the first option, so i edited the .bashrc file and now it all works fine..thank you!!!!!!!!

---

