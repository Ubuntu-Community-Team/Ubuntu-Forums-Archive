---
title: "Unable to save file in the read-only area"
date: 2012-10-26
forum: General Help
---

### Post by vkadal on 2012-10-26
I have installed gEDA, a software to develop electronic Schematics and PCBs. It has got installed in the default location. It has a library of symbols, which are used in preparation of schematics, and the library is located in read only file section under /usr or /etc. The libraries are editable and newer symbols can be added to the library. My problem is I am not able to save the newly created symbols in the read-only area. I am able to save in Desktop / Download. But gEDA will not display the library component if it is not saved in the particular directory, which is in read-only area. Is there any way to copy the file to that area?

---

### Post by netopalis45 on 2012-10-26
Post the output of ```
ls -l
``` on the directory containing the library.

---

### Post by 2F4U on 2012-10-27
The directories /usr and /etc are not read-only, but you cannot write in them as a normal user. Instead, you should create the file in a location you can write to and then use sudo to copy the file to /usr or /etc. Sudo will ask you to give your password.

---

### Post by vkadal on 2012-10-27
I have installed gEDA, a schematic and PCB editor for making design and fabrication of PCBs. It has a library of components stored in /usr/share/gEDA directory. I want to edit one of the library files, and save in the same folder. Since the folder is write protected, I am not able to save. Is there any work around for this problem. Iam able to save the edited file in some other location , for e.g  in Desktop.

---

### Post by zombifier25 on 2012-10-27
Every folders and files outside of your home is owned by root in order to prevent the users or malicious scripts from editing them. If you want to edit the files as root, run this command (beware: dangerous, use with care):
```
gksu nautilus
```
It will launch the file manager as root, and you will be able to modify any file.

---

### Post by coffeecat on 2012-10-27
Threads merged. Please do not create duplicates.

---

