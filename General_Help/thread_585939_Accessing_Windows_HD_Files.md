---
title: "Accessing Windows HD Files"
date: 2007-10-21
forum: General Help
---

### Post by puner on 2007-10-21
Hi,

I can access my windows files (music, videos, pictures) fine with ubuntu (7.1) but only after i put the password in.

This means when i want to load my music in Banshee, my music wont display until i put the password in.

Is there a solution to auto-logging into the WinXp before I do anything?

---

### Post by prince_niceguy on 2007-10-21
are you using ntfs-3g...

can you put the out put of the following command

$ more /etc/fstab

looking at fstab we can make out what is the problem.

---

### Post by puner on 2007-10-22
When i put that command into terminal get, Bash, command not found....

It's not really a problem, more like extra security.

Does this happen for you to?

---

### Post by prince_niceguy on 2007-10-22
command "more" is present by default... i not get this problem.

I am sure you wouldn't have put the $ in the command but just recheck the same... just type the following

more /etc/fstab 

if that gives some security reasons then type

sudo more /etc/fstab

that should give some output...

---

### Post by puner on 2007-10-22
Here is what came up, I can't really interpret that haha

[[IMG]http://imagenerd.com/thumbnails/th_screenshot-puner-puner-desktop:-~Mrcx.png[/IMG]](http://imagenerd.com/show.php?_img=screenshot-puner-puner-desktop:-~Mrcx.png)

---

### Post by prince_niceguy on 2007-10-22
apparently you ntfs drive is not there in the fstab.

can you install gparted from synaptic and then put the screen shot of the same. will let you know what change need to be done in the fstab to get your ntfs drive read write wihtout password.

---

### Post by puner on 2007-10-22
Apparently its a WMD :P

[[IMG]http://img81.imageshack.us/img81/6316/screenshotgpartedzg2.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotgpartedzg2.png)

---

### Post by prince_niceguy on 2007-10-22
run the following command.

sudo gparted

---

### Post by puner on 2007-10-22
Its stuck on this:

[[IMG]http://img87.imageshack.us/img87/6463/screenshotzs4.th.png[/IMG]](http://img87.imageshack.us/my.php?image=screenshotzs4.png)

Never stops scanning...

---

### Post by prince_niceguy on 2007-10-23
OK... seems some problem...

can you run gparted from the live CD and then take a screen shot and send it... 

BTW are you using gutsy? if yes, then it should have detected the drives and made it read write by itself.

---

