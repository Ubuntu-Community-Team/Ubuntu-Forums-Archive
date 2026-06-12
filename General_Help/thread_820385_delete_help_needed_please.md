---
title: "delete help needed please"
date: 2008-06-06
forum: General Help
---

### Post by ekalfal on 2008-06-06
I am a new Linux user and need help. I recently went to Ubuntu and in the process saved files from my Windows installation. When I upgraded to ubuntu 8.04 I copied the files to my Home folder. That went great but when I was finished I sent them to the trash and now I can not delete them! I can not remove them from the trash bin either, they are simply stuck there. I have changed permissions, etc, for everything and still I can not empty the trash bin. How can I force this delete? Any help would be greatly appreciated! Thanx in advance, ekalfal

---

### Post by leito666 on 2008-06-06
[http://ubuntuforums.org/showthread.php?t=819971&highlight=trash](http://ubuntuforums.org/showthread.php?t=819971&highlight=trash)

[http://ubuntuforums.org/showthread.php?t=818511&highlight=trash](http://ubuntuforums.org/showthread.php?t=818511&highlight=trash)

---

### Post by ibutho on 2008-06-06
Try
```
sudo rm -rf /home/user/.Trash/*
```
Be careful when using "rm -rf" because it can cause permanent data loss if used incorrectly.

---

### Post by kamaji792 on 2008-06-06
For a safer delete try.
```
cd /home/<user name>/.Trash/
ls -a
   <list of files>
rm -f <file to delete>
```
Repeat the **rm** command for each file you want to delete.

All the best

---

### Post by ekalfal on 2008-06-06
I tried all the above mentioned methods and got no where. I still have the folders/files in the trash bin and can not remove them. Any more ideas?
Thanx.....

---

