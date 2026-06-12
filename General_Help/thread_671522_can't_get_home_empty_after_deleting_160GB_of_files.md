---
title: "can't get /home empty after deleting 160GB of files and emptying the trash"
date: 2008-01-18
forum: General Help
---

### Post by daveoftheworld on 2008-01-18
Hello. I recently (2 days ago) installed ubuntu 7.10 and accidentally formatted a drive that had an os and files on it. I found testdisk and photorec and have recovered some files. Then I moved all those recovered files to an external  drive for storage. Then I typed into terminal, sudo nautilus and deleted all of the recovered files in /home and emptied the trash. Then I rebooted and ran gparted and it shows that my /home partition is a total of 335GB with 154GB used. I do not have 154GB on this computer as its a fresh install so what is going on. It is as if the deleted files are still on the hd somewhere. I've gone to the home folder and looked at properties of all folders in it and they all have very little in them so I'd like to find these 154 GB's and remove them from the system. I've checked all folders under filesystem and they might add up to about 4 GB. I hope someone can help solve this.   Thank you for reading.

---

### Post by philinux on 2008-01-18
If you used sudo nautilus and didnt actually delete then they will be in /.Trash thats roots trash directory.

---

### Post by vexorian on 2008-01-18
Did you set nautilus to show hidden files as well? there may be plenty of folders beginning with . in your /home

---

### Post by danwood76 on 2008-01-18
Yeah press ctrl+h and look in the root of your home folder and /root for .Trash-username folders which will contain the delelted files.

regards,
Danny

---

