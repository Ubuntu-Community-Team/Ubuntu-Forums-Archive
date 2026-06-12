---
title: "only one software mangemant too [HELP]"
date: 2006-10-13
forum: General Help
---

### Post by ww2airborne on 2006-10-13
in the top panel a popup will popup in the corner saying that i need to install software updates im sure you all have seen that before

i click on it to up date my software and an error box will say
"only one software managemnt tool is allowed to run at the same time" 
"please close the other application e.g. 'aptitude' or 'Synaptic' first"

i close all my programs then tried it again and it still said that 
so i restarted and it still was there
then I shut it all down and when it booted up again it was still there


im new to linux so i could of done something wrong

if anyone know how to fix this can you please help

thanks :D

---

### Post by aysiu on 2006-10-13
Perhaps the updater itself is already running... somehow.

Can you try going to System > Preferences > Sessions and unchecking the box that says to save your session automatically at logout... then log out and log back in again?

---

### Post by ww2airborne on 2006-10-13
it didnt work
the thing you told me to uncheck was unchecked

---

### Post by aysiu on 2006-10-13
Darn.

Don't know what else to recommend. Anyone else?

---

### Post by ww2airborne on 2006-10-13
o  well if no one knows i guess i reinstall the OS the only thing i would have to install is Automatix and a few other programs

thanks for the help

---

### Post by aysiu on 2006-10-13
Before you do that, please file a bug report on this:
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by triplep on 2006-10-14
It sounds like /var/lib/dpkg/lock is in a bad state, I'd rm it, then touch it back into exsistance, giving it a new inode.

It appears to be master lock, above the /root/.synaptic/lock from the looks of strace output.

---

