---
title: "Deleted items not in trash"
date: 2016-07-19
forum: General Help
---

### Post by 4kh3RAm on 2016-07-19
Deleted files no longer go to the trash. ?

---

### Post by DogMatix on 2016-07-19
Your deleted files should show in the directory:

 /home/your_username/.local/share/Trash/files

... unless you are logged in as root.

---

### Post by DragonBoy on 2016-07-19
If you use file window and move files to the trash. Then it will go to the following path:

/home/<user_name>/.local/share/Trash/files

There are two other directories that are created which are:

/home/<user_name>/.local/share/Trash/expunged
/home/<user_name>/.local/share/Trash/info


If you remove files from the terminal window with the "rm -rf <file_name>" then they are gone. Unless you have some time of snap shot backup of your system. Then you can retrieve it if you deleted by accident.

---

### Post by 4kh3RAm on 2016-07-19
After rebooting, deleted files were sent to Trash.

---

