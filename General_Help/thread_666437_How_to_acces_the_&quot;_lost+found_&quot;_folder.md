---
title: "How to acces the &quot; lost+found &quot; folder"
date: 2008-01-13
forum: General Help
---

### Post by abena on 2008-01-13
Hi people!

This is what I did: I touch the /etc/fstab file and I ruin it, so, I had to reinstall ubuntu in another partition, but, the partition where used to be my old and ruin ubuntu is now with just one folder " lost+found " it is about 2Gb, but I cannot access it, when I open it, it seems to be empty!

How can I open it, to recovery my data????

Thanks

---

### Post by erpo on 2008-01-13
For future reference, always back up a configuration file before you edit it.

```

cp /etc/fstab /etc/fstab.bak
vi /etc/fstab

```

If you find you can't read /mnt/oldfilesystem/lost+found, try:
```

sudo ls /mnt/oldfilesystem/lost+found

```

---

### Post by abena on 2008-01-13
I have a backup file of the fstab, but I cannot access my old file system, (lost+found) and the /mnt directory is empty...

---

