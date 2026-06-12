---
title: "default mount options of the file manager"
date: 2015-06-25
forum: General Help
---

### Post by mugen2 on 2015-06-25
Hi guys,

is there anyway to change the mount options for mounting a partition using the left panel of the file manger?

---

### Post by PaulW2U on 2015-06-25
As you're looking for help, moving to *General Help*.

---

### Post by haplorrhine on 2015-06-25
I don't think so, but I just noticed the **[FONT=courier new]--read-only[/FONT]** and **[FONT=courier new]--rw[/FONT]** flags listed on the **[FONT=courier new]mount[/FONT]** info page. huh...

---

### Post by cariboo on 2015-06-25
It would help if you let us know what it is you are trying to do. In most cases, it is easier to set the mount options from the command line. You need to edit /etc/fstab.

---

### Post by mugen2 on 2015-06-26
Well, I know how to do use command line or fstab.

But i want to change the way file manager does it, cause it's default options are wrong.

---

### Post by deadflowr on 2015-06-26
What's wrong about it?
Explain...

---

### Post by mugen2 on 2015-06-26
NTFS drive are mounted case sensitive and also without the option "windows_names"
This will case problems with windows accessing the partition later.

FAT32 partition is mounted correctly by default.

---

