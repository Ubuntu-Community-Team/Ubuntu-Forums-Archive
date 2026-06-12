---
title: "Unable to delete file from recycle bin"
date: 2006-12-17
forum: General Help
---

### Post by TimmyS on 2006-12-17
I am having a problem where I can not delete a folder containing several files from the recycle bin. When I first used the folder, I used the [COLOR="Red"]chmod 777[/COLOR] command so that I could execute a program that was inside the folder. I have now put the folder in the recycle bin, but I get the error message - "/home/timmy.../libhpi.so" cannot be deleted because you do not have permissions to modify its parent folder. Any suggestions?

---

### Post by firebadger on 2006-12-17
If you are really sure you want to delete the file, use sudo to execute the rm command as root.

---

### Post by NoNo_231 on 2006-12-17
From a terminal you can do

cd ~/.Trash
sudo chmod 777 -R name_of_the_folder

and then empty your trash bin
or more agressively

cd ~/.Trash
sudo rm -r name_of_the_folder

Be careful not to delete something you don't want to.

---

