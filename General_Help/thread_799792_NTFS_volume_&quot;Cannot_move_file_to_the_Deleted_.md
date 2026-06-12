---
title: "NTFS volume: &quot;Cannot move file to the Deleted Items&quot;"
date: 2008-05-19
forum: General Help
---

### Post by deltaromeo on 2008-05-19
Hi, does anyone know why I get the following error message when I try deleting files from an NTFS partition? 

---
Cannot move file to the Deleted Items folder, do you want to delete permanently?

The file "new file" cannot be moved to the wastebasket
---

Thanks.

---

### Post by ubuscout on 2008-05-19
...maybe could be some permission's problem ?!?

have u tried also with "sudo rm .... "

---

### Post by deltaromeo on 2008-05-19
Thanks ubuscout, that would work although it would delete the file completely.  I would like to be able to use the Deleted Items feature on the NTFS drives in case I need to recover the files.

---

### Post by ubuscout on 2008-05-19
ok....

...but if I rember well when u delete a file or some other content in a ntfs partition from ubuntu, at first it delete the item selected but if u look well in / of ntfs volume u'll find a ./Trash-<user> directory where u can find what u have deleted...

...until u give a "rm -rf ./Trash..." u'll find that content there...

---

### Post by drs305 on 2008-05-19
Hardy Heron wasn't really designed for a normal Trash folder on an NTFS drive. However, it appears if you mount the partition with a uid=1000 you can make it work. 

Here is the thread:
[http://ubuntuforums.org/showthread.php?t=771076](http://ubuntuforums.org/showthread.php?t=771076)

---

### Post by deltaromeo on 2008-05-19
Fantastic!  Thanks drs305 :)

---

### Post by noynac on 2008-05-19
---

---

