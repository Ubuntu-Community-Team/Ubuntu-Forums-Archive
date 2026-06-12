---
title: "SSD Not working after Gparted"
date: 2016-05-09
forum: General Help
---

### Post by Vanilla Godzilla on 2016-05-09
I was using an Adata SSD without problems. I needed it for another project and I only had an OS installed on it so I used Gparted to delete the partition. Turned off computer and took the SSD out. Installed it in the other laptop and it did not recognize it anymore. Tried a windows machine and still nothing. Used a 2.5 SATA to USB 3.0 converter and I get a chime like something has been plugged in, but nothing show up?

---

### Post by grahammechanical on 2016-05-09
You deleted the partition. There is nothing to recognise. It does not have a file system (format). You should have deleted the data by re-formatting the partition. 

Regards

---

### Post by gedakc on 2016-05-09
You might consider creating a new partition and file system.  That way you can mount the file system and store data in it.

---

