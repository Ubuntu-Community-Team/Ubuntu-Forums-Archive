---
title: "Permission restrictions"
date: 2013-05-24
forum: General Help
---

### Post by phillyj on 2013-05-24
In my older Ubuntu (10.xx, I think), I can delete files and do things without getting permission errors. In my desktop with the latest 12.04, I can't delete things from desktop or write things to a new HDD (work in progress for the HDD). My question is, why am I not given full powers for working in the GUI? I know you need sudo for some things via cmd line. I feel very restricted. Honestly don't know if its the new distro or I set up something wrong in the installation of the OS?

---

### Post by Dennis N on 2013-05-24
You should have write permission (which allows you to delete files) for your home folder and sub-folders. Check that you do.

To see folder permissions of the Desktop folder:

In the terminal:

**ls -dl Desktop**

The output should begin with this:

drwxr-xr-x <owner> <group>

(this shows the owner has write (w) permission).

---

### Post by arubislander on 2013-05-24
From the sounds of it your user received a different uid from when you installed Ubuntu the first time. Usually this happens if you had more than one user in the previous install and you created the users in the reinstall in a different order. I'm assuming of course that you did a reinstall with preservation of your /home partition.

---

### Post by phillyj on 2013-05-24
> **arubislander said:**
> From the sounds of it your user received a different uid from when you installed Ubuntu the first time. Usually this happens if you had more than one user in the previous install and you created the users in the reinstall in a different order. I'm assuming of course that you did a reinstall with preservation of your /home partition.

Hmm, I installed Ubuntu to this new SSD. I didn't like the unity interface so I somehow got xubuntu (I think; not sure) to get me the classic desktop view. XFCE, maybe? I can't tell until I get home. Maybe that's where it got messed up?

---

### Post by arubislander on 2013-06-04
No way to know now... What errors are you getting exactly?

---

