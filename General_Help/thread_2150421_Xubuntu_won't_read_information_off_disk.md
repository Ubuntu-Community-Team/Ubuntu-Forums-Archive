---
title: "Xubuntu won't read information off disk"
date: 2013-06-01
forum: General Help
---

### Post by marinecomm on 2013-06-01
Installed Xubuntu on my fairly new computer. Sometimes when I try to update/install software it asks me for the install DVD. I put in the install DVD and it fails to load the necessary package(s) off the DVD. I can go into the file manager system and see all the files that are contained in the DVD. I tried mounting the DVD but that doesn't seem to help. I am new to *ubuntu so not sure how to troubleshoot this problem. Thank you in advance for any help offered. I am running Xubuntu 13.04 64 bit.

---

### Post by 2F4U on 2013-06-01
I have never seen an installed Ubuntu system asking for the install DVD when the system is installed to hdd. I would guess that something in your repository configuration points to the DVD and when you install software that is not in the current repositories, it asks for the DVD. Go through your repositories and see if there are entries for the install DVD.

---

### Post by marinecomm on 2013-06-01
Under Software Sources -> Other Software tab there are several entries for the cdrom

---

### Post by 2F4U on 2013-06-01
If they are ticked (i. e. enabled) then disable the entries. They are not needed since updates are handled online by connecting to the repositories.

---

### Post by marinecomm on 2013-06-01
Done. Other than that I have experienced no other issues with Xubuntu being able to read my disks.

---

