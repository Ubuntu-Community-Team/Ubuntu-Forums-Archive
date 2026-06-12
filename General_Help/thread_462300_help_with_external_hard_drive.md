---
title: "help with external hard drive"
date: 2007-06-02
forum: General Help
---

### Post by eternaldeals on 2007-06-02
Need some help with my external usb hard drive! when I plug it in Ubuntu see it and lets me read the files on it and I can also move file from it to my computer. but it will not let me move file from my computer to it . It gives me this error
   ERROR While copying to “/media/disk”. 
you do not have permissions to write to this folder.
can anyone help me with this problem. 
It a Maxtor hard drive if it helps.

---

### Post by Rajiv_Nair on 2007-06-02
To edit/set permissions for the drive type in > sudo nautilus and in the file browser window that appears click on the "computer" button and right click on your External USB drive and check the permissions tab :)

---

### Post by milambyr on 2007-06-02
This worked for me, if your drive is not NTFS...

sudo chown -R username:username /media/disk

of course put in your username and the actual location of mounted HDD

---

