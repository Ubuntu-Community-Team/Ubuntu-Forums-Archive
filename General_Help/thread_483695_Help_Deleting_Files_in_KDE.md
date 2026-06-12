---
title: "Help Deleting Files in KDE"
date: 2007-06-25
forum: General Help
---

### Post by teabeartom on 2007-06-25
Hi,
I have an external hard drive that I store most of my data on.  I want to delete about 10 GB of files on there.  In konqueror, I right clicked, and I only have the option to move them to the trash.  I did this, but I only have 5 GB of free space on my computer hard drive, and for some reason it has to copy all of those files to /home/tom/.trash/ or some folder like that and told me that I didn't have enough disk space to delete those files off my external hard drive.  This doesn't make sense to me.  

Isn't there simply a way to delete the files off of my external hard drive???  Please, any help would be appreciated.  Thanks!

---

### Post by swisscow on 2007-06-25
You could try just deleting a few at a time, and emptying the recycle bin as you go along.

Or **in the directory** you could use ```
rm *.* 
```but this will dump everything and I'm pretty sure it bypasses the recycle bin **so be careful!**

---

### Post by Clay_Banger on 2007-06-25
select the folder that you want to delete, then press <Shift>+<Delete> that will bypass the trash bin.

---

### Post by teabeartom on 2007-06-25
Thank you so much!  The Shift + Delete did the trick!

---

