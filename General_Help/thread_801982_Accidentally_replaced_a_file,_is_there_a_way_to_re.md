---
title: "Accidentally replaced a file, is there a way to recover it?"
date: 2008-05-21
forum: General Help
---

### Post by werg on 2008-05-21
I've accidentally replaced a file I need with one with the same name (by choosing 'replace' when saving with an application). Is there a way to recover th replaced file?

Thanks

---

### Post by HumanAnarchist on 2008-05-21
Depends of the program you used. Maybe it created a backup file for you... check for hidden files, files that start with a .filename. 

```

ls -a

```

---

### Post by werg on 2008-05-21
I've checked, there isn't a backup file.

---

### Post by HumanAnarchist on 2008-05-21
not much you can do then, computers are kinda stupid, they do what you tell the to do...

---

### Post by werg on 2008-05-21
Are you sure there's absolutely nothing I can do?

---

### Post by todak on 2008-05-21
If you overwrote a file that YOU created, then there is nothing you can do to recover the original. :( When I am working on a picture file, for example,  I ALWAYS choose "save as..." or "save a copy.." options and give the file a different name. That way I retain the original file.

---

### Post by HumanAnarchist on 2008-05-21
It really depends of the program you use, but it is technicaly possible to retain some of the information from the disk if you're really lucky, but that involves heavy harddrive/filesystem digging. 

Dumping you whole partition to a file with "dd of=/dev/sdx[1234] if=some.file" and grepping for the the info you lost could work.

---

### Post by danwood76 on 2008-05-21
The best solution is to just not overwrite the file in the first place.
If a file is important save a backup at least, or save a backup when you start editing a file.

---

