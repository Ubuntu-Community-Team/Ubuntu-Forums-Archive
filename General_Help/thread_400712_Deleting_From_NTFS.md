---
title: "Deleting From NTFS"
date: 2007-04-03
forum: General Help
---

### Post by GuitarRocker2562 on 2007-04-03
I have my NTFS windows drive mounted in ubuntu with write support. When I delete stuff from the drive it just moves it to a .Trash-ian folder on the partition. How do I actually delete them?

---

### Post by taurus on 2007-04-03
```
sudo rm /path_to_that_partition/.Trash/*
```

---

### Post by gilforsyth on 2007-04-03
Just delete the files again from within the .trash-*** folder, or delete the folder itself.  Kind of a pain to delete everything twice, there may be a way to streamline the process, but I don't know it.

---

### Post by GuitarRocker2562 on 2007-04-03
deleting it while in the trash is permanent, good!

I will just delete the trash when my HDD is getting full

---

